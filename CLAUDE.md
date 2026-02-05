# Seattle Orcas Prototype - CCE Context

## Project Overview
Seattle Orcas Enterprise Intelligence Prototype - Demo for Jagan Nemani at AnalyticLabs.

**Live URL**: https://orcas.analyticlabs.io

## Deployment

**Platform**: Vercel (static HTML)
**Domain**: orcas.analyticlabs.io (custom domain via Vercel)

### Deployment Workflow
- Push to `master` triggers Vercel deployment via GitHub Actions
- Vercel config in `vercel.json` handles routing and headers

### Required Secrets (GitHub → Settings → Secrets)
- `VERCEL_TOKEN` - Vercel API token
- `VERCEL_ORG_ID` - Vercel organization ID
- `VERCEL_PROJECT_ID` - Vercel project ID

## Pages

| Route | File | Description |
|-------|------|-------------|
| `/` | federated_data.html | Federated data visualization (default) |
| `/federated-data` | federated_data.html | Same as above |
| `/fan-engagement` | fan_engagement_dashboard.html | Fan engagement dashboard |
| `/enterprise-intelligence` | enterprise_intelligence_demo.html | Enterprise intelligence demo |
| `/game-replay` | game_replay_animation.html | Game replay animation |

## Tech Stack
- Pure HTML/CSS/JavaScript (no build step)
- Static files served by Vercel
- Charts: Chart.js / D3.js

## Previous Deployment (Deprecated)
Was previously deployed to Azure Container Apps via Docker.
- Old workflow: `.github/workflows/deploy-azure.yml.disabled`
- Container: acrzeusmemorydev.azurecr.io/seattle-orcas

---

**CCE Version**: 1.0.0
**Last Updated**: 2026-02-05
