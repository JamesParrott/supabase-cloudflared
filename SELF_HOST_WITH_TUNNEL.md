# Self-hosted Supabase with Cloudflared

## Deployment
https://supabase.com/docs/guides/self-hosting/docker#dashboard-authentication

Get a clone of supabase for the base code
```sh
git clone --depth=1 https://github.com/supabase/supabase
```

Clone this repo
```sh
git clone --depth=1 https://github.com/JamesParrott/supabase-cloudflared
```

Copy this repo's patches into the supabase repo
```sh
cp -rf supabase-cloudflared/* supabase
```


Change dir to the supabase project repo's docker directory
```sh
cd supabase/docker
```

Edit the env variables
```sh
nano .env
```
Populate the env variables specific to your deployment, including those to be kept secret, e.g.:
CLOUDFLARED_TOKEN

Either comment out the SMTP section, or set SMTP_* to your email senders creds




Start the services (in detached mode)
```sh
docker compose up -f docker-compose.yml -f docker-compose.cloudflared.yml -d
```


