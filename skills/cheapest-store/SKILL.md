---
name: cheapest-store
description: Find the cheapest supermarket for a list of groceries, or compare one product's price across stores. Use when the user asks where to shop, which store is cheaper, or how much something costs at each store.
---

Use this skill when the user wants to know where a shop, or one product, is
cheapest.

## A list of items → `compare_basket`

1. Collect the items. Each item is free text ("plain flour 1kg"), a retailer
   product URL, or a barcode. Keep the user's sizes and brands; set `qty` only
   when they give a count. If the list is empty or unclear, ask for it.
2. Call `compare_basket` once with the whole list (up to 100 items). Leave
   `match_mode` at its default unless the user asks: `exact` for the same
   product and size, `substitutes` when they're happy with a cheaper brand.
3. The card shows the stores, totals and items. In the reply, give the verdict
   in one or two sentences instead of repeating the table:
   - If `verdict.cheapest` is set, name that store and the saving the tool
     returned.
   - If it is missing, do not name a cheapest store. Say why, from
     `verdict.cheapest_withheld`: `coverage` means no store stocks enough of
     the list (name `verdict.most_complete`); `zone` means some prices are
     from another price zone.
   - Mention the store plan's split ("buy these there, those here") when it
     uses more than one store, and any items no store priced.
4. Mention stale prices only when `stale_line_count` is above zero.

## One product → `search_product`

1. Call `search_product` with the product as the user named it. Use `limit`,
   `max_price` or `sort` only when they ask for more results, a budget or an
   order.
2. Summarise the verdict headline. Offers are already ordered best value
   first; don't re-rank them.

## A store by name → `list_stores`

If the user asks about a specific store ("is it cheaper at X?") and X is not
in the comparison result, call `list_stores`. If X is not listed, say
OpenOrder doesn't cover it and give the comparison for the stores it does.

## Don't

- Don't say or imply a store is covered unless `list_stores` or a comparison
  result names it.

- Don't compute, round or re-rank prices, totals or savings yourself.
- Don't compare stores across countries.
- Don't claim a price is current if the tool marked it older.
