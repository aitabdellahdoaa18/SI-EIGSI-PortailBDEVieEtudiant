# SI-EIGSI – Portail BDE – Vie étudiant
Projet de système d'information (EIGSI) : un portail web pour le BDE et la vie étudiante, qui remplace le traitement manuel des événements, des inscriptions et des adhésions.

## 1. Présentation

Le portail permet :
- aux **étudiants** de consulter les événements, de s'inscrire et de demander une adhésion ;
- au **BDE** de créer des événements, de suivre les inscriptions et les présences, et de confirmer les adhésions ;
- à l'**administration** d'approuver ou de refuser les événements qui débutent à 18 h ou après (le BDE reçoit le motif en cas de refus).

Règles métier principales :
- contrôle des places et des doublons à l'inscription ;
- cotisation de 200 MAD par année ou 300 MAD par cycle Prépa/Ingénieur, payée hors portail puis confirmée manuellement par le BDE ;
- génération d'affiches assistée par l'IA (Gemini), à valider par le BDE avant publication.

## 2. Architecture technique

| Couche | Choix |
|---|---|
| Frontend | React / Vite |
| Backend | API Node.js (droits contrôlés par rôle côté serveur) |
| Base de données | SQLite (évolution possible : PostgreSQL) |
| Service IA | API `@google/genai` (Gemini), appelée côté serveur |
| Rôles | Étudiant, membre du BDE, administrateur |

## 3. Contenu du dépôt

```
├── Demo/                                    # Éléments de démonstration du MVP
├── Portail_BDE_VieEtudiante.zip             # Code source complet de l'application
├── README.md                                # Ce fichier
├── Rapport_Final_MVP_Portail-BDE.pdf        # Rapport final (séance 5)
├── S1_Rapport_Portail_BDE_Vie_Etudiant-.pdf # Rapport séance 1
└── S2_Rapport_Portail_BDE_Vie_Etudiante_.pdf# Rapport séance 2
```

Le code source est fourni dans l'archive `Portail_BDE_VieEtudiante.zip`. Il suffit de la décompresser pour obtenir le projet complet.

## 4. Prérequis

- Node.js et npm installés (sous Windows, utiliser `npm.cmd` si PowerShell bloque la commande `npm`).
- Pour la génération d'affiches uniquement : une clé API Gemini valide, un modèle d'image autorisé, un accès Internet et un quota suffisant.

## 5. Installation et lancement

1. Télécharger le dépôt, puis décompresser `Portail_BDE_VieEtudiante.zip`.
2. Ouvrir un terminal dans le dossier décompressé.
3. Installer les dépendances :
   ```bash
   npm install
   ```
4. Créer à la racine du projet un fichier `.env.local` contenant la clé API Gemini, lue par le serveur.
5. Démarrer l'application avec les scripts de lancement définis dans le fichier `package.json` du projet (serveur API et interface), puis ouvrir l'adresse locale affichée dans le terminal.

## 6. Déploiement

- **Version actuelle :** exécution locale avec un serveur unique ; les utilisateurs doivent accéder au même serveur.
- Les sauvegardes du fichier de base SQLite doivent être organisées.
- **Évolution :** migration vers PostgreSQL pour un hébergement évolutif ou un usage simultané plus important.

## 7. Limites connues

- Le paiement des cotisations n'est pas automatisé (confirmation manuelle par le BDE).
- L'envoi automatique des courriels n'est pas configuré.
- La génération d'affiches Gemini est intégrée côté serveur, mais une génération d'image réussie doit encore être vérifiée avec une clé valide.

## 8. Documentation

Les rapports du projet sont à la racine du dépôt : S1, S2 et le **rapport final** (démonstration et KPI, retour d'expérience, processus TO-BE augmenté par l'IA, consolidation des sources).
