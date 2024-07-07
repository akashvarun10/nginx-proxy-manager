### Nginx Proxy Manager

1. **Install Docker and Docker-Compose**
    - Docker Install documentation
    - Docker-Compose Install documentation

2. **Create a `docker-compose.yml` file similar to this:**
```yaml
version: '3.8'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '81:81'
      - '443:443'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```
This is the bare minimum configuration required. See the documentation for more.

3. **Bring up your stack by running**
```bash
docker-compose up -d

# If using docker-compose-plugin
docker compose up -d
```

4. **Log in to the Admin UI**
   When your docker container is running, connect to it on port 81 for the admin interface. Sometimes this can take a little bit because of the entropy of keys.
   [http://127.0.0.1:81](http://127.0.0.1:81)

   **Default Admin User:**
   - Email: `admin@example.com`
   - Password: `changeme`
   
   Immediately after logging in with this default user, you will be asked to modify your details and change your password.

### Features

- Beautiful and Secure Admin Interface based on Tabler
- Easily create forwarding domains, redirections, streams, and 404 hosts without knowing anything about Nginx
- Free SSL using Let's Encrypt or provide your own custom SSL certificates
- Access Lists and basic HTTP Authentication for your hosts
- Advanced Nginx configuration available for super users
- User management, permissions, and audit log