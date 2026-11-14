# Rental Microservices — état initial

Ce dépôt contient le socle historique d'une future formation DevOps d'environ
30 heures. Il est actuellement en phase de restructuration.

L'état antérieur complet, documentation comprise, est conservé par le tag Git
`legacy/v1-microservices`. La documentation présente dans la branche courante
décrit uniquement ce qui existe réellement.

## Services

| Service | Technologie | Port | Rôle actuel |
|---|---|---:|---|
| `car-rental-service` | Java 17, Spring Boot, Gradle | 8080 | API de location avec stockage en mémoire |
| `hello-service` | Java 17, Spring Boot, Gradle | 8081 | API minimale retournant `Hello` |

Les deux services possèdent un Dockerfile multi-stage et sont assemblés par
Docker Compose. Ils partagent un réseau Docker, mais ne communiquent pas encore
entre eux.

## Démarrage avec Docker Compose

Prérequis : Docker avec la commande `docker compose`.

```bash
docker compose up --build
```

Dans un autre terminal :

```bash
curl http://localhost:8080/cars
curl http://localhost:8081/hello
```

Pour arrêter les services :

```bash
docker compose down
```

## Tests locaux

Prérequis : JDK 17.

Sous Linux ou macOS :

```bash
cd car-rental-service && ./gradlew clean test
cd ../hello-service && ./gradlew clean test
```

Sous Windows PowerShell :

```powershell
Set-Location car-rental-service
.\gradlew.bat clean test
Set-Location ..\hello-service
.\gradlew.bat clean test
```

## Intégration continue actuelle

Deux workflows GitHub Actions exécutent séparément les opérations suivantes :

1. tests Gradle ;
2. compilation ;
3. recherche de secrets avec Gitleaks ;
4. construction des images Docker ;
5. publication dans GHCR uniquement après un push sur `main` ;
6. scan Trivy des images publiées.

Il n'existe pas encore de déploiement, de cluster Kind, de tests E2E, de base
de données, de volumes applicatifs ni de communication inter-services.

## Documentation maintenue

- [État de référence et commandes](docs/PROJECT-BASELINE.md)
- [Notes pédagogiques extraites de l'ancienne documentation](archive/legacy-docs/README.md)
- [Car Rental Service](car-rental-service/README.md)
- [Hello Service](hello-service/README.md)

La prochaine étape prévue consiste à produire le checkpoint étudiant initial,
avec un service Python de tarification à la place de `hello-service`.
