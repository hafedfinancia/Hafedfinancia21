HAFEDFINANCIA – Code source complet et robuste (Document explicatif)
🏦 Objectif du logiciel
HAFEDFINANCIA est une application financière complète permettant de :
•	Gérer des comptes utilisateurs et rôles (RBAC)
•	Effectuer des transactions sécurisées
•	Produire des statistiques et rapports
•	Supporter plusieurs langues
•	S'intégrer facilement dans un SI moderne via une API REST sécurisée
 
🛠 Architecture technique (proposée et robuste)
HAFEDFINANCIA/
├── api/              # API REST (Gin)
│   └── routes/       # Routage, middlewares
├── configs/          # Configurations multi-environnements (dev, prod)
├── internal/
│   ├── auth/         # Authentification, JWT, RBAC
│   ├── db/           # Modèles et accès base de données (GORM)
│   ├── transaction/  # Logique métier transactions
│   ├── stats/        # Statistiques et reporting
│   └── i18n/         # Internationalisation
├── scripts/          # Scripts CI/CD, migration, etc.
├── Dockerfile        # Build multi-stage optimisé
├── go.mod / go.sum   # Dépendances Go
└── main.go           # Point d’entrée
 
🔒 Sécurité et authentification (internal/auth)
•	JWT avec refresh token sécurisé (expiration courte pour access token)
•	RBAC : rôles et permissions fines
•	Rate limiting sur /login
•	Stockage sécurisé des secrets avec variables d’env.
•	Revocation et détection des tokens volés
Clé technique : Middleware Gin CheckPermission("transaction:create").
 
🗄 Base de données et transactions (internal/db, internal/transaction)
•	Pool de connexions GORM optimisé
•	Transactions atomiques db.Transaction()
•	Audit trail (audit_logs)
•	Précision financière via decimal.Decimal ou int64
•	Prévention injections SQL même pour requêtes brutes
 
📈 Statistiques et reporting (internal/stats)
•	Agrégations SQL via GORM
•	Export CSV / Excel / PDF (Go libraries)
•	Visualisation via API et front-end externe
 
🌍 Internationalisation (internal/i18n)
•	Chargement dynamique de fichiers JSON (fr.json, en.json)
•	Middleware détection langue (Accept-Language)
•	Stockage de la langue préférée utilisateur
 
⚙ API REST (api/routes)
•	Versioning /api/v1/...
•	Validation stricte des requêtes
•	Gestion centralisée des erreurs → JSON structuré
•	Logging structuré avec logrus ou zap
 
🐳 Déploiement & Observabilité
•	Dockerfile multi-stage

