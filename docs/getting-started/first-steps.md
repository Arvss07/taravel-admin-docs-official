# First Steps

Now that you have Tara-Vel Admin installed and configured, let's take your first steps with the application.

## Starting the Application

### 1. Start Development Server

```bash
# Start the development server
npm run dev

# The application will be available at:
# http://localhost:3000
```

### 2. Access the Application

Open your browser and navigate to `http://localhost:3000`. You should see the login page.

## Initial Setup

### 1. Create Admin User

The first time you run the application, you'll need to create an admin user:

1. Go to the Firebase Authentication console
2. Go to the Users tab
3. Create a new user
4. Set the user's email and password
5. Copy the document id of the user
6. Copy the email of the user
7. Go to the Firestore database
8. Go to the users collection
9. create a new entry where the document id matches the user's document id
10. Add the following fields:

``` json
  // Firestore metadata fields
  name: string;
  role: "admin";
  created_at: string; // current date and time in ISO format
  status: "active";
```

### 2. Explore the Dashboard

Once logged in, you'll see the main dashboard with:

- **System Overview** - Key metrics and statistics
- **Recent Activity** - Latest system events
- **Quick Actions** - Shortcuts to common tasks

## Key Features to Explore

### 1. User Management

- Navigate to **Users** in the sidebar
- View existing users
- Create new users

### 2. Vehicle Management

- Go to **Vehicles** section
- Add vehicle types (Bus, Van)
- Configure vehicle settings

### 3. ID Verification

- Check **ID Verification** section
- Review pending verifications
- Process verification requests

### 4. System Monitoring

- Explore **System Logs**
- Monitor system health
- Review audit trails

### Database Operations

```bash
# View Firestore data
firebase firestore:query

# Export data
npm run firebase:export-data

# Import data
npm run firebase:import-data
```

## Troubleshooting

### Common Issues

1. **Port already in use**
   ```bash
   # Kill process using port 3000
   npx kill-port 3000
   ```

2. **Firebase connection issues**
   ```bash
   # Test Firebase connection
   npm run firebase:test-admin-sdk
   ```

3. **Environment variable issues**
   ```bash
   # Verify .env.local exists and has correct values
   cat .env.local
   ```

## Next Steps

Now that you're familiar with the basics:

1. **Explore Architecture** - Learn about the system design
2. **Read API Documentation** - Understand the available endpoints

## Getting Help

If you encounter issues:

- Review the [Architecture Documentation](../architecture/system-overview.md)
- Contact the development team
- Open an issue on GitHub

---

*Congratulations! You've successfully set up and started using Tara-Vel Admin.*
