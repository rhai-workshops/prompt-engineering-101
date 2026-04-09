# Prompt Engineering 101

Complete workshop package for teaching prompt engineering and AI skills to non-technical professionals.

**🎓 Workshop Slides:** [View Presentation](https://docs.google.com/presentation/d/15uhHMERyQhyd285_Lh7q-ZQJMiSOfZndS7reZMgumNg/edit?slide=id.g367e88771d4_0_5447#slide=id.g367e88771d4_0_5447)

> Originally developed for NC State Textiles workshop, now generalized for any industry.

---

## Overview

**Target Audience:** Marketing and sales professionals (adaptable to any industry)
**Duration:** 3 hours (2:00–5:00 PM)
**Platform:** Open WebUI on OpenShift
**Focus:** Hands-on prompt engineering with real use cases

### What's Included:
- OpenShift deployment files for Open WebUI
- Workshop participant guide with hands-on labs
- Sample data files (CSV, sales reports) for exercises
- Presentation slide outline
- Prompt engineering reference card

---

## Quick Start

### 1. Deploy Open WebUI

```bash
# Login to your OpenShift cluster
oc login --token=<your-token> --server=<your-server>

# Create secrets from template
cd openshift/openwebui
cp 00-secrets.yaml.template 00-secrets.yaml
# Edit 00-secrets.yaml with your MAAS API key

# Deploy
oc apply -f 00-secrets.yaml
oc apply -f 01-pvc.yaml
oc apply -f 02-deployment.yaml
oc apply -f 03-service.yaml
oc apply -f 04-route.yaml
```

See `openshift/openwebui/README.md` for detailed deployment instructions.

### 2. Prepare Workshop Materials

**Before the workshop:**
- Review `guides/WORKSHOP-GUIDE.md` (participant instructions)
- Create presentation slides from `SLIDES-OUTLINE.md`
- Print `guides/PROMPT-CHEAT-SHEET.md` as handouts
- Share sample data files from `sample-data/` directory

**Update API Configuration:**
```bash
# Edit secrets with your actual model API endpoint and key
oc edit secret openwebui-secrets -n <your-namespace>
```

### 3. Test the Platform

1. Access Open WebUI via the route URL
2. Create an admin account (first user becomes admin)
3. Upload a sample CSV from `sample-data/`
4. Try a few prompts from the workshop guide

---

## Workshop Use Cases

The labs cover real-world marketing and sales scenarios:

- **Product Image Analysis** - Identify visual patterns in successful products
- **Competitor Analysis** - Analyze competitor product positioning
- **Sentiment Analysis** - Extract insights from customer feedback
- **Sales Data Analysis** - Identify top performers and trends
- **Trend Forecasting** - Predict emerging fashion trends from images
- **Document RAG** - Extract insights from sales reports and documents

---

## Prerequisites

### Infrastructure:
- OpenShift cluster (4.12+)
- 1 vCPU, 2GB RAM for Open WebUI
- 5GB storage for Open WebUI data
- OpenAI-compatible model API endpoint (MAAS)

### For Participants:
- Web browser
- No coding experience required

---

## Deployment

### Quick Deploy

```bash
# 1. Create secrets from template
cd openshift/openwebui
cp 00-secrets.yaml.template 00-secrets.yaml
# Edit with your MAAS API key and generate WEBUI_SECRET_KEY

# 2. Deploy all resources
oc apply -f .

# 3. Get access URL
oc get route openwebui -o jsonpath='{.spec.host}'
```

### Detailed Instructions

See `openshift/openwebui/README.md` for complete deployment guide.

---

## Configuration

### Update Model API

Edit the secrets to configure your model endpoint:

```bash
oc edit secret openwebui-secrets
```

Update:
- `OPENAI_API_KEY` - Your MAAS API token
- `OPENAI_API_BASE_URL` - Your endpoint URL (in deployment.yaml)

### Available Models

Update the `OPENAI_API_MODELS` environment variable in `02-deployment.yaml` to match your MAAS endpoint:

```bash
# Check available models
curl -s https://your-maas-endpoint/v1/models \
  -H "Authorization: Bearer YOUR_API_KEY" | jq -r '.data[].id'
```

### Storage Classes

The deployment uses `ocs-storagecluster-ceph-rbd` (RWO) for persistent storage. Adjust in PVC files if your cluster uses different storage classes.

---

## Cleanup

Remove the deployment:

```bash
cd openshift/openwebui
oc delete -f .
oc delete pvc openwebui-data-pvc
```

---

## Customization

### For Other Industries

The workshop uses textiles/fashion examples, but techniques apply universally:
- Replace sample data with your industry data
- Update use case scenarios in `guides/WORKSHOP-GUIDE.md`
- Adjust product examples in slides

### Scaling for Larger Workshops

Note: Open WebUI uses ReadWriteOnce (RWO) storage, so replicas=1 only. For high availability:
- Use a load balancer in front of multiple instances
- Or increase resources for the single pod

```bash
# Increase storage if needed (edit before deployment)
# Edit 01-pvc.yaml to increase from 5Gi
```
