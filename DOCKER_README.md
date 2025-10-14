# Build and run with Docker

This workspace contains two services:

- `hospital-backend-main` — Spring Boot backend (jar) listening on port 8081
- `hospital-frontend-main` — Vite + React frontend (built static) served on port 5173

Quick commands (from repository root `d:/hospital`):

1) Build both images and start with docker-compose:

   docker-compose build
   docker-compose up -d

2) Build only backend image:

   docker build -t hospital-backend:local ./hospital-backend-main

3) Build only frontend image:

   docker build -t hospital-frontend:local ./hospital-frontend-main

Notes:
- The backend already contains a production-ready multi-stage Dockerfile that uses Maven and Eclipse Temurin 21 runtime.
- The frontend Dockerfile performs a build using Node 18 and serves the `dist` directory using `serve` on port 5173.
- If you want the frontend to proxy API calls to backend in production, configure your build or a reverse proxy accordingly.
