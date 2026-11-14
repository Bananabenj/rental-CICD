# Notes utiles issues de la documentation historique

Cette note conserve uniquement les intentions pédagogiques encore pertinentes.
Les documents originaux complets restent consultables dans le tag
`legacy/v1-microservices`.

## Éléments réutilisables

- le domaine de location de voitures est assez simple pour laisser la priorité
  aux pratiques DevOps ;
- deux services permettent d'étudier les pipelines indépendants, le réseau et
  les contrats d'API ;
- Docker Compose fournit un premier environnement d'intégration local ;
- les exercices envisagés autour de PostgreSQL, des volumes, de la
  communication inter-services et du monitoring restent pertinents ;
- les tests existants constituent un point de départ pour expliquer la
  différence entre tests unitaires, tests de composants et tests système ;
- les déclenchements CI filtrés par chemin illustrent les compromis d'un
  monorepo.

## Éléments volontairement non conservés

- les multiples guides de démarrage qui répétaient les mêmes commandes ;
- les rapports de génération et de « complétion » du projet ;
- le tutoriel Spring Initializr, hors du futur objectif DevOps ;
- le tutoriel de publication manuelle sur Docker Hub, redondant avec GHCR ;
- les descriptions affirmant qu'une communication inter-services existait ;
- les annonces de Grype, de monitoring, de déploiement ou de tests E2E non
  présents dans l'implémentation ;
- l'affirmation selon laquelle les images étaient publiées depuis `develop` ;
- les index et représentations textuelles de l'arborescence, rapidement
  obsolètes.

## Idées à réintroduire dans le nouveau parcours

1. provoquer un échec de test et diagnostiquer la CI ;
2. construire et tracer les images par SHA Git ;
3. ajouter un service Python réellement appelé par le service Java ;
4. ajouter PostgreSQL, des migrations et des tests de volumes ;
5. déployer un environnement éphémère avec Kind ;
6. exécuter des smoke tests et un scénario E2E ;
7. collecter automatiquement les diagnostics en cas d'échec ;
8. promouvoir un même artefact sans le reconstruire.
