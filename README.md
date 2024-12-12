# GO_POC - Microservices Demo

Dette repository indeholder en Proof of Concept (POC) for en microservice-arkitektur. Projektet demonstrerer brugen af flere microservices, en NGINX-load balancer og integration med eksterne services som RabbitMQ og Vault.

## **Indhold**

- [Introduktion](#introduktion)
- [Arkitektur](#arkitektur)
- [Komponenter](#komponenter)
- [Installation](#installation)
- [Sådan bruges projektet](#sådan-bruges-projektet)
- [Testing](#testing)
- [Teknologier](#teknologier)
- [Forfattere](#forfattere)

---

## **Introduktion**

Dette projekt implementerer en POC for en digital auktionsplatform, som består af følgende microservices:

- **User Service**: Håndtering af brugerdata.
- **Auth Service**: Godkendelse og token-håndtering (JWT).
- **Catalog Service**: Håndtering af kataloger med auktionsgenstande.
- **Auction Service**: Håndtering af auktioner og deres data.
- **Bidding Service**: Håndtering af budgivning på auktioner.

---

## **Arkitektur**

![Arkitekturdiagram](link_til_dit_diagram.png)

Systemet bruger en NGINX-load balancer som reverse proxy til at dirigere API-kald til de relevante microservices.

---

## **Komponenter**

- **NGINX**: Load balancer og reverse proxy.
- **RabbitMQ**: Messaging mellem microservices.
- **Vault**: Håndtering af secrets og miljøvariabler.
- **MongoDB**: Database til opbevaring af data for microservices.

---

## **Installation**

### **Forudsætninger**
- Docker og Docker Compose installeret.

### **Start projektet**
1. Klon dette repository:
   ```bash
   git clone https://github.com/dit-brugernavn/GO_POC.git
   cd GO_POC
   ```

2. Start services:
   ```bash
   docker-compose up -d
   ```

3. Tjek status for services:
   ```bash
   docker ps
   ```

---

## **Sådan bruges projektet**

Microservices er tilgængelige gennem NGINX ved følgende endpoints:

- **User Service**: `http://localhost:4000/api/user`
- **Auth Service**: `http://localhost:4000/api/auth`
- **Catalog Service**: `http://localhost:4000/api/catalog`
- **Auction Service**: `http://localhost:4000/api/auction`
- **Bidding Service**: `http://localhost:4000/api/bidding`

### Eksempel
For at teste User Service:
```bash
curl http://localhost:4000/api/user
```

---

## **Testing**

Du kan teste endpoints via:
- **Postman**: Importér din Postman-kollektion og send requests.
- **curl**: Brug kommandolinjen til at sende HTTP-requests.

---

## **Teknologier**

Projektet bruger følgende teknologier:
- **Docker & Docker Compose**: Containerization.
- **NGINX**: Load balancer og reverse proxy.
- **MongoDB**: Database.
- **RabbitMQ**: Messaging.
- **Vault**: Håndtering af secrets.
- **C# .NET**: Udvikling af microservices.

---

## **Forfattere**

- [Dit Navn](link_til_din_github_profil)
- Andre relevante personer eller grupper.
