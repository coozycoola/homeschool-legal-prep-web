# Homeschool Hour Tracker - Web Hosting

This folder contains the web hosting files for the password reset functionality.

## Files

- `index.html` - Landing page for the domain
- `auth/reset-password.html` - Password reset handler page
- `CNAME` - Custom domain configuration for GitHub Pages

## Deployment Instructions

### Step 1: Create GitHub Repository

1. Go to GitHub and create a new repository
2. Name it something like `homeschool-hour-tracker-web`
3. Make it public (required for free GitHub Pages)
4. Don't initialize with README (we'll upload these files)

### Step 2: Upload Files

1. Upload all files from this `web/` folder to the repository root
2. The structure should be:
   ```
   repository-root/
   ├── index.html
   ├── auth/
   │   └── reset-password.html
   ├── CNAME
   └── README.md
   ```

### Step 3: Enable GitHub Pages

1. Go to repository Settings > Pages
2. Source: Deploy from a branch
3. Branch: main (or master)
4. Folder: / (root)
5. Click Save

### Step 4: Configure Custom Domain

1. **Update CNAME file**: Replace `yourdomain.com` with your actual domain
2. **In Squarespace DNS Settings**:
   - Add a CNAME record:
     - Name: `www`
     - Value: `yourusername.github.io`
   - Add an A record (for apex domain):
     - Name: `@`
     - Value: `185.199.108.153`
   - Add additional A records with values:
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`

### Step 5: Verify Deployment

1. Wait 10-15 minutes for DNS propagation
2. Visit `https://yourdomain.com` - should show landing page
3. Visit `https://yourdomain.com/auth/reset-password.html` - should show password reset handler
4. GitHub Pages will automatically provision SSL certificate

### Step 6: Update App Configuration

1. In your mobile app, update the auth service redirect URL
2. In Supabase dashboard, update the redirect URLs
3. Test the complete password reset flow

## Troubleshooting

- **DNS not working**: Wait up to 24 hours for full propagation
- **SSL certificate issues**: GitHub Pages automatically handles SSL, but it can take a few hours
- **404 errors**: Ensure file paths match exactly (case sensitive)
- **Custom domain not working**: Verify CNAME record points to `yourusername.github.io`

## Important Notes

- GitHub Pages has a 1GB storage limit (more than enough for this use case)
- The service is free for public repositories
- Updates to the repository automatically deploy to the website
- GitHub Pages supports custom domains with automatic SSL