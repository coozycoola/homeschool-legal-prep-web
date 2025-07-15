# Squarespace DNS Configuration for GitHub Pages

## Step-by-Step DNS Setup

### 1. Access Squarespace DNS Settings

1. Log into your Squarespace account
2. Go to **Settings** → **Domains**
3. Click on your domain name
4. Click **DNS Settings**

### 2. Configure DNS Records

You need to add these DNS records:

#### A Records (for apex domain)
Add these four A records:

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

#### CNAME Record (for www subdomain)
Add this CNAME record:

| Type | Name | Value |
|------|------|-------|
| CNAME | www | yourusername.github.io |

**Replace `yourusername` with your actual GitHub username!**

### 3. Detailed Instructions

#### Adding A Records:
1. Click **Add Record**
2. Select **A** from the dropdown
3. Leave **Host** field empty (or enter `@`)
4. Enter IP address in **Points to** field
5. Click **Add Record**
6. Repeat for all four IP addresses

#### Adding CNAME Record:
1. Click **Add Record**
2. Select **CNAME** from the dropdown
3. Enter `www` in **Host** field
4. Enter `yourusername.github.io` in **Points to** field
5. Click **Add Record**

### 4. Verification

After adding all records, your DNS settings should look like this:

```
Type    Host    Points to
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
CNAME   www     yourusername.github.io
```

### 5. Wait for Propagation

- **DNS propagation time**: 15 minutes to 24 hours
- **Most changes**: Active within 1-2 hours
- **SSL certificate**: GitHub Pages will automatically provision SSL

### 6. Test Your Setup

After DNS propagation:

1. Visit `http://yourdomain.com` - should redirect to HTTPS and show your landing page
2. Visit `https://www.yourdomain.com` - should also work
3. Visit `https://yourdomain.com/auth/reset-password.html` - should show password reset handler

### 7. Common Issues & Solutions

#### Issue: "DNS_PROBE_FINISHED_NXDOMAIN"
- **Solution**: Wait longer for DNS propagation (up to 24 hours)
- **Check**: Verify A records are pointing to the correct GitHub IP addresses

#### Issue: "Certificate not valid"
- **Solution**: GitHub Pages automatically provisions SSL, but it can take 1-24 hours
- **Check**: Ensure your CNAME file in the repository contains the correct domain

#### Issue: "404 Not Found"
- **Solution**: Verify GitHub Pages is enabled and deploying from the correct branch
- **Check**: Ensure files are in the repository root, not in a subfolder

#### Issue: "Repository not found"
- **Solution**: Ensure the repository is public (required for free GitHub Pages)
- **Check**: Verify the CNAME record points to `yourusername.github.io` (not `.com`)

### 8. Alternative: Using Subdomain

If you prefer to use a subdomain (like `app.yourdomain.com`):

1. **Add CNAME record**:
   - Type: CNAME
   - Host: app
   - Points to: yourusername.github.io

2. **Update CNAME file** in repository to contain: `app.yourdomain.com`

3. **Update app configuration** to use `https://app.yourdomain.com`

### 9. Squarespace-Specific Notes

- **No TTL setting**: Squarespace manages TTL automatically
- **Propagation**: Usually faster than other registrars (15-60 minutes)
- **SSL**: Works seamlessly with GitHub Pages SSL
- **Support**: Squarespace support can help verify DNS records if needed

### 10. Final Checklist

✅ All A records added with correct GitHub IP addresses  
✅ CNAME record added pointing to yourusername.github.io  
✅ CNAME file in repository updated with your domain  
✅ GitHub Pages enabled and deploying  
✅ DNS propagation completed (test with online DNS checker)  
✅ SSL certificate provisioned (https works)  
✅ Both yourdomain.com and www.yourdomain.com work  
✅ Password reset handler accessible at /auth/reset-password.html  

Once all items are checked, your web hosting is ready for the password reset flow!