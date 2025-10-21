# Valor-Nation-United
Valor Nation Generator 
services:
  - type: web
    name: valor-backend
    env: docker
    rootDir: backend
    plan: free
    autoDeploy: true
    healthCheckPath: /health
    envVars:
      - key: STABILITY_API_KEY
        sync: false
      - key: R2_ACCOUNT_ID
        sync: false
      - key: R2_ACCESS_KEY_ID
        sync: false
      - key: R2_SECRET_ACCESS_KEY
        sync: false
      - key: R2_BUCKET
        sync: false
      - key: R2_PUBLIC_BASE
        sync: false
      - key: R2_SIGNED_URLS
        sync: false
      - key: R2_SIGNED_TTL_SECONDS
        sync: false
      - key: MEDIA_SIGN_SHARED_SECRET
        sync: false

  - type: web
    name: valor-frontend
    env: docker
    rootDir: frontend
    plan: free
    autoDeploy: true
    envVars:
      - key: BACKEND_URL            # Render injects the live backend URL here
        fromService:
          name: valor-backend
          type: web
          property: url

