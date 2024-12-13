# GO_POC: Microservices Setup med NGINX Load Balancer

Dette repository indeholder implementeringen af et microservices-baseret system til GO_POC-projektet. Systemet består af flere services som authentication, user management, catalog, auction og bidding. **NGINX** er konfigureret som en load balancer til at dirigere trafik til de korrekte microservices.

## Funktioner

- **Microservices**:
  - `authservice`: Håndterer autentificering.
  - `userservice`: Administrerer brugerdata.
  - `catalogservice`: Administrerer produktkataloget.
  - `auctionservice`: Håndterer auktioner.
  - `biddingservice`: Håndterer bud på auktioner.
- **NGINX Load Balancer**: Dirigerer HTTP-forespørgsler baseret på URL-stier til de korrekte backend-services.
- **Docker Compose**: Brugt til at starte alle services og NGINX som en samlet løsning.

---

## Filstruktur

- **`nginx/nginx.conf`**:
  Indeholder NGINX-konfigurationen til at rute forespørgsler til de relevante backend-services.

- **`docker-compose.yml`**:
  Definerer alle microservices, NGINX, samt netværkskonfiguration.

---

## Hvordan det virker

### NGINX Konfiguration
NGINX fungerer som en load balancer og lytter på port `4000`. Den ruter forespørgsler til de relevante backend-services baseret på URL-stien:
- `/api/auth/` → `authservice`
- `/api/user/` → `userservice`
- `/api/catalog/` → `catalogservice`
- `/api/auction/` → `auctionservice`
- `/api/bidding/` → `biddingservice`

Eksempel fra `nginx.conf`:
```nginx
location /api/auth/ {
    proxy_pass http://auth_backend;
}
```

### Docker Compose
`docker-compose.yml` filen bruges til:
- At starte alle microservices og NGINX.
- Sikre, at NGINX venter på, at alle services er klar.
- Forbinde alle services til samme Docker-netværk (`go_infrastructure_auctionnetwork`).

---

## Opsætningsvejledning

1. **Klon repository**:
   ```bash
   git clone https://github.com/dit-repo/go_poc.git
   cd go_poc
   ```

2. **Start alle services med Docker Compose**:
   ```bash
   docker-compose up -d
   ```

3. **Verificer kørende containere**:
   ```bash
   docker ps
   ```
   Sørg for, at alle services, inkl. NGINX, kører.

---

## Test af services

### Eksempel: Test `authservice`
For at teste `authservice` login-endpointet, kan du bruge denne `curl`-kommando:
```bash
curl http://localhost:4000/api/auth/loginuser \
   -H "Content-Type: application/json" \
   -d '{"username": "testadmin", "password": "admin123"}'
```

Forventet svar:
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5..."
}
```

### Test af andre services
Du kan teste de andre endpoints som følger:
- **User Service**:
  ```bash
  curl http://localhost:4000/api/user/
  ```
- **Catalog Service**:
  ```bash
  curl http://localhost:4000/api/catalog/
  ```
- **Auction Service**:
  ```bash
  curl http://localhost:4000/api/auction/
  ```
- **Bidding Service**:
  ```bash
  curl http://localhost:4000/api/bidding/
  ```

---

## Fejlfinding

- **NGINX-konfiguration**: Sørg for, at `nginx/nginx.conf` er korrekt monteret i containeren.
- **Docker-netværk**: Sørg for, at netværket `go_infrastructure_auctionnetwork` eksisterer, og alle services er forbundet til det.
  ```bash
  docker network ls
  ```
- **Logs**: Tjek logs for fejl:
  ```bash
  docker logs <container_name>
  ```

---

## Mulige forbedringer
- Tilføj health checks til services.
- Implementer HTTPS i NGINX.
---

## Bidragydere
- **Dit navn**
- **Dit team**

---