# Deployment and Operations

## Target topology

Internet/Zalo WebView → DNS and TLS reverse proxy → application server `192.168.40.94:3003` → backend services → PostgreSQL/Redis/object storage.

Administration domain: `https://hoithao-hiephoi.vkesys.com`.

Private IPs must not be published as client API URLs. The Mini App uses a valid HTTPS public API domain approved for its environment.

## Environment configuration

Provide `.env.example` without secrets. Required categories:

- application environment and public URLs;
- database and Redis;
- JWT/session keys;
- Zalo Mini App and OA settings;
- SMTP/email;
- object storage;
- upload and export limits;
- logging and monitoring;
- feature flags.

Validate required variables at process startup and fail fast with redacted errors.

## Containers and services

Recommended production services:

- `admin-web`
- `api`
- `worker`
- `postgres`
- `redis`
- reverse proxy
- optional S3-compatible object storage

Use health checks and restart policies. Do not store persistent uploads inside an ephemeral application container.

## Reverse proxy

- Force HTTPS.
- Set secure headers.
- Forward real client IPs only from trusted proxies.
- Configure request body limits appropriate to uploads.
- Apply timeouts separately for APIs and downloads.
- Serve hashed static assets with long cache lifetimes.

## Database operations

- Run migrations as an explicit release step.
- Back up before destructive migrations.
- Daily automated backups plus a documented retention policy.
- Periodically test restoration to a non-production environment.
- Never run uncontrolled schema synchronization in production.

## Logging and monitoring

Use structured logs with request ID, service, level and safe context. Redact tokens, passwords, registration answers and unnecessary personal data.

Monitor:

- API latency and error rate;
- database connections and slow queries;
- queue depth and failed jobs;
- storage utilization;
- authentication failures;
- export/notification failures;
- uptime and certificate expiry.

## Release process

1. Build immutable artifacts.
2. Run type checks, lint and tests.
3. Scan dependencies and container images.
4. Apply migration plan.
5. Deploy application and workers.
6. Verify readiness and smoke tests.
7. Roll back when health criteria fail.

## Security operations

- Rotate credentials and signing keys using documented procedures.
- Restrict administrative access by least privilege.
- Protect databases and Redis from direct public access.
- Maintain audit logs separately from ordinary application logs where possible.
- Document incident response, token revocation and temporary integration shutdown.
