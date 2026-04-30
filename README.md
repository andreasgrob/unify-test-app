# Unify Test App

A full-stack task management application demonstrating CloudBees Unify workflows and feature flags.

## Architecture

- **Frontend**: React + Vite (Node.js)
- **Backend**: Go REST API
- **Feature Flags**: CloudBees Feature Management
- **CI/CD**: CloudBees Workflows

## Repositories

- [Frontend](https://github.com/andreasgrob/unify-test-app-frontend) - React application
- [Backend](https://github.com/andreasgrob/unify-test-app-backend) - Go API service

## Deployment Workflows

This repository contains application-level workflows that coordinate deployments across both services:

### deploy-dev.yaml
- Deploys both frontend and backend to development environment
- Auto-triggered on component repository changes
- Runs integration tests

### deploy-staging.yaml
- Deploys to staging environment
- Includes E2E testing and performance validation
- Requires manual approval

### deploy-production.yaml
- Production deployment with multiple strategies:
  - Backend: Blue-Green deployment
  - Frontend: Canary deployment (10% → 25% → 50% → 100%)
- Multi-region deployment
- Comprehensive monitoring and verification
- Requires manual approval

### rollback.yaml
- Emergency rollback procedure
- Quick restoration to previous stable version
- Incident response workflow

## Environments

| Environment | Frontend | Backend |
|-------------|----------|---------|
| Development | https://dev.unify-test-app.example.com | https://dev-api.unify-test-app.example.com |
| Staging | https://staging.unify-test-app.example.com | https://staging-api.unify-test-app.example.com |
| Production | https://unify-test-app.example.com | https://api.unify-test-app.example.com |

## Feature Flags

The application uses 50+ feature flags for controlled rollouts:
- UI features (dark mode, new dashboard, etc.)
- Backend features (caching, rate limiting, etc.)
- Configuration values (timeouts, limits, URLs)

## Running Locally

See individual component repositories for local development instructions.
