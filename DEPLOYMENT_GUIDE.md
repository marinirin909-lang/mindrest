# MindRest Web Deployment Guide

## 🌐 Correct URLs

**IMPORTANT**: The correct domain is:
- ✅ **Correct**: `https://mindrest.mindpilot.online/`
- ❌ **Incorrect**: `http://restmind.mindpilot.online/`

## 📁 Files to Deploy

### **Main Web App**
- **File**: `index.html` (renamed from `mindrest.html`)
- **Purpose**: Main meditation app
- **URL**: `https://mindrest.mindpilot.online/`

### **Landing Page**
- **File**: `mindrest-landing.html`
- **Purpose**: Marketing/landing page
- **URL**: `https://mindrest.mindpilot.online/landing` (or configure as needed)

## 🚀 Deployment Steps

### **1. Web Server Configuration**

#### **Apache Server**
```apache
# Ensure index.html is the default file
DirectoryIndex index.html

# Enable HTTPS
<VirtualHost *:443>
    ServerName mindrest.mindpilot.online
    DocumentRoot /path/to/your/web/root
    # SSL configuration here
</VirtualHost>
```

#### **Nginx Server**
```nginx
server {
    listen 443 ssl;
    server_name mindrest.mindpilot.online;
    root /path/to/your/web/root;
    index index.html;
    
    # SSL configuration here
}
```

#### **Shared Hosting**
- Upload `index.html` to the public_html or www directory
- Ensure `index.html` is set as the default page
- Most hosts automatically serve `index.html` as default

### **2. File Upload**

#### **Main App Files**
```
📁 / (web root)
├── 📄 index.html              # Main app (renamed from mindrest.html)
├── 📄 mindrest-landing.html   # Landing page
└── 📁 assets/                # If you have additional assets
```

#### **Upload Methods**
1. **FTP/SFTP**: Upload files directly to web root
2. **File Manager**: Use hosting control panel file manager
3. **Git**: Deploy from Git repository
4. **CI/CD**: Use deployment pipelines

### **3. SSL Certificate**

#### **Required for HTTPS**
- Install SSL certificate for `mindrest.mindpilot.online`
- Most hosting providers offer free SSL (Let's Encrypt)
- Ensure HTTPS redirects are configured

#### **Redirect HTTP to HTTPS**
```apache
# Apache
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

```nginx
# Nginx
server {
    listen 80;
    server_name mindrest.mindpilot.online;
    return 301 https://$server_name$request_uri;
}
```

## 🔍 Verification Steps

### **1. Check URLs**
- [ ] `https://mindrest.mindpilot.online/` loads main app
- [ ] `https://mindrest.mindpilot.online/mindrest-landing.html` loads landing page
- [ ] All internal links work correctly
- [ ] Privacy policy and terms of service links work

### **2. Test Functionality**
- [ ] Theme toggle works (light/dark mode)
- [ ] Subtitle displays correctly
- [ ] All app features work (meditation, sleep sounds, journaling)
- [ ] Mobile responsive design works
- [ ] Privacy policy and terms of service links open correctly

### **3. SSL Verification**
- [ ] HTTPS works without warnings
- [ ] SSL certificate is valid
- [ ] HTTP redirects to HTTPS

## 🛠️ Troubleshooting

### **Common Issues**

#### **1. Page Not Found**
- **Cause**: Wrong file name or location
- **Solution**: Ensure `index.html` is in the web root directory

#### **2. Wrong Domain**
- **Cause**: Using `restmind.mindpilot.online` instead of `mindrest.mindpilot.online`
- **Solution**: Use correct domain name

#### **3. HTTP Not Working**
- **Cause**: SSL certificate not installed or misconfigured
- **Solution**: Install SSL certificate and configure HTTPS

#### **4. Theme Toggle Not Working**
- **Cause**: JavaScript not loading or CORS issues
- **Solution**: Check browser console for errors

#### **5. Links Not Working**
- **Cause**: Wrong URLs in configuration
- **Solution**: Verify all URLs use `https://mindrest.mindpilot.online/`

### **Debugging Steps**

1. **Browser Console**: Check for JavaScript errors
2. **Network Tab**: Verify all resources load correctly
3. **SSL Checker**: Use online SSL validation tools
4. **DNS Check**: Ensure domain points to correct server

## 📱 Android App Configuration

### **Current Configuration**
```json
{
  "appId": "com.mindrest.app",
  "appName": "MindRest - Meditation & Sleep",
  "webDir": "public",
  "server": {
    "url": "https://mindrest.mindpilot.online/",
    "androidScheme": "https"
  }
}
```

### **Deployment Ready**
- ✅ Android app configured for correct URL
- ✅ Privacy policy and terms of service links configured
- ✅ Theme toggle functionality integrated
- ✅ New .aab file built and ready for Play Store

## 🔄 Post-Deployment

### **1. Update DNS**
- Point `mindrest.mindpilot.online` to your server
- Wait for DNS propagation (typically 24-48 hours)

### **2. Submit to Play Store**
- Upload the new .aab file to Google Play Console
- Ensure all store listing information is correct
- Test the app thoroughly before release

### **3. Monitor Performance**
- Check website loading speed
- Monitor app performance
- Gather user feedback

## 📞 Support

### **If Issues Occur**
1. **Check Domain**: Ensure you're using `mindrest.mindpilot.online`
2. **Verify Files**: Confirm `index.html` is in the correct location
3. **Test HTTPS**: Ensure SSL certificate is properly installed
4. **Clear Cache**: Clear browser cache and test again

### **Contact Information**
- **Domain**: `mindrest.mindpilot.online`
- **Main App**: `https://mindrest.mindpilot.online/`
- **Landing Page**: `https://mindrest.mindpilot.online/mindrest-landing.html`

---

## ✅ Deployment Checklist

### **Pre-Deployment**
- [ ] All files are ready (`index.html`, `mindrest-landing.html`)
- [ ] SSL certificate is installed
- [ ] DNS is configured correctly
- [ ] Server is configured to serve `index.html` as default

### **Post-Deployment**
- [ ] Main app loads at `https://mindrest.mindpilot.online/`
- [ ] Landing page loads correctly
- [ ] All internal links work
- [ ] Theme toggle functions properly
- [ ] Mobile responsive design works
- [ ] Privacy policy and terms of service links work
- [ ] Android app connects to correct URL

**Status**: 🚀 **Ready for Deployment**

Your MindRest web app is properly configured with:
- Correct domain name (`mindrest.mindpilot.online`)
- Main page as `index.html`
- All functionality working
- Theme toggle and subtitle features
- Android app ready for Play Store submission
