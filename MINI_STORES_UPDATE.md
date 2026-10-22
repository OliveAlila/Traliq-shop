# Traliq seller mini-stores

## Included
- Each approved seller's existing `vendor_stores.slug` becomes a public storefront route at `/store/<slug>` on the same Traliq domain.
- Public mini-store page uses Traliq styling, shows `<Store Name> Store`, store description, products, and links customers back to Traliq.
- Store pages load only approved stores and active, non-archived products through the existing `/api/marketplace/stores/:slug` endpoint. Seller products remain in the main catalogue.
- Seller dashboard displays the complete shareable mini-store link and a Copy Store Link action.
- Product form includes editable placeholder photo choices alongside existing device upload and HTTPS image URL options.
- Existing test account `seller@gmail.com`, if present in the database with a store, is assigned the brand `Seller-Studio` and slug `seller-studio` at backend startup. Its approval status is preserved; this does not bypass admin approval.

## Important deployment notes
- Deploy both the updated client and server. The startup SQL update only takes effect when the updated backend starts against the production database.
- `seller@gmail.com` must already be a vendor with a `vendor_stores` record and status `approved` to make the public page available. The update deliberately does not create or approve a seller account.
- Expected URL after deployment: `https://<your-traliq-domain>/store/seller-studio`.
- Client production build was not verified in this environment because Vite was unavailable after dependency installation timed out. Run `npm install --prefix client` and `npm run build --prefix client` before deploying.
