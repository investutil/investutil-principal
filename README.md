## Introduction
Welcome to the InvestUtil project repository. This repository contains information about my site, which I plan to partially open-source. The project aims to provide a comprehensive investment utility platform. For the initial setup and development, I plan to use this guide.

## Domain Name
investutil.com

## Tech Stack

### Frontend

- Framework: Next.js
- Hosting: Cloudflare Pages
  
### Backend
- Framework: Rust Axum
- Hosting: Oracle ARM Cloud
### Database
- Type: SQLite
- Service: Cloudflare D1
  
### Production Deployment
The deployment process for the InvestUtil project involves using Cloudflare Pages for the frontend, Oracle ARM Cloud for the backend, and Cloudflare D1 for the database. This section will be updated with detailed deployment instructions as the project progresses.

#### Diagram
Below is a diagram illustrating the architecture and tech stack of the InvestUtil project:

```mermaid
graph TD;
    A[Frontend: Next.js] -->|Hosted on| B[Cloudflare Pages]
    B -->|Interacts with| C[Backend: Rust Axum]
    C -->|Hosted on| D[Oracle ARM Cloud]
    C -->|Database Access| E[SQLite: Cloudflare D1]
```

### Development Environment Setup
WSL2 Ubuntu, Next.js + Rust Axum + SQLite

### DevOps Tools and Services

- **Version Control:** GitHub (private repo)
- **CI/CD Pipeline:** GitHub Actions
- **Code Quality:** SonarCloud
- **Testing:** 
  - Unit and Integration Tests: Jest for Next.js
  - End-to-End Tests: Cypress or Playwright
- **Deployment:**
  - **Nightly Builds:** Automated nightly builds using GitHub Actions
  - **Pre-production:** Similar setup as production, hosted on a staging server
  - **Production:** Cloudflare Pages (for frontend), Oracle ARM Cloud (for backend), Cloudflare D1 (for database)
