# Open WebUI Deployment for AI Workshop

This directory contains the OpenShift deployment files for Open WebUI with MAAS integration.

## Prerequisites

- OpenShift cluster access
- MAAS API endpoint with API key
- OpenShift storage classes available

## Quick Deploy

```bash
# 1. Create secrets from template
cp 00-secrets.yaml.template 00-secrets.yaml

# 2. Edit with your actual API key
# Update OPENAI_API_KEY with your MAAS token
# Generate WEBUI_SECRET_KEY with: openssl rand -base64 32

# 3. Apply in order
oc apply -f 00-secrets.yaml
oc apply -f 01-pvc.yaml
oc apply -f 02-deployment.yaml
oc apply -f 03-service.yaml
oc apply -f 04-route.yaml

# 4. Get the URL
oc get route openwebui -o jsonpath='{.spec.host}'
```

## Configuration

### Secrets (00-secrets.yaml)
- `OPENAI_API_KEY`: Your MAAS API token
- `WEBUI_SECRET_KEY`: Random 32+ character secret for session encryption

### Environment Variables (02-deployment.yaml)
- `OPENAI_API_BASE_URL`: MAAS endpoint URL
- `OPENAI_API_MODELS`: Comma-separated list of available models
- `AIOHTTP_CLIENT_TIMEOUT`: HTTP client timeout (seconds)
- `OPENAI_API_TIMEOUT`: OpenAI API timeout (seconds)
- `WEBUI_NAME`: Application title
- `ENABLE_SIGNUP`: Allow user registration
- `DEFAULT_USER_ROLE`: Role for new users (user/admin)

## First Time Setup

1. Navigate to the route URL
2. Create an admin account (first user is automatically admin)
3. Additional users can register or be created by admin

## Available Models

Update `OPENAI_API_MODELS` in the deployment to match what's available from your MAAS endpoint:

```bash
# Check available models
curl -s https://your-maas-endpoint/v1/models \
  -H "Authorization: Bearer YOUR_API_KEY" | jq -r '.data[].id'
```

## Troubleshooting

```bash
# Check pod logs
oc logs -l app=openwebui --tail=50

# Check if model endpoint is reachable
oc exec deployment/openwebui -- python3 -c "
import requests
r = requests.get('https://your-endpoint/v1/models', 
                 headers={'Authorization': 'Bearer YOUR_KEY'})
print(r.json())
"

# Restart deployment
oc rollout restart deployment/openwebui
```

## Cleanup

```bash
oc delete -f .
oc delete pvc openwebui-data-pvc
```
