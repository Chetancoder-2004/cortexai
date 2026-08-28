# CortexAI

CortexAI is a comprehensive full-stack application featuring a React-based frontend and a robust Node.js microservices backend. The platform provides authentication, real-time chat, AI agent integration, and billing services.

## Architecture Overview

The system is built with a microservices architecture:

- **Frontend**: A modern React application built with Vite, Tailwind CSS, Redux Toolkit, Framer Motion, and Firebase. It includes a Monaco-based code editor and rich markdown support.
- **Backend Services** (Node.js & Express):
  - **API Gateway**: Acts as the single entry point, routing requests to the appropriate microservices using `express-http-proxy`.
  - **Auth Service**: Handles user authentication and session management.
  - **Chat Service**: Manages real-time chat functionalities.
  - **Agent Service**: Integrates with AI models and agents.
  - **Billing Service**: Manages subscriptions, usage tracking, and payments.

## Tech Stack

- **Frontend**: React 19, Vite, Tailwind CSS v4, Redux Toolkit, Framer Motion, Firebase, Monaco Editor.
- **Backend**: Node.js, Express, Redis (ioredis).
- **Infrastructure & Deployment**:
  - Docker & Docker Compose
  - AWS (ECR, ECS, S3, CloudFront)
  - GitHub Actions for CI/CD

## Getting Started

### Prerequisites

- Node.js (v18 or higher)
- Docker & Docker Compose
- AWS CLI configured (for deployment)

### Local Development

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Chetancoder-2004/cortexai.git
   cd cortexai
   ```

2. **Setup Environment Variables:**
   Create `.env` files in the frontend and respective backend service directories based on the required configurations (e.g., ports, Redis URIs, external API keys).

3. **Start Backend Services:**
   You can run the backend services individually using `npm run dev` in each service directory (e.g., `backend/gateway`, `backend/services/auth`), or use Docker Compose if configured.

4. **Start the Frontend:**
   ```bash
   cd frontend
   npm install
   npm run dev
   ```

## Deployment

The project includes a robust CI/CD pipeline using GitHub Actions (`.github/workflows/deploy.yml`). 
Upon pushing to the `main` branch, the workflow automatically:
- Builds Docker images for the backend services and pushes them to Amazon ECR.
- Updates Amazon ECS services for the backend.
- Builds the React frontend and syncs it to an Amazon S3 bucket.
- Invalidates the CloudFront cache to serve the latest frontend build.

## License

ISC License
