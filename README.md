## Blog

This repository is a part of a blog which explains how to use keycloak as a authentication broker for a NextJS v13 application. Please go through this [blog](https://medium.com/@harshbhandariv/secure-nextjs-v13-application-with-keycloak-6f68406bb3b5)

## Getting Started

### Run keycloak with a postgres database

```bash
docker compose up -d
```

> Please note that the above method cannot be used for production.

### Run the development server

```bash
NODE_OPTIONS='--dns-result-order=ipv4first' npm run dev
```

### To build the project

```bash
npm run build
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

### To start the nextjs server(production mode)

```bash
NODE_OPTIONS='--dns-result-order=ipv4first'  npm start
```

> Make sure to setup the environment variables.

### Realms

Realms are the unit of administration in keycloak, users and clients are configured inside a realm. Our docker compose will initialize a realm in keycloak called _qickstart_.

Login to keycloak with user alice and password alice.

### Prepare Environment

Rename .env.example file to .env.local

Replace KEYCLOAK_CLIENT_SECRET in .env file, for example generate a random string with:
`node -e 'console.log(crypto.randomBytes(16).toString("hex"))'`

In KEYCLOAK*ISSUER replace realm name with \_qickstart*

A sample .env.local file should be:

```
KEYCLOAK_CLIENT_ID="nextjs"
KEYCLOAK_CLIENT_SECRET="c52025ce76009892594e73f00406cbc7"
KEYCLOAK_ISSUER="http://localhost:8080/realms/quickstart"
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="e07c3bf461834f50383a471543e93427"
```

### Troubleshoot

Reset everything:

docker compose rm -svf
sudo rm -rf postgres_db/

In case of authentication problems, you can go to keycloak admin page in: http://localhost:8080/
Use admin/admin as user and pass
