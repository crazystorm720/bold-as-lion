Here is the essential documentation to deploy and operate DocuSeal for your LLC, following the same first-principles approach.

### 📚 Core Documentation & Key Concepts

Start with these official resources to understand what DocuSeal is and its core capabilities.

| Resource | Description | Key Takeaways |
| :--- | :--- | :--- |
| **Welcome to DocuSeal** | Official introduction and key features. | DocuSeal is an open-source platform for digital document signing and processing, a modern alternative to DocuSign. |
| **Open Source Self-Hosted** | Official page for on-premises features. | Host on your servers for data privacy; platform is free to self-host with optional Pro plan for advanced features. |

### 💡 Key Features for Your LLC
- **PDF Form Builder**: Drag-and-drop interface to create fillable PDF forms with 10 field types (signature, date, text, etc.).
- **Automatic eSignature**: All signed documents receive a digital, industry-standard PDF eSignature for verification.
- **Self-Hosted & Secure**: Run the platform on your own infrastructure, inside a VPN, to ensure only your organization can access sensitive documents.
- **Robust File Storage**: Store documents locally on your server's disk or on your private cloud storage (AWS S3, Google Cloud, Azure).

### 🚀 Deployment Primitives

You have two main paths for deployment. The core technical requirements are the same for both.

- **Core Dependencies**: 
    - **PostgreSQL**: Serves as the primary database for all document metadata and user records.
    - **Redis**: Used for caching and managing background jobs.
    - **Docker**: The simplest way to run the DocuSeal application itself.

- **Deployment Options**:
    - **Docker on Your Server**: This gives you the most control. The general workflow is:
        1.  Ensure Docker is installed on your Debian server.
        2.  Clone the DocuSeal repository: `git clone https://github.com/docusealco/docuseal.git`.
        3.  Configure environment variables (e.g., `DATABASE_URL`, `REDIS_URL`, `DOCUSEAL_SECRET_KEY`).
        4.  Start the application with `docker-compose up -d`.
    - **Managed PaaS (Railway)**: This is the fastest option, abstracting away server management. You can deploy with a single click, and Railway automatically provisions the necessary PostgreSQL and Redis instances for you.

The table below compares these two main deployment methods.

| Method | Difficulty | Key Features | Best For |
| :--- | :--- | :--- | :--- |
| **Docker on Your Server** | More difficult | Full control over server and configuration; data stored on your hardware. | Users comfortable with server administration and command line. |
| **Managed PaaS (Railway)** | Easier | One-click deploy; automated scaling and dependency management. | Users wanting a quick, hassle-free setup without managing a server. |

### 🛠️ Operational Basics

Once deployed, access your instance via its URL and log in. The initial admin account is created during the first setup.

- **Create and Send a Document**:
    1.  **Upload**: Upload a PDF or Word document and use the drag-and-drop builder to add fields for signatures, dates, and text.
    2.  **Send**: Add recipients by email or phone, or generate a shareable link. You can also sign the document yourself immediately using the "Self Sign" feature.

- **After Sending**:
    - Track all submissions from your dashboard, viewing statuses like "sent," "opened," "awaiting," and "completed".
    - Once all parties sign, you and the signers receive the executed document and a signature certificate (audit log) with detailed timestamps and IP addresses.

### 💰 Pricing and Pro Features

- **Self-Hosted Version**: The open-source version is **free forever** without limitations for self-hosting.
- **Pro Plan**: For your LLC, a paid Pro plan ($240/year per user) unlocks business-critical features like white-labeling (removing DocuSeal branding), automated SMS reminders, and Single Sign-On (SAML).

DocuSeal is a powerful and cost-effective way to manage document signing for your business. The open-source version is more than capable for getting started.

If you run into specific questions about Docker configuration or the initial setup wizard, feel free to ask.
