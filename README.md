# Pan Tech Africa backend

## Run it
1. Install Node 18 or newer.
2. `npm install`
3. Copy `.env.example` to `.env`, then fill in `PI_API_KEY`, `ALLOWED_ORIGINS` and `VALIDATION_KEY`.
4. `npm start`

## Connect the storefront
In `public/index.html`, set `API_BASE` in the CONFIG block to this server's public HTTPS address, for example `https://your-app.onrender.com`. If this server also serves the storefront (it does, from `public/`), `ALLOWED_ORIGINS` is the same address.

## Deploy
Any Node host works (Render, Railway, Fly.io, a VPS). Set the same variables from `.env` in the host's settings and use `npm start` as the start command.
Use a host with a persistent disk, or replace `orders.json` with a database, otherwise orders are lost on redeploy.

## Pi Developer Portal
- App URL: your deployed HTTPS address
- Keep `SANDBOX: true` in the storefront while testing, then set it to `false` for Mainnet.
- The portal's domain validation reads `https://yourdomain/validation-key.txt`.

## Keep prices in sync
`catalog.js` holds the real prices. If you change a price in `public/index.html`, change it here too, or payments for that product will be rejected on purpose.
