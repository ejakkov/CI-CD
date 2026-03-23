# CI-CD University Project

This repository contains a university study project focused on building and automating a CI/CD pipeline for a Python app across multiple environments.

## What it does

- Installs Python dependencies for `python-greetings`
- Deploys the app with `pm2`
- Runs automated API tests from `course-js-api-framework`
- Promotes changes through: `dev -> staging -> preprod -> prod`

## Pipeline Implementations

- `Jenkinsfile` with staged deployment + testing flow
- GitHub Actions workflow in `.github/workflows/python-greetings.yml`
- Reusable composite actions in `.github/actions/`:
  - `install-pip-deps`
  - `deploy`
  - `test`

## Tech Stack

- Jenkins
- GitHub Actions (self-hosted runner)
- Python / pip
- Node.js / npm
- PM2

## Notes

This is an educational project for CI/CD practice and environment promotion strategy.
