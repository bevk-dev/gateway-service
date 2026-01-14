# gateway-service

Kratek opis
- API gateway / reverse proxy za vse javne HTTP klice.
- Usmerja zahteve na `user-service`, `list-service` in `recipe-service` prek konfiguriranih rout.
- Poenoten vstopni endpoint za mobilno aplikacijo in druge odjemalce. Storitev privzeto posluša na portu `8080`.

Gradnja

```bash
# v mapi gateway-service
./mvnw clean package -DskipTests
docker build -t <your-registry>/gateway-service:latest .
```

Zagon
- Lokalno z Docker Compose: iz `shopsync-infra/docker-compose.yml` (izpostavljen kot `8080:8080`).
- Kubernetes manifests: `shopsync-infra/k8s/gateway-service`.

Env spremenljivke
- `USER_SERVICE_URL` — URL do `user-service` (npr. `http://user-service:8083`).
- `LIST_SERVICE_URL` — URL do `list-service` (npr. `http://list-service:8082`).
- `RECIPE_SERVICE_URL` — URL do `recipe-service` (npr. `http://recipe-service:8084`).

Konfiguracija
- `src/main/resources/application.yml`

Centralna dokumentacija sistema
- Za arhitekturo celotnega sistema in pregled vseh storitev glej `shopsync-infra/DOCUMENTATION.md`.

