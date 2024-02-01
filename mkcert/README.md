# Creating and Adding SSL Certificate using mkcert

## Prerequisites
- Install `mkcert`: https://github.com/FiloSottile/mkcert#installation

## Step 1: Install mkcert
```bash
mkcert -install
```

This command installs a local CA in the system trust store.

## Step 2: Create SSL Certificate
```bash
# Replace "yourdomain.local" with the domain you want to use
mkcert -key-file key.pem -cert-file cert.pem yourdomain.local
```

This command generates a self-signed SSL certificate for the specified domain.

## Step 3: Locate the Certificate Files
```bash
# By default, mkcert stores certificates in the ~/.local/share/mkcert directory
ls -la ~/.local/share/mkcert
```

Find the `key.pem` and `cert.pem` files.

## Step 4: Import Certificate into Chrome

### 4.1 Open Chrome
- Go to Chrome Settings > Privacy and Security > Manage Certificates.

### 4.2 Import Certificate
- Under the "Authorities" tab, click "Import."
- Select the `rootCA.pem` file from the `mkcert` directory.

## Step 5: Import Certificate into Firefox

### 5.1 Open Firefox
- Go to Firefox Preferences > Privacy & Security > View Certificates > Authorities.

### 5.2 Import Certificate
- Click "Import" and select the `rootCA.pem` file from the `mkcert` directory.

## Step 6: Test SSL Connection
- Start your local server using the generated SSL certificate.
- Access your application in both Chrome and Firefox using `https://yourdomain.local`.

**Note:** For production, obtain a valid SSL certificate from a certificate authority.
