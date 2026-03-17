# AI Workshop: Practical Prompt Engineering for Marketing & Sales

Complete workshop package for teaching prompt engineering and AI skills to non-technical professionals.

---

## Overview

**Target Audience:** Marketing and sales professionals (textiles industry)
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

## Repository Structure

```
.
├── README.md                      # This file
├── SLIDES-OUTLINE.md              # Presentation structure (44 slides)
│
├── guides/
│   ├── WORKSHOP-GUIDE.md          # Main participant guide (labs & exercises)
│   ├── QUICKSTART.md              # Fast deployment instructions
│   └── PROMPT-CHEAT-SHEET.md      # 1-page reference card
│
├── openshift/
│   ├── openwebui/                 # Open WebUI deployment (recommended)
│   │   ├── 00-secrets.yaml.template
│   │   ├── 01-pvc.yaml
│   │   ├── 02-deployment.yaml
│   │   ├── 03-service.yaml
│   │   ├── 04-route.yaml
│   │   └── README.md
│   │
│   └── (LibreChat files available as alternative)
│
└── sample-data/
    ├── customer-feedback.csv      # Customer reviews for sentiment analysis
    ├── sales-data.csv             # Sales performance data
    ├── quarterly-sales-report.md  # Sample report for RAG exercise
    └── README.md                  # Data file documentation
```

---

## Workshop Agenda

| Time | Activity |
|------|----------|
| 2:00–2:20 | Intro to AI & LLMs |
| 2:20–2:35 | What is Prompt Engineering? |
| 2:35–2:50 | Open WebUI Demo |
| 2:50–3:40 | Lab 1: Prompt Engineering Basics |
| 3:40–4:20 | Lab 2: Industry Use Cases |
| 4:20–4:40 | Lab 3: RAG & Document Upload |
| 4:40–4:55 | Advanced Techniques |
| 4:55–5:00 | Wrap-up |

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

## Open WebUI Features

Open WebUI provides a comprehensive workspace for AI interactions:

### Workspace Components

**Models**
- Select and configure available AI models
- Create custom model configurations based on existing models
- Adjust parameters like temperature, top-p, and system prompts
- Save custom model presets for different use cases
- Switch between models mid-conversation

**Knowledge**
- Upload and manage documents for RAG (Retrieval Augmented Generation)
- Build knowledge bases from PDFs, text files, and documents
- Query uploaded documents during conversations

**Prompts**
- Save and reuse effective prompts
- Create prompt templates with variables
- Share prompts across your organization

**Skills** (Functions)
- Extend AI capabilities with custom functions
- Integrate external APIs and tools
- Create reusable workflows

**Tools**
- Web search integration
- Code execution capabilities
- File analysis and processing

### Key Features for Workshops

- **Multi-user support** - Each participant gets their own account
- **Conversation history** - Save and review past interactions
- **File uploads** - Analyze CSV, PDF, images, and documents
- **Model switching** - Compare responses across different models
- **Prompt library** - Share best practices with participants

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

## Troubleshooting

### Pods not starting

```bash
# Check pod status
oc get pods -l app=openwebui

# View logs
oc logs -l app=openwebui --tail=50

# Check events
oc get events --sort-by='.lastTimestamp'
```

### Model not responding

```bash
# Check if MAAS endpoint is reachable from pod
oc exec deployment/openwebui -- python3 -c "
import requests
r = requests.get('https://your-endpoint/v1/models',
                 headers={'Authorization': 'Bearer YOUR_KEY'})
print(r.json())
"

# Check logs for errors
oc logs deployment/openwebui | grep -i error
```

### Can't access route

```bash
# Check route
oc get route openwebui

# Test health endpoint
oc exec deployment/openwebui -- curl -s http://localhost:8080/health
```

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

---

## Support

**Issues?**
- Check `openshift/openwebui/README.md` for troubleshooting
- Review OpenShift logs: `oc logs -l app=openwebui`
- Verify MAAS API configuration in secrets and deployment

---

## License

[Add your license here]

---

## Ready to Get Started?

1. Deploy Open WebUI: See `openshift/openwebui/README.md`
2. Review participant guide: `guides/WORKSHOP-GUIDE.md`
3. Create your presentation from: `SLIDES-OUTLINE.md`
4. Test with sample data from: `sample-data/`
