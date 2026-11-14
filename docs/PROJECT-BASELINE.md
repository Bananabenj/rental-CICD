# État de référence avant refonte

## Objet

Ce document fixe le point de départ de la refonte pédagogique. L'état original
peut être retrouvé avec :

```bash
git switch --detach legacy/v1-microservices
```

Il ne faut pas développer depuis cet état détaché. Pour revenir au travail
courant :

```bash
git switch main
```

## Éléments réellement disponibles

- deux applications Spring Boot 3.4.0 avec Java 17 et Gradle ;
- six classes de test JUnit, dont des tests unitaires, des tests MVC et deux
  tests de chargement du contexte Spring ;
- deux Dockerfiles multi-stage ;
- un fichier `docker-compose.yml` ;
- deux workflows GitHub Actions, filtrés par service ;
- publication GHCR et scan Trivy uniquement pour les pushes sur `main`.

## Commandes du projet

| Besoin | Commande |
|---|---|
| Lancer le système | `docker compose up --build` |
| Voir son état | `docker compose ps` |
| Voir les journaux | `docker compose logs -f` |
| Arrêter le système | `docker compose down` |
| Tester le service Java principal | `cd car-rental-service && ./gradlew clean test` |
| Tester le service Hello | `cd hello-service && ./gradlew clean test` |
| Tester les endpoints sous Unix | `./start.sh test` |

Les équivalents Windows utilisent `gradlew.bat` au lieu de `gradlew`.

## Limites connues

- aucun fichier Quarto ;
- aucune persistance ni migration de schéma ;
- aucun volume applicatif ;
- aucune communication inter-services effective ;
- aucun test de contrat, test système, smoke test ou test E2E ;
- aucun manifeste Kubernetes ni déploiement Kind ;
- aucune analyse de couverture ou qualité statique ;
- aucun SBOM ni signature d'image ;
- duplication importante entre les deux workflows CI.

## Vérification locale effectuée

L'arborescence, les sources, les tests, les Dockerfiles et les workflows ont été
inspectés statiquement. Les tests Gradle n'ont pas pu être exécutés dans
l'environnement de maintenance initial, car aucun JDK n'y était installé et
`JAVA_HOME` n'était pas défini. Docker n'y était pas disponible non plus.

Ces validations doivent être rejouées sur une machine équipée de Java 17 et de
Docker avant de créer `checkpoint/00-starter`.

## Dépôts pédagogiques retenus

| Dépôt cible | Visibilité | Contenu |
|---|---|---|
| `rental-devops-course` | public | Présentations Quarto, énoncés et ressources |
| `rental-devops-starter` | template public | Point de départ distribué aux binômes |
| `rental-devops-reference` | privé | Solutions et historique des checkpoints |

Le découpage physique en trois dépôts interviendra après la construction et la
validation des checkpoints dans le dépôt de travail actuel.
