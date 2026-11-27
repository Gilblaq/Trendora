# Groove Link Jumia + Temu catalogue

## Current storefront behaviour
- The customer catalogue is at `marketplace.html`.
- Product data is loaded from `products.json` in the next catalogue-data integration step; the current static MVP deliberately has no invented Jumia or Temu listings.
- The default selling price is calculated as supplier cost in GHS × 1.45.
- Delivery and additional charges are not included in the displayed product price and must be confirmed before payment.
- Orders are requests sent to Groove Link on WhatsApp. This static website does not collect or store payments or customer orders.

## Product record format
Add records to the `products` array in `products.json` only after checking the actual source listing and Ghana fulfilment details.

```json
{
  "id": "unique-product-id",
  "name": "Exact product title",
  "description": "Accurate short description",
  "category": "Gadgets",
  "source": "Jumia",
  "sourceUrl": "https://www.jumia.com.gh/...",
  "imageUrl": "https://...",
  "supplierPriceGhs": 100,
  "available": true
}
```

Allowed source values: `Jumia` or `Temu`. Allowed categories: Fashion, Gadgets, Accessories, Jewellery, Home, Other.

For Temu listings priced in another currency, convert the actual item price to GHS using a current, documented rate before entering `supplierPriceGhs`. Do not treat an advertised item price as the delivered-to-Ghana cost. Check shipping, customs/import charges, seller restrictions, stock and return terms separately.

## Important limitation
This is a static GitHub Pages / Cloudflare Pages storefront. It does not scrape Jumia or Temu, sync live inventory, or accept online payments. Automated marketplace feeds/API access and a secure server-side order/payment backend need separate approved integrations and Cloudflare configuration. Never put marketplace API keys, payment secrets or admin passwords in browser JavaScript.

## Marketplace access and content rights

- Do not scrape marketplace pages or copy/re-host product photos, descriptions, or other listing material unless the marketplace or rights holder has authorized that use. Jumia's Ghana buyer terms allow forwarding product links but restrict republishing or commercially exploiting marketplace material except where expressly permitted: https://pay.jumia.com.gh/cms/customers-terms-and-conditions.html
- Jumia Ghana also offers its official JForce sales-consultant programme. It provides a unique link to products from Jumia's full catalogue and Jumia handles fulfilment; this is a commission/referral model, not the custom reseller checkout described above: https://www.jumia.com.gh/mlp-jforce/
- Temu's official affiliate programme provides approved affiliate links/codes and pays qualifying commissions or referral rewards subject to the local programme terms. This is also different from purchasing products as a reseller: https://www.temu.com/affiliate_question.html
- Before any automated import, confirm that the specific programme grants catalogue/feed access and image/content usage rights for Groove Link. Do not place API keys or access tokens in this static site.
