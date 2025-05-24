This is not a dev repo, it is a summary repo.
But it is recommended to put clone investutil-front and investutil-back projects into this project.

See the code in [Front-end](https://github.com/investutil/investutil-front-public), [Back-end](https://github.com/investutil/investutil-back-public) [Infrastructure]([https://github.com/investutil/investutil-back-public](https://github.com/investutil/investutil-infra) repos

## Introduction
Welcome to the InvestUtil project repository. This repository contains information about my site, which I plan to partially open-source. The project aims to provide a comprehensive investment utility platform. For the initial setup and development, I plan to use this guide.

## Project Structure

```
investutil-principal/
├── investutil-front/     # Frontend application (React)
├── investutil-back/      # Backend application (Rust)
└── investutil-infra/     # Infrastructure and deployment configurations
    ├── docker/          # Docker configurations
    │   └── backend/     # Backend Docker files
    └── k8s/            # Kubernetes configurations
        └── backend/    # Backend K8s manifests
```

## Children Repositories

### Public Repositories
#### Front-end
https://github.com/investutil/investutil-front-public
#### Back-end
https://github.com/investutil/investutil-back-public
#### Infrastructure
https://github.com/investutil/investutil-infra

## Domain Name
### Site
www.investutil.com
### Documentation
doc.investutil.com
### Blog
blog.investutil.com
### Tech Wiki
https://github.com/investutil/investutil-principal/wiki

## Tech Stack

### Frontend
- Library: React
- Hosting: Cloudflare Pages
- Anti-Scraping Bot: Fight Mode
  
### Backend
- Framework: Rust Axum
- Hosting: Oracle ARM Cloud

### Database
- Type: PostgreSQL with Supabase
- Rust connection: sqlx

### Infrastructure
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **Registry**: GitHub Container Registry
- **CI/CD**: GitHub Actions

### Documentation
- mdBook

### Blog
- Hugo

### Production Deployment

The deployment process for the InvestUtil project involves multiple components:

#### Frontend Deployment
- Hosted on Cloudflare Pages
- Automated deployment through GitHub Actions

#### Backend Deployment
Two deployment options are available:

1. **Docker Compose (Development)**
   - Simple deployment using Docker Compose
   - Includes PostgreSQL database
   - See `investutil-infra/docker/backend/` for configuration

2. **Kubernetes (Production)**
   - Full Kubernetes deployment
   - Includes:
     - Backend service deployment
     - PostgreSQL StatefulSet
     - ConfigMaps and Secrets management
   - See `investutil-infra/k8s/backend/` for configuration

#### Database
- PostgreSQL with Supabase for production
- Local PostgreSQL for development

#### Architecture Diagram
Below is a diagram illustrating the architecture and tech stack of the InvestUtil project:

```mermaid
graph TD;
    A[Frontend: React] -->|Hosted on| B[Cloudflare Pages]
    B -->|Interacts with| C[Backend: Rust Axum]
    C -->|Hosted on| D[Oracle ARM Cloud]
    C -->|Database Access| E[sqlx]
    C -->|Containerized with| F[Docker]
    F -->|Orchestrated by| G[Kubernetes]
```

### Development Environment Setup
WSL2 Ubuntu, React + Rust Axum + Local PostgreSQL 

### DevOps Tools and Services
- **Version Control:** GitHub (private repo)
- **CI/CD Pipeline:** GitHub Actions
- **Code Quality:** SonarCloud
- **Code Formatting:**
  - React: Prettier
  - Rust: rustfmt
- **Testing:** 
  - Unit and Integration Tests:
    - Jest for React
    - Rust (Axum): Built-in Rust test framework and additional libraries
  - End-to-End Tests: Cypress or Playwright
  - Database Tests: sqlx
- **Deployment:**
  - **Nightly Builds:** Automated nightly builds using GitHub Actions
  - **Pre-production:** Similar setup as production, hosted on a staging server
  - **Production:** Cloudflare Pages (frontend), Oracle ARM Cloud (backend), PostgreSQL with Supabase (database)

## Local Development Setup

### Backend Setup

1. Navigate to the backend directory:
```bash
cd investutil-back
```

2. Copy the environment variables template:
```bash
cp .env.example .env
```

3. Configure your `.env` file:
```env
# Server Configuration
HOST=0.0.0.0
PORT=8080

# Database Configuration
DATABASE_URL=postgresql://username:password@localhost:5432/database_name

# JWT Configuration
JWT_SECRET=your_secure_jwt_secret

# Other Configuration
RUST_LOG=debug
```

**Important Security Notes:**
- Never commit the `.env` file to version control
- Use strong passwords and secure JWT secrets
- Implement stricter security settings in production

### Frontend Setup

1. Navigate to the frontend directory:
```bash
cd investutil-front
```

2. Copy the environment variables template:
```bash
cp .env.example .env
```

3. Configure your `.env` file:
```env
VITE_API_URL=http://localhost:8080
```

## Development

1. Start the backend server:
```bash
cd investutil-back
cargo run
```

2. Start the frontend development server:
```bash
cd investutil-front
npm run dev
```

## Deployment

For detailed deployment instructions, please refer to:
- Frontend deployment: See frontend repository README
- Backend deployment: See backend repository README
- Infrastructure setup: See [investutil-infra](https://github.com/investutil/investutil-infra) repository

## Security Considerations

- Environment files (.env) contain sensitive information and should never be committed to Git
- Use .env.example as a template, but never include actual sensitive data
- Implement more secure configurations in production
- Regularly update dependencies to patch security vulnerabilities
- For production deployments:
  - Use secure secrets management in Kubernetes
  - Enable HTTPS/TLS for all services
  - Implement proper network policies
  - Follow the principle of least privilege
