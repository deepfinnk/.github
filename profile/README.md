# DeepFinnk - AI Financial Assistant (Bunq Hackathon Project)

Welcome to DeepFinnk, an AI-powered financial assistant designed to help you manage your Bunq finances through natural language interaction. This project was built for a hackathon and comprises several interconnected components.

## Project Goal

DeepFinnk aims to simplify personal finance management by allowing users to:

*   **Query:** Ask financial questions or state financial goals in plain English.
*   **Plan:** Receive AI-generated, actionable financial plans based on their Bunq account data.
*   **Execute:** Automatically implement these plans (e.g., create budget accounts, transfer funds) via the Bunq API.

## Components

This project is divided into three main repositories:

1.  **Frontend Web Application (`webapp`)**
    *   **Purpose:** Provides the user interface for viewing account balances, initiating actions, and interacting with the AI assistant via chat.
    *   **Technology:** Next.js, React, TypeScript, Tailwind CSS, shadcn/ui, v0.dev.
    *   **Repository:** [https://github.com/deepfinnk/webapp](https://github.com/deepfinnk/webapp)
    *   **Deployment:** [View Live Demo (Vercel)](https://vercel.com/adamcretu36-gmailcoms-projects/v0-new-project-ul4s8obpkvs) *(Note: Link might be specific to initial deployment)*

2.  **AI Research Agent (`research-agent`)**
    *   **Purpose:** Handles natural language understanding, financial plan generation using AI, and orchestrates communication between the frontend and the Bunq service.
    *   **Technology:** Python, Flask, Camel AI (`camel-ai[owl]`), Flasgger.
    *   **Repository:** [https://github.com/deepfinnk/research-agent](https://github.com/deepfinnk/research-agent)

3.  **Bunq MCP Service (`bunq-service`)**
    *   **Purpose:** Acts as a secure interface to the Bunq API, executing the financial tasks requested by the AI agent. Uses a Multi-Agent Collaboration Platform (MCP) approach.
    *   **Technology:** Python, Flask, Camel AI, Bunq SDK, Docker.
    *   **Repository:** [https://github.com/deepfinnk/bunq-service](https://github.com/deepfinnk/bunq-service)

## Getting Started

To run the entire DeepFinnk system, you will need to set up and run each component individually. Please refer to the `README.md` file within each component's repository for specific setup and running instructions:

*   [Frontend Setup](https://github.com/deepfinnk/webapp#getting-started)
*   [AI Agent Setup](https://github.com/deepfinnk/research-agent#setup)
*   [Bunq Service Setup](https://github.com/deepfinnk/bunq-service#setup)

Ensure all necessary environment variables (like API keys and service URLs) are configured correctly for the components to communicate.

## Architecture Overview (Conceptual)

```mermaid
graph TD
    A[User via Frontend (Next.js)] --> B(AI Agent Service (Flask));
    B --> C{Financial Query / Goal};
    B --> D[Plan Generation (Camel AI)];
    D --> E{Generated Plan};
    B --> F(Bunq MCP Service (Flask));
    F --> G{Execute Plan Actions};
    G --> H[Bunq API];
    H --> F;
    F --> B;
    B --> A;

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style F fill:#ccf,stroke:#333,stroke-width:2px
    style H fill:#ff9,stroke:#333,stroke-width:2px
```

*(This is a simplified representation. Refer to individual repositories for detailed architecture.)*
