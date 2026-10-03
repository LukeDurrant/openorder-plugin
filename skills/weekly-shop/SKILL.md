---
name: weekly-shop
description: Plan the week's meals and turn the plan into a priced shopping list and per-store cart links. Use when the user asks about their meal plan, wants dinner ideas for the week, or wants their shopping in a supermarket cart.
---

Use this skill for the weekly cycle: plan meals, price the list, fill carts.

## Plan

- `get_meal_plan` shows what is planned for a week (Monday `week_start`,
  defaulting to this week).
- `suggest_meals` ranks recipes cheapest-this-week first; `get_weekly_menu`
  is the specials-led menu; `list_recipes` is the user's library.
- `add_to_plan` adds a recipe to a day (0 = Monday). Only add what the user
  chose or clearly asked for, then confirm the day and meal.

## Price

- `get_shopping_list` prices the plan. Order sheets split the shop so each
  item is on exactly one store's sheet. With `retailer` set, it is that one
  store's whole-basket sheet instead — an alternative to the split, never in
  addition to it.

## Fill carts → `get_cart_handoff`

1. Call `get_cart_handoff`. It can take up to ~40 seconds for a large plan.
2. The card shows one section per store with a button per cart link. In the
   reply, tell the user:
   - to sign in to each store in their own browser first;
   - links marked as adding to the cart must be opened **once** — opening one
     twice doubles the items;
   - items under "add by hand" have a search link each;
   - items marked "you have it" should not be bought;
   - for a store using the browser extension, the OpenOrder extension fills
     the whole sheet on the store's own page.
3. Follow each sheet's `instructions` exactly. Stop at the cart: the user
   reviews it and pays themselves.

## Never

- Never ask for, type or store a supermarket password, verification code or
  payment details.
- Never open a link for the user, reproduce an extension's request, or go
  past the cart review page.
- Never buy an item the sheet says the user already has.
