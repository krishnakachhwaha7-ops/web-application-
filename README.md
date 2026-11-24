# Commonplace Store

A dependency-free Node.js store API with a persisted JSON database. Requires Node.js 18+.

## Run

```sh
npm start
```

Open `http://localhost:3000` for API health. Open `http://localhost:3000` for the API-backed storefront. Catalog, authentication, checkout, and admin product/order actions call the REST API.

## Demo admin

`admin@commonplace.store` / `admin123`

## API

- `GET /api/products` — catalog
- `POST /api/auth/register` — create customer account; returns bearer token
- `POST /api/auth/login` — login; returns bearer token and role
- `GET /api/orders` — own orders; admin sees all
- `POST /api/orders` — place order using `{ "items": [{"productId":"p1","quantity":1}], "address":"..." }`
- `PATCH /api/orders/:id` — admin status update using `{ "status":"Shipped" }`
- `POST /api/products` — admin product creation
- `DELETE /api/products/:id` — admin product removal

Persistent records are stored in `data/store.json`, created on first start. This learning project uses a JSON file database; it does not currently use MySQL, PostgreSQL, or MongoDB. For production, replace demo password hashing and in-memory sessions with a vetted auth/session implementation and TLS.

