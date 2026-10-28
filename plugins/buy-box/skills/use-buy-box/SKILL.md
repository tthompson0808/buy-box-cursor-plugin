---
name: use-buy-box
description: Use when the user wants to save, update, load, export, list or delete their buying criteria (a buy box) for homes, cars or any other category, or wants listings checked and ranked against a saved buy box. Not for Amazon seller Buy Box questions.
---

Buy-Box stores the user's own buying criteria by category. Explicit user instructions take priority over this skill.

## Before a search or comparison

1. Call `get_buy_box` for the category before searching, filtering or ranking listings.
2. Show the user the loaded criteria and ask for confirmation before acting on them.
3. If no box exists, offer to create one with `set_buy_box`.

## Saving or changing a box

1. Call `get_buy_box` first and reuse the field names already in the box.
2. To add or remove one item from a list, use `add` or `remove` instead of resending the whole list.
3. If the result includes warnings about a field that looks like an existing one, tell the user and fix it with `remove_fields` if they agree.
4. Read back what was saved.
5. Do not store health details, account numbers or passwords. Decline if asked.

## Scoring listings

1. Call `score_candidates` with the listings as objects holding whatever fields you have (price, mileage, year, seats, a description).
2. Present the ranked results. Listings that break a numeric limit or mention a dealbreaker come last, labeled with the rule they broke.
3. Treat anything a listing does not state as unknown, not as a pass. Say which facts the user should check with the seller.
4. Ask before acting on the results.

## Other requests

- `export_buy_box` returns a box as readable text the user can save or share.
- `list_categories` shows which categories have a box.
- `delete_buy_box` removes a box. Confirm the category with the user before deleting.

Buy-Box cannot buy anything, contact sellers or make payments. If the user asks for that, say so and do not call a Buy-Box tool for it.
