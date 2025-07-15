# App Configuration Template

## Replace Domain Placeholders

Once your domain is set up, you need to update these files in your mobile app:

### 1. Update Auth Service

**File**: `services/authService.ts`  
**Line**: ~132

```typescript
// BEFORE (current placeholder):
redirectTo: 'https://yourapp.com/auth/reset-password',

// AFTER (replace with your actual domain):
redirectTo: 'https://yourdomain.com/auth/reset-password',
```

### 2. Update Supabase Dashboard

**Location**: Supabase Dashboard → Authentication → URL Configuration

**Update these redirect URLs**:
```
// BEFORE:
https://yourapp.com/auth/reset-password

// AFTER:
https://yourdomain.com/auth/reset-password
```

### 3. Update Web Files

**File**: `web/CNAME`  
**Content**: Replace `yourdomain.com` with your actual domain

**File**: `web/README.md`  
**Content**: Replace all instances of `yourdomain.com` with your actual domain

### 4. Verification Checklist

After making these changes:

✅ **Auth Service**: Updated redirect URL to your domain  
✅ **Supabase Dashboard**: Updated redirect URLs  
✅ **Web Files**: CNAME file contains your domain  
✅ **DNS**: A records and CNAME record configured  
✅ **GitHub Pages**: Repository deployed and accessible  
✅ **SSL**: HTTPS working for your domain  
✅ **Testing**: Password reset flow works end-to-end  

## Quick Update Script

Here's exactly what to replace in each file:

### services/authService.ts
```diff
- redirectTo: 'https://yourapp.com/auth/reset-password',
+ redirectTo: 'https://yourdomain.com/auth/reset-password',
```

### web/CNAME
```diff
- yourdomain.com
+ yourdomain.com
```

### Supabase Dashboard
```diff
- https://yourapp.com/auth/reset-password
+ https://yourdomain.com/auth/reset-password
```

## Example with Real Domain

If your domain is `homeschooltracker.com`, here's what each would look like:

**services/authService.ts**:
```typescript
redirectTo: 'https://homeschooltracker.com/auth/reset-password',
```

**web/CNAME**:
```
homeschooltracker.com
```

**Supabase redirect URLs**:
```
https://homeschooltracker.com/auth/reset-password
homeschooltracker://auth/reset-password
exp://localhost:19000/--/auth/reset-password
```

## Testing the Complete Flow

1. **Deploy web files** to GitHub Pages
2. **Configure DNS** in Squarespace
3. **Update app configuration** with your domain
4. **Update Supabase** redirect URLs
5. **Test password reset** by:
   - Requesting password reset email
   - Clicking email link
   - Verifying web page opens
   - Confirming mobile app opens or manual token works
   - Completing password reset in mobile app

Once all steps are complete, your password reset flow will work seamlessly!