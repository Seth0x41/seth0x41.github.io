# Multiple Domain Setup for GitHub Pages

This document explains how your blog is set up to work with both GitHub Pages URL (`seth0x41.github.io`) and your custom domain (`seth0x41.tech`).

## How It Works

1. **Primary domain**: The site primarily uses your custom domain `seth0x41.tech`
2. **GitHub Pages domain**: GitHub automatically redirects `seth0x41.github.io` to your custom domain
3. **SEO benefits**: Canonical URLs ensure search engines understand both domains refer to the same content

## Key Files and Settings

### 1. CNAME File

The `CNAME` file in the root of your repository tells GitHub Pages to use your custom domain. Current content:
```
seth0x41.tech
```

### 2. _config.yml

The configuration specifies your primary domain:
```yaml
url: "https://seth0x41.tech" # Primary domain
baseurl: "" # Empty for sites at the root of domain
canonical_url: true # Ensures proper canonical URL handling
```

### 3. Canonical URLs

The `<link rel="canonical">` tag in the HTML head tells search engines which version of the URL is the "official" one. This prevents duplicate content issues.

## DNS Configuration

To maintain both domains, ensure your DNS is configured correctly:

1. **For your custom domain (`seth0x41.tech`)**:
   - Add an `A` record pointing to GitHub Pages IP addresses:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Or add a `CNAME` record pointing to `seth0x41.github.io` (if using a subdomain)

2. **For the GitHub Pages domain**:
   - No additional configuration needed - GitHub handles this automatically

## Benefits of This Setup

1. **Branding**: Your custom domain reinforces your personal/professional brand
2. **Fallback**: If your custom domain has issues, the GitHub Pages domain still works
3. **SEO**: Search engines will understand both URLs refer to the same content
4. **Flexibility**: You can change your primary domain in the future without losing traffic

## Maintenance

If you need to change domains in the future:

1. Update the `url` in `_config.yml`
2. Update the `CNAME` file with your new domain
3. Update your DNS settings
4. The canonical URL tags will ensure a smooth transition for SEO

## Troubleshooting

- If your custom domain isn't working, check DNS propagation (can take up to 48 hours)
- Verify HTTPS is enforced in your GitHub repository settings
- Check GitHub Pages settings to ensure your custom domain is properly recognized 