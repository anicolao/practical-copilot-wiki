# Deployment Setup Guide

This guide describes the manual steps required to enable automatic deployment of the Practical Copilot Wiki to GitHub Pages.

## Prerequisites

- Repository owner/admin access to configure GitHub Pages settings

## Configuration Steps

### 1. Enable GitHub Pages

1. Navigate to your repository on GitHub
2. Go to **Settings** > **Pages** (in the left sidebar)
3. Under **Build and deployment**:
   - **Source**: Select "GitHub Actions"
   - This will enable the workflow-based deployment instead of branch-based deployment

### 2. Verify Workflow Permissions

The deployment workflow requires specific permissions that should already be configured in the `.github/workflows/deploy.yml` file:

```yaml
permissions:
  contents: read
  pages: write
  id-token: write
```

These permissions are already set in the workflow file, so no additional configuration is needed.

### 3. Repository Permissions (if needed)

If the workflow fails with permission errors:

1. Go to **Settings** > **Actions** > **General**
2. Scroll to **Workflow permissions**
3. Ensure either:
   - "Read and write permissions" is selected, OR
   - "Read repository contents and packages permissions" is selected with the "Allow GitHub Actions to create and approve pull requests" option enabled

Note: The workflow uses deployment environments, which handle permissions automatically when GitHub Pages source is set to "GitHub Actions".

## How It Works

Once configured:

1. **Automatic Deployment**: When changes are pushed to the `main` branch:
   - The workflow automatically builds the TiddlyWiki
   - The generated `index.html` is uploaded as a Pages artifact
   - The site is deployed to GitHub Pages

2. **Manual Deployment**: You can also trigger deployment manually:
   - Go to **Actions** > **Deploy to GitHub Pages**
   - Click "Run workflow" and select the `main` branch

## Accessing Your Wiki

After successful deployment, your wiki will be available at:

```
https://<username>.github.io/<repository-name>/
```

For this repository:
```
https://anicolao.github.io/practical-copilot-wiki/
```

## Troubleshooting

### Build Fails with "Dependencies lock file is not found"

This error occurs if `package-lock.json` is missing or ignored. The fix:
- Ensure `package-lock.json` is committed to the repository
- Verify it's not listed in `.gitignore`

### Deployment Fails with Permission Errors

Check that:
1. GitHub Pages source is set to "GitHub Actions" (not "Deploy from a branch")
2. The workflow has the required permissions (see step 2 above)

### Site Shows 404

1. Verify the deployment completed successfully in the Actions tab
2. Check that GitHub Pages is enabled in repository settings
3. Wait a few minutes for the DNS to propagate

### Custom Domain Issues

If you want to use a custom domain:
1. Go to **Settings** > **Pages**
2. Enter your custom domain under "Custom domain"
3. Follow GitHub's instructions to configure DNS records
4. Enable "Enforce HTTPS" once DNS is configured
