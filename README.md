# 🚀 BobApp - Projet CI/CD avec Spring Boot & Angular

## 📋 Description

BobApp est une application web complète développée dans le cadre du projet OpenClassrooms "Gérez un projet collaboratif en intégrant une démarche CI/CD". L'application comprend :

- **Backend** : API REST Spring Boot (Java 17)
- **Frontend** : Application Angular avec TypeScript
- **Base de données** : MySQL
- **CI/CD** : GitHub Actions avec analyse SonarCloud et publication Docker

## 🏗️ Architecture

```
📦 BobApp
├── 📁 back/                 # Backend Spring Boot
│   ├── 📁 src/main/java/    # Code source Java
│   ├── 📁 src/test/java/    # Tests unitaires
│   ├── 📄 pom.xml           # Configuration Maven
│   ├── 📄 Dockerfile        # Image Docker backend
│   └── 📄 sonar-project.properties
├── 📁 front/                # Frontend Angular
│   ├── 📁 src/              # Code source TypeScript
│   ├── 📄 package.json      # Dépendances Node.js
│   ├── 📄 Dockerfile        # Image Docker frontend
│   └── 📄 sonar-project.properties
├── 📁 .github/workflows/    # Pipelines CI/CD
│   ├── 📄 backend-sonar.yml # Analyse SonarCloud Backend
│   ├── 📄 frontend-sonar.yml# Analyse SonarCloud Frontend
│   └── 📄 docker.yml        # Build & Publication Docker
└── 📄 README.md
```

## 🛠️ Technologies Utilisées

### Backend
- **Java 17**
- **Spring Boot 3.x**
- **Spring Data JPA**
- **MySQL**
- **Maven**
- **JUnit 5**
- **Jacoco** (couverture de code)

### Frontend
- **Angular 16+**
- **TypeScript**
- **HTML/CSS**
- **Karma/Jasmine** (tests)

### DevOps
- **Docker** & **Docker Hub**
- **GitHub Actions**
- **SonarCloud**
- **Maven**
- **npm**

## 🚀 Installation et Lancement

### Prérequis
- Java 17+
- Node.js 18+
- Docker
- MySQL (pour développement local)

### 🐳 Avec Docker (Recommandé)

```bash
# Cloner le repository
git clone https://github.com/VAcheronPradelAlyssa/Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance.git
cd Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance

# Lancer avec Docker Compose
docker-compose up -d

# Ou utiliser les images depuis Docker Hub
docker run -d -p 8080:8080 vacheronalyssa/bobapp-backend:latest
docker run -d -p 4200:80 vacheronalyssa/bobapp-frontend:latest
```

### 💻 Développement Local

#### Backend
```bash
cd back
mvn spring-boot:run
# Backend disponible sur http://localhost:8080
```

#### Frontend
```bash
cd front
npm install
npm start
# Frontend disponible sur http://localhost:4200
```

## 🔄 Pipeline CI/CD

### Workflows GitHub Actions

#### 1. **Analyse SonarCloud Backend** (`backend-sonar.yml`)
- **Déclenchement** : Push/PR sur `main`
- **Actions** :
  - Setup JDK 17
  - Cache Maven dependencies
  - Build & Tests avec Maven
  - Analyse qualité SonarCloud
  - Génération rapport couverture Jacoco

#### 2. **Analyse SonarCloud Frontend** (`frontend-sonar.yml`)
- **Déclenchement** : Push/PR sur `main`
- **Actions** :
  - Setup Node.js 18
  - Installation dépendances npm
  - Tests unitaires avec couverture
  - Analyse qualité SonarCloud

#### 3. **Build & Publication Docker** (`docker.yml`)
- **Déclenchement** : Push sur `main`/`develop`, PR sur `main`
- **Actions** :
  - Build images Docker locales
  - Tests fonctionnels des images
  - Publication sur Docker Hub (si `main`)
  - Tests des images publiées

### 📊 Qualité du Code - SonarCloud

| Composant | Quality Gate | Coverage | Bugs | Vulnerabilities |
|-----------|--------------|----------|------|-----------------|
| **Backend** | ![Quality Gate](https://sonarcloud.io/api/project_badges/measure?project=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_backend&metric=alert_status) | ![Coverage](https://sonarcloud.io/api/project_badges/measure?project=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_backend&metric=coverage) | ![Bugs](https://sonarcloud.io/api/project_badges/measure?project=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_backend&metric=bugs) | ![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_backend&metric=vulnerabilities) |
| **Frontend** | ![Quality Gate](https://sonarcloud.io/api/project_badges/measure?project=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_frontend&metric=alert_status) | ![Coverage](https://sonarcloud.io/api/project_badges/measure?project=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_frontend&metric=coverage) | ![Bugs](https://sonarcloud.io/api/project_badges/measure?project=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_frontend&metric=bugs) | ![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_frontend&metric=vulnerabilities) |

## 🐳 Images Docker

### Docker Hub
- **Backend** : `vacheronalyssa/bobapp-backend:latest`
- **Frontend** : `vacheronalyssa/bobapp-frontend:latest`

### Tags disponibles
- `latest` : Dernière version stable
- `{sha-commit}` : Version spécifique par commit
- `{date}` : Version par date de build

## 🧪 Tests

### Backend
```bash
cd back
mvn test                    # Tests unitaires
mvn verify                  # Tests + couverture Jacoco
mvn sonar:sonar            # Analyse SonarCloud locale
```

### Frontend
```bash
cd front
npm test                    # Tests unitaires
npm run test:ci            # Tests avec couverture
npm run e2e                # Tests end-to-end
```

## 📈 Métriques et Monitoring

- **SonarCloud** : Qualité du code, couverture, sécurité
- **GitHub Actions** : Statut des builds, déploiements
- **Docker Hub** : Statistiques de téléchargement des images

## 🔧 Configuration

### Variables d'environnement

#### Backend
```properties
# application.properties
spring.datasource.url=jdbc:mysql://localhost:3306/bobapp
spring.datasource.username=${DB_USERNAME:root}
spring.datasource.password=${DB_PASSWORD:password}
```

#### Secrets GitHub Actions
- `SONAR_TOKEN` : Token SonarCloud
- `DOCKERHUB_USERNAME` : Nom d'utilisateur Docker Hub
- `DOCKERHUB_TOKEN` : Token Docker Hub

## 🤝 Contribution

1. **Fork** le projet
2. **Créer** une branche feature (`git checkout -b feature/amazing-feature`)
3. **Commit** les changements (`git commit -m 'feat: add amazing feature'`)
4. **Push** vers la branche (`git push origin feature/amazing-feature`)
5. **Ouvrir** une Pull Request

### Conventions de commit
```
feat: nouvelle fonctionnalité
fix: correction de bug
docs: documentation
style: formatage
refactor: refactoring
test: ajout/modification tests
chore: tâches maintenance
```

## 📝 Licence

Ce projet est développé dans le cadre d'un projet éducatif OpenClassrooms.

## 👥 Auteur

**Vacheron Pradel Alyssa**
- GitHub: [@VAcheronPradelAlyssa](https://github.com/VAcheronPradelAlyssa)
- LinkedIn: [Alyssa Vacheron Pradel](https://linkedin.com/in/alyssa-vacheron-pradel)

## 🔗 Liens Utiles

- [SonarCloud Backend](https://sonarcloud.io/project/overview?id=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_backend)
- [SonarCloud Frontend](https://sonarcloud.io/project/overview?id=VAcheronPradelAlyssa_Gerez-un-projet-collaboratif-en-int-grant-une-d-marche-CI-CDsoutenance_frontend)
- [Docker Hub Backend](https://hub.docker.com/r/vacheronalyssa/bobapp-backend)
- [Docker Hub Frontend](https://hub.docker.com/r/vacheronalyssa/bobapp-frontend)