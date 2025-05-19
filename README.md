# React Native Manual Build Workflow

## Overview

This GitHub Actions workflow automates the build and deployment process for iOS and Android mobile applications. It provides flexible options for manual triggering and can also be scheduled for daily builds.

## Key Strategy: Manual Profile Management

### Why Manual Profile Management?
- 🔧 Granular control over provisioning profiles
- 🛡️ Avoid common Fastlane provisioning complications
- 🔒 Secure, step-by-step certificate and profile handling

## Key Features

- Semantic versioning of the application
- Conditional builds for iOS and Android
- Manual or scheduled workflow execution
- Staged deployment to staging environment
- Automated release notes generation
- Slack notification after successful build

## Workflow Inputs

When manually triggering the workflow, you can configure:

- **Branch**: Target branch for the build (default: 'development')
- **iOS**: Include iOS build (default: true)
- **Android**: Include Android build (default: true)
- **Only Bump Build**: Increment build number without major changes
- **Force Build**: Proceed with build even without release notes

## Build Process

### Version Management
- Retrieves current version from `package.json`
- Applies semantic versioning strategy
- Updates version across the project
- Commits and pushes version changes to the specified branch

### iOS Build
- Sets up development environment
- Configures code signing and provisioning profiles
- Installs dependencies
- Builds and deploys to staging using Fastlane

### Android Build
- Sets up Java and Android build tools
- Configures signing and configuration files
- Installs dependencies
- Builds and deploys to staging using Fastlane

### Notifications
- Sends build status notification to Slack after completion

## Prerequisites

- GitHub Actions enabled
- Configured secrets and variables
- Ruby and Fastlane installed
- Appropriate Apple and Google developer accounts

## Security

The workflow uses base64 encoded secrets for:
- Certificates
- Provisioning profiles
- Keystore files
- Configuration files

## Notes

- Requires careful management of secrets
- Recommended to use in conjunction with proper CI/CD practices