# =============================================================================
# BUS TICKET BOOKING SYSTEM — BACKEND — Environment Variables
# =============================================================================
#
# HOW TO USE THIS FILE:
# ---------------------
# 1. Copy this file to the backend repo root:
#      cp Bus-Ticket-Backend.env.example "gs studeis/bus-ticket-booking-system/.env.example"
#
# 2. In the repo root, duplicate it and remove the .example suffix:
#      cp .env.example .env
#
# 3. Edit .env and set real values (DO NOT commit .env to git).
#
# 4. Load the variables before running:
#
#    PowerShell:
#      Get-Content .env | ForEach-Object {
#        if ($_ -match '^([^#=]+)=(.*)$') {
#          [Environment]::SetEnvironmentVariable($matches[1], $matches[2], 'Process')
#        }
#      }
#      .\mvnw.cmd spring-boot:run
#
#    Git Bash / WSL:
#      export $(cat .env | xargs)
#      ./mvnw spring-boot:run
#
# 5. Add .env to .gitignore (NEVER commit real credentials!):
#      echo ".env" >> .gitignore
#
# =============================================================================


# -----------------------------------------------------------------------------
# DATABASE (MySQL)
# -----------------------------------------------------------------------------
# MySQL root password (or whatever user you configured in application.properties)
# Required — app won't connect without this
# In production: use a dedicated non-root user with limited privileges.
DB_PASSWORD=1234567890


# -----------------------------------------------------------------------------
# SPRING SECURITY — Admin Credentials (HTTP Basic + form login)
# -----------------------------------------------------------------------------
# Username for the in-memory admin user
# Defaults to "admin" if not set
# Used by both HTTP Basic (on /api/**) and form login (on view pages)
APP_ADMIN_USER=admin

# Password for the in-memory admin user
# REQUIRED — if blank, Spring generates a random password at startup (see logs)
# Frontend's BACKEND_PASSWORD env var MUST match this value
# In production: use a strong password from a secrets manager
APP_ADMIN_PASSWORD=admin1234


# -----------------------------------------------------------------------------
# CORS CONFIGURATION
# -----------------------------------------------------------------------------
# Comma-separated list of origins allowed to call /api/** endpoints
# Browsers enforce this on cross-origin requests
# Defaults to "http://localhost:8081" (our frontend origin)
# Production examples:
#   APP_CORS_ORIGINS=https://mybusapp.com
#   APP_CORS_ORIGINS=https://app.mycompany.com,https://admin.mycompany.com
APP_CORS_ORIGINS=http://localhost:8081


# -----------------------------------------------------------------------------
# OPTIONAL — JVM Tuning
# -----------------------------------------------------------------------------
# Uncomment to increase heap if you hit OutOfMemoryError:
# JAVA_OPTS=-Xmx1g -Xms512m


# -----------------------------------------------------------------------------
# OPTIONAL — Spring Profile
# -----------------------------------------------------------------------------
# Switch between application-{profile}.properties files
# Leave commented to use application.properties only
# SPRING_PROFILES_ACTIVE=dev


# =============================================================================
# VERIFICATION
# =============================================================================
# After setting env vars, verify with:
#
#   # Should return 401 (proves auth is enforced)
#   curl -i http://localhost:8080/api/trips
#
#   # Should return 200 with JSON (proves creds work)
#   curl -i -u admin:admin1234 http://localhost:8080/api/trips
#
# =============================================================================
