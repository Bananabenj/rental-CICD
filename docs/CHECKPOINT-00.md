# Checkpoint 00 — socle étudiant

## Intention pédagogique

Le dépôt doit être immédiatement exécutable tout en exposant clairement les
problèmes qui seront résolus pendant la formation. Les étudiants disposent de
deux technologies et de deux images, sans système distribué déjà achevé.

## Contenu

- un service Java/Spring Boot de location ;
- un service Python/FastAPI de tarification ;
- des tests unitaires et HTTP pour les deux services ;
- un endpoint `/health` par service ;
- un assemblage Docker Compose ;
- des workflows CI minimaux ;
- un script Python portable pour les commandes courantes.

## Critères d'acceptation

Sur une machine disposant des prérequis :

```bash
python scripts/course.py prerequisites
python scripts/course.py test
python scripts/course.py compose-up
python scripts/course.py smoke
python scripts/course.py compose-down
```

Toutes les commandes doivent réussir. Après `compose-up`, les réponses
suivantes sont attendues :

- `GET /health` retourne `{"status":"UP"}` pour les deux services ;
- `GET /cars` retourne les voitures initiales ;
- `POST /quotes` retourne un tarif en EUR.

## Hors périmètre intentionnel

- appel du service Python depuis Java ;
- tests de contrat entre services ;
- persistance et volumes ;
- Kind, E2E et smoke tests exécutés dans la CI ;
- durcissement complet des images et de la supply chain.

Ces absences ne sont pas des anomalies : elles matérialisent la progression des
TP suivants.
