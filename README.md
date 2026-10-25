# Werewolf Town — standalone admin console ("High Inquisitor")

A single static page (`index.html`, no build). It is the same console the backend
serves at `/admin`, but hosted separately and talking to the backend API over HTTPS.

## Use it

1. Open the site, pick the server (**Cloud (Render)** by default, or **Local (:4477)**).
2. Paste your admin secret key and press **Connect**. The key is stored only in
   that browser's localStorage and sent as the `x-admin-key` header.

## Set up on Render

1. On the **backend** service, add the env var `ADMIN_SECRET_KEY` (a long random string).
   The built-in default key is rejected on hosted servers, so without this you can't sign in.
2. Deploy this folder as a Static Site (`render.yaml` already has `fangs-and-torches-admin`,
   publish directory `admin-site`, no build command).
3. Optional: attach a custom domain such as `admin.<your-domain>`.

If the backend isn't at `https://fangs-torches.onrender.com`, change `DEFAULT_BASE_URL`
and the `<option>` values in `index.html`.

## Local preview

```bash
npx serve admin-site
```
(Local backend: `npm run dev --workspace=apps/backend`, choose **Local (:4477)**; the dev
default key `fangs-torches-admin-secret` works only when not hosted.)
