# Deploy n8n to Railway

This guide will help you deploy n8n to [Railway](https://railway.app/) with just a few clicks.

## Quick Deploy

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/n8n)

## Manual Deployment

### Prerequisites

- A [Railway account](https://railway.app/) (free tier available)
- Git installed on your local machine (optional, for cloning)

### Step 1: Create a New Project

1. Log in to your [Railway dashboard](https://railway.app/dashboard)
2. Click on "New Project"
3. Select "Deploy from GitHub repo"
4. Connect your GitHub account and select this repository

### Step 2: Configure Environment Variables

Railway will automatically detect the `railway.json` configuration. You need to set the following environment variables in your Railway project:

#### Required Variables:

- `N8N_BASIC_AUTH_ACTIVE=true` - Enable basic authentication
- `N8N_BASIC_AUTH_USER=<your-username>` - Your admin username
- `N8N_BASIC_AUTH_PASSWORD=<your-password>` - Your admin password
- `N8N_HOST=<your-railway-domain>` - Will be auto-assigned by Railway
- `WEBHOOK_URL=https://<your-railway-domain>/` - Your Railway URL

#### Optional Variables:

- `N8N_PORT=5678` - Port (default: 5678)
- `N8N_PROTOCOL=https` - Protocol (use https on Railway)
- `GENERIC_TIMEZONE=America/New_York` - Your timezone
- `N8N_ENCRYPTION_KEY=<random-key>` - For encrypting credentials (generate a secure random string)

### Step 3: Add Persistent Storage (Recommended)

1. In your Railway project, click on your service
2. Go to the "Variables" tab
3. Add a volume mount at `/home/node/.n8n` to persist your data

### Step 4: Deploy

1. Railway will automatically build and deploy your application using the Dockerfile
2. Once deployed, you'll receive a public URL (e.g., `your-app.railway.app`)
3. Visit your URL to access the n8n editor

### Step 5: Access on Mobile

Your n8n instance is now optimized for mobile access! You can:

- Access the workflow editor from your phone or tablet
- Create and edit workflows on the go
- The interface is responsive and mobile-friendly

## Database Configuration

For production use, it's recommended to use an external database:

### PostgreSQL (Recommended)

1. Add a PostgreSQL database to your Railway project
2. Add these environment variables:
   - `DB_TYPE=postgresdb`
   - `DB_POSTGRESDB_HOST=<provided-by-railway>`
   - `DB_POSTGRESDB_PORT=5432`
   - `DB_POSTGRESDB_DATABASE=<database-name>`
   - `DB_POSTGRESDB_USER=<database-user>`
   - `DB_POSTGRESDB_PASSWORD=<database-password>`

### MySQL

1. Add a MySQL database to your Railway project
2. Add these environment variables:
   - `DB_TYPE=mysqldb`
   - `DB_MYSQLDB_HOST=<provided-by-railway>`
   - `DB_MYSQLDB_PORT=3306`
   - `DB_MYSQLDB_DATABASE=<database-name>`
   - `DB_MYSQLDB_USER=<database-user>`
   - `DB_MYSQLDB_PASSWORD=<database-password>`

## Troubleshooting

### Application won't start

- Check the Railway logs for error messages
- Ensure all required environment variables are set
- Verify that the volume is properly mounted

### Can't access from mobile

- Ensure the application is deployed successfully
- Check that HTTPS is enabled (Railway provides this by default)
- Clear your mobile browser cache

### Workflows aren't persisting

- Add a persistent volume mount at `/home/node/.n8n`
- Or configure an external database (recommended for production)

## Resources

- [n8n Documentation](https://docs.n8n.io/)
- [Railway Documentation](https://docs.railway.app/)
- [n8n Community Forum](https://community.n8n.io/)

## Cost Optimization

Railway offers a free tier with:
- $5 free credit per month
- Usage-based pricing after that

To optimize costs:
- Use the free tier for testing
- Scale down replicas when not in use
- Consider using Railway's sleep mode for development instances

## Security Notes

- Always use strong passwords for `N8N_BASIC_AUTH_PASSWORD`
- Generate a secure random string for `N8N_ENCRYPTION_KEY`
- Enable HTTPS (enabled by default on Railway)
- Regularly update your n8n instance
- Consider using Railway's private networking for database connections

## Support

For issues specific to:
- **n8n**: Visit the [n8n community forum](https://community.n8n.io/)
- **Railway deployment**: Check [Railway's documentation](https://docs.railway.app/)
