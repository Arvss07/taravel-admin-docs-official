# Configuration

This guide covers configuring your Tara-Vel Admin environment after installation.

## Environment Variables

### Required Environment Variables

Create a `.env.local` file in your project root with the following variables:

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

# Cloudinary Configuration
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email Configuration
SMTP_HOST=your_smtp_host
SMTP_PORT=587
SMTP_USER=your_smtp_user
SMTP_PASS=your_smtp_password
SMTP_FROM=noreply@taravel.app

# App Configuration
NEXT_PUBLIC_APP_URL=http://localhost:3000
NEXT_PUBLIC_APP_NAME=Tara-Vel Admin
```

## Firebase Setup

### 1. Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project
3. Enable Authentication, Firestore, and Storage

### 2. Configure Authentication

```bash
# Enable Email/Password authentication
# Configure authorized domains
```

### 3. Set up Firestore

```bash
# Deploy Firestore rules and indexes
npm run firebase:deploy-rules-indexes
```

## Cloudinary Setup

### 1. Create Cloudinary Account

1. Sign up at [Cloudinary](https://cloudinary.com/)
2. Get your cloud name, API key, and API secret
3. Add them to your environment variables

## Next Steps

Once configuration is complete:

1. **[First Steps](first-steps.md)** - Run the application and explore features
2. **[Architecture](../architecture/system-overview.md)** - Understand the system design
