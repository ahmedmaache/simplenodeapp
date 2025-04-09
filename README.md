# Node.js Application for cPanel Deployment

This is a comprehensive Node.js application optimized for deployment on cPanel's Node.js Selector.

## Features
- Express.js web server
- Static file serving
- Sample API endpoint
- cPanel-specific configuration
- Environment variables support

## Prerequisites
- cPanel hosting with Node.js Selector enabled
- Node.js 18+ installed on server
- SSH access (recommended)

## Installation

1. Upload all files to your cPanel account (via File Manager or FTP)
2. In cPanel, navigate to "Node.js Selector"
3. Click "Create Application"
4. Set the following parameters:
   - Application root: `/home/yourusername/nodeapp` (path where you uploaded files)
   - Application URL: `yourdomain.com` or subdomain
   - Application startup file: `app.js`
   - Passenger log file: `/home/yourusername/logs/nodeapp.log`
5. Click "Save"

## Configuration

1. Set environment variables in cPanel:
   - In Node.js Selector, go to "Environment Variables"
   - Add `NODE_ENV=production`
   - Add `PORT=3000` (must match .htaccess)

2. Required .htaccess configuration is already included in the project.

## Running the Application

1. SSH into your server (recommended)
2. Navigate to your application directory:
   ```bash
   cd ~/nodeapp
   ```
3. Install dependencies:
   ```bash
   npm install --production
   ```
4. The application will automatically start via Passenger when accessed

## Troubleshooting

1. If application doesn't start:
   - Check error logs in `/home/yourusername/logs/nodeapp.log`
   - Verify file permissions (should be 755 for directories, 644 for files)
   - Ensure Node.js version matches package.json "engines" requirement

2. Common issues:
   - PORT mismatch between .htaccess and .env
   - Missing node_modules (run `npm install`)
   - Incorrect application root path in cPanel

## Development

For local development:
```bash
npm install
npm run dev