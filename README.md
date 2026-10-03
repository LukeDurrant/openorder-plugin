# OpenOrder

OpenOrder answers one question: **where should I do this shop?** Give your
assistant a grocery list and it compares the whole basket across the major
supermarkets in your country, using fresh prices from OpenOrder's own
catalogue, and tells you which store is cheapest and what to buy where.

For shoppers in Australia, the United Kingdom, New Zealand and the United
States.

## What you can ask

- "Which supermarket is cheapest for milk, bread, eggs, chicken and rice?"
- "How much is a 2kg bag of rice at each store?"
- "Which supermarkets do you compare in my country?"
- "Suggest a cheap dinner for Wednesday and add it to my plan."
- "Turn this week's meal plan into cart links for each store."

## Install

**Claude Code**

```bash
claude plugin marketplace add LukeDurrant/openorder-plugin
```

```bash
claude plugin install openorder@openorder
```

Then type `/mcp` in a session, choose the OpenOrder server and sign in.

**Claude (web, desktop, mobile) and ChatGPT:** add OpenOrder from the
plugin directory once it is listed. Until then, add
`https://www.openorder.bot/api/mcp` as a custom connector (Claude) or under
Plugins in Developer mode (ChatGPT). Steps for each app are at
[www.openorder.bot/ai](https://www.openorder.bot/ai).

## What is in the plugin

- **A connector** to OpenOrder's hosted MCP server at
  `https://www.openorder.bot/api/mcp`. It provides the tools: basket
  comparison, product price lookup, the list of stores covered, your recipes
  and meal plan, a priced shopping list, and each store's own cart links.
  Price comparisons and cart links are shown as cards where the app supports
  them.
- **Three skills** that tell the assistant how to use those tools:
  `get-started`, `cheapest-store` and `weekly-shop`.

The plugin runs nothing on your computer. It contains no scripts, hooks or
executables.

## Signing in

The first time a tool runs you are sent to OpenOrder's own consent page to
sign in and approve the connection. Create a free account at
[www.openorder.bot](https://www.openorder.bot) first. Your assistant never
sees your OpenOrder password, and you can disconnect at any time in your
assistant's connector settings.

Prices are compared for the country of the postcode saved in your OpenOrder
settings. If the assistant says it can't tell which country you shop in, save
your postcode there and ask again.

## What it sends and receives

Your assistant sends OpenOrder the items, products or week you ask about.
OpenOrder returns prices, store comparisons, your recipes, meal plans and
shopping lists, and cart links. It does not return your email address,
password or payment details. See the
[privacy policy](https://www.openorder.bot/privacy).

## What it will not do

- It never asks for, or handles, your supermarket login, verification codes
  or payment details.
- It never checks out. Cart links open in your own browser, where you review
  the cart and pay yourself.
- It only compares the stores it lists. Ask which stores are covered.

## Licence

The files in this repository are released under the [MIT licence](LICENSE).
The OpenOrder service they connect to has its own
[terms](https://www.openorder.bot/terms).

## Help

[Support](https://www.openorder.bot/support) ·
[Terms](https://www.openorder.bot/terms) ·
[How to connect an assistant](https://www.openorder.bot/ai)
