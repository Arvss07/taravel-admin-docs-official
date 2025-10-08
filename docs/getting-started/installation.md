# Installation

This guide will walk you through setting up the Tara-Vel Admin development environment from scratch.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

### Required Software

- **Node.js** 18.17 or later
- **npm** 9.0 or later (comes with Node.js)
- **Git** for version control
- **Firebase CLI** for Firebase operations

### Optional but Recommended

- **VS Code** with recommended extensions
- **Firebase Tools** for local development

## Step 1: Clone the Repository

!!! note "Private Repository Access"
    The Tara-Vel Admin repository is currently private. You'll need to be granted access by the development team to clone the repository.

```bash
# Clone the repository (requires access)
git clone https://github.com/Arvss07/taravel-admin-official.git
cd taravel-admin-official

# Verify you're in the correct directory
dir
```

!!! warning "Access Required"
    If you don't have access to the private repository, contact the development team to request access before proceeding with the installation.

## Step 2: Install Dependencies

```bash
# Install all project dependencies
npm install

# This will install:
# - Next.js and React dependencies
# - UI component libraries (Radix UI, shadcn/ui)
# - Firebase SDK and admin SDK
# - Development tools (ESLint, Prettier, etc.)
```

## Step 3: Firebase CLI Setup

```bash
# Install Firebase CLI globally
npm install -g firebase-tools

# Login to Firebase
firebase login

# Verify installation
firebase --version
```

## Step 4: Environment Configuration

### Create Environment File

```bash
# Copy the example environment file
cp .env.example .env.local
```

### Configure Environment Variables

Edit `.env.local` with your Firebase project details:

```env
# Firebase Configuration
NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id

# Firebase Admin SDK (Server-side)
FIREBASE_ADMIN_PROJECT_ID=your_project_id
FIREBASE_ADMIN_CLIENT_EMAIL=your_service_account_email
FIREBASE_ADMIN_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\nYour private key here\n-----END PRIVATE KEY-----\n"

# Cloudinary Configuration (for image processing)
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email Configuration (for notifications)
SMTP_HOST=your_smtp_host
SMTP_PORT=587
SMTP_USER=your_smtp_user
SMTP_PASS=your_smtp_password

# App Configuration
NEXT_PUBLIC_APP_URL=http://localhost:3000
NEXT_PUBLIC_APP_NAME=Tara-Vel Admin
```

## Step 5: Firebase Project Setup

### Initialize Firebase in Your Project

```bash
# Initialize Firebase in your project
firebase init

# Select the following services:
# - Firestore: Configure security rules and indexes
# - Hosting: Configure files for Firebase Hosting
# - Functions: Configure a Cloud Functions directory
```

### Configure Firestore

```bash
# Deploy Firestore rules and indexes
npm run firebase:deploy-rules-indexes

# This will deploy:
# - firestore.rules (security rules)
# - firestore.indexes.json (database indexes)
```

## Step 6: Verify Installation

### Start Development Server

```bash
# Start the development server
npm run dev

# The application will be available at:
# http://localhost:3000
```

### Test Firebase Connection

```bash
# Test Firebase admin SDK connection
npm run firebase:test-admin-sdk

# Test verification system
npm run firebase:test-verification
```

## Step 7: Development Tools Setup

### VS Code Extensions (Recommended)

Install these VS Code extensions for the best development experience:

```json
{
  "recommendations": [
    "bradlc.vscode-tailwindcss",
    "esbenp.prettier-vscode",
    "ms-vscode.vscode-typescript-next",
    "firebase.vscode-firebase-explorer",
    "ms-vscode.vscode-json",
    "formulahendry.auto-rename-tag",
    "christian-kohler.path-intellisense"
  ]
}
```

### Git Hooks Setup

```bash
# Install Husky git hooks
npm run prepare

# This sets up pre-commit hooks for:
# - ESLint code linting
# - Prettier code formatting
# - Type checking
```

## Troubleshooting Installation

### Common Issues

#### Node.js Version Issues
```bash
# Check your Node.js version
node --version

# If you need to update Node.js, use nvm:
nvm install 18.17.0
nvm use 18.17.0
```

#### Firebase Permission Issues
```bash
# Re-authenticate with Firebase
firebase logout
firebase login

# Check your Firebase project access
firebase projects:list
```

#### Dependency Installation Issues
```bash
# Clear npm cache and reinstall
npm cache clean --force
rm -rf node_modules package-lock.json
npm install
```

#### Environment Variable Issues
```bash
# Verify your .env.local file exists and has correct values
cat .env.local

# Check for any syntax errors in environment variables
```

### Getting Help

If you encounter issues during installation:

1. Check the [Troubleshooting Guide](../troubleshooting/common-issues.md)
2. Open an issue on GitHub with:
   - Your operating system
   - Node.js version
   - Error messages
   - Steps you've already tried

## Next Steps

Once installation is complete:

1. **[Configure your environment](configuration.md)** - Set up Firebase services
2. **[Take your first steps](first-steps.md)** - Explore the application
3. **[Learn the architecture](../architecture/system-overview.md)** - Understand the system design

---

*Installation complete! Let's move on to [configuration](configuration.md).*
