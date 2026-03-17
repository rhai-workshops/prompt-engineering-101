# Quick Start Guide - Open WebUI on OpenShift

Get Open WebUI running in under 10 minutes.

## Prerequisites

```bash
# Verify you have oc CLI
oc version

# Login to OpenShift
oc login https://api.your-cluster.com:6443
```

## Deploy in 4 Steps

### 1. Create Secrets

```bash
# Navigate to Open WebUI deployment directory
cd openshift/openwebui

# Create secrets file from template
cp 00-secrets.yaml.template 00-secrets.yaml

# Generate secure keys
openssl rand -base64 32
# Copy output and use as WEBUI_SECRET_KEY
```

Edit `00-secrets.yaml` and update:
- `OPENAI_API_KEY`: Your MAAS API token
- `WEBUI_SECRET_KEY`: Paste generated value from above

### 2. Configure Model Endpoint

Edit `02-deployment.yaml`:

Update the `OPENAI_API_BASE_URL` value:
```yaml
- name: OPENAI_API_BASE_URL
  value: "https://your-maas-endpoint/v1"
```

Update the model name to match your MAAS endpoint:
```yaml
- name: OPENAI_API_MODELS
  value: "Granite-3.3-8B-Instruct"
```

To check available models:
```bash
curl -s https://your-maas-endpoint/v1/models \
  -H "Authorization: Bearer YOUR_API_KEY" | jq -r '.data[].id'
```

### 3. Deploy All Resources

```bash
# Apply all YAML files in order
oc apply -f 00-secrets.yaml
oc apply -f 01-pvc.yaml
oc apply -f 02-deployment.yaml
oc apply -f 03-service.yaml
oc apply -f 04-route.yaml

# Wait for deployment to complete
oc rollout status deployment/openwebui
```

### 4. Access Open WebUI

```bash
# Get the route URL
oc get route openwebui -o jsonpath='{.spec.host}'

# Or get full URL
echo "https://$(oc get route openwebui -o jsonpath='{.spec.host}')"
```

Open the URL in your browser and create your admin account (first user becomes admin).

## Verify Deployment

```bash
# Check pod status
oc get pods -l app=openwebui

# Should see:
# openwebui-xxxxx   1/1   Running

# Check logs
oc logs -l app=openwebui --tail=50

# Test health endpoint
oc exec deployment/openwebui -- curl -s http://localhost:8080/health
# Should return: {"status":true}
```

## Quick Configuration

### Add More Models

If you have access to multiple models through your MAAS endpoint:

```bash
oc set env deployment/openwebui \
  OPENAI_API_MODELS="Granite-3.3-8B-Instruct,Mistral-7B-Instruct"
```

### Increase Timeout (for slower models)

```bash
oc set env deployment/openwebui \
  AIOHTTP_CLIENT_TIMEOUT=300 \
  OPENAI_API_TIMEOUT=300
```

### Disable User Registration (after admin setup)

```bash
oc set env deployment/openwebui ENABLE_SIGNUP=false
```

## Troubleshooting

### Pod not starting

```bash
# Check events
oc describe pod -l app=openwebui

# Common issues:
# - PVC not bound (check storage class)
# - Image pull errors (check network/registry)
# - Missing secrets (verify 00-secrets.yaml applied)
```

### Model not responding

```bash
# Test MAAS endpoint from pod
oc exec deployment/openwebui -- python3 -c "
import requests
r = requests.get('https://your-endpoint/v1/models',
                 headers={'Authorization': 'Bearer YOUR_KEY'},
                 timeout=10)
print(r.status_code)
print(r.json())
"

# Check logs for connection errors
oc logs deployment/openwebui | grep -i "error\|timeout"
```

### Can't access route

```bash
# Verify route exists
oc get route openwebui

# Check route configuration
oc describe route openwebui

# Test from within cluster
oc run test --image=curlimages/curl --rm -i --restart=Never \
  -- curl -s http://openwebui:8080/health
```

## Cleanup

```bash
# Remove all resources
cd openshift/openwebui
oc delete -f .

# Remove PVC (data will be lost)
oc delete pvc openwebui-data-pvc
```

## Next Steps

1. Create your admin account at the Open WebUI URL
2. Review the workspace features (Models, Knowledge, Prompts)
3. Test with a simple prompt
4. Upload a sample file from `sample-data/`
5. Review `WORKSHOP-GUIDE.md` for lab exercises

## Advanced Configuration

For detailed configuration options, see:
- `openshift/openwebui/README.md` - Full deployment guide
- `openshift/openwebui/02-deployment.yaml` - All environment variables
- Open WebUI documentation: https://docs.openwebui.com
