# Buy-Box for Cursor

Save your buying criteria for homes, cars or anything else, so your AI assistant checks your budget, must-haves and dealbreakers before it searches or ranks listings.

This plugin connects Cursor to the hosted Buy-Box MCP server at `https://buybox.agentconsult.ai/mcp`. It contains configuration only. The server is run by Agentic Consulting LLC.

## What it does

Tell your AI assistant your budget, must-haves and dealbreakers once, and it can check searches and listings against them every time. Buy-Box saves those rules as a buy box for each category, such as homes or cars: budget, must-haves, nice-to-haves, dealbreakers, preferred brands or models, and any other fields you want.

- Save and update a buy box by category. Add or remove one item from a list without retyping the whole box.
- Load your criteria before a search, so the assistant filters to your rules.
- Score and rank up to 100 listings at a time against a saved box. Listings that break a numeric limit or mention a dealbreaker go to the end, labeled with the rule they broke. Anything a listing doesn't state is marked unknown, not counted as a pass.
- Export a box as Markdown you can save or share.
- List your categories and delete a box you no longer need.

The assistant is told to show you loaded criteria and ranked results and ask before acting on them.

Buy-Box is for your own purchase criteria. It is not an Amazon seller tool and is not related to Amazon Buy Box tracking services.

## Tools

| Tool | What it does | Type |
|---|---|---|
| `get_buy_box` | Retrieve the saved buy-box criteria for a category (homes, cars, or any freeform name). | Read-only |
| `set_buy_box` | Create or update the buy box for a category. Any field names are allowed. | Write |
| `score_candidates` | Check a list of listings against a saved buy box and rank them. | Read-only |
| `export_buy_box` | Return a buy box as readable Markdown the user can read or save. | Read-only |
| `list_categories` | List all categories that have a buy box defined. | Read-only |
| `delete_buy_box` | Remove the buy box for a category. | Write |

The plugin also includes a `use-buy-box` skill that tells the agent when to load, save and score criteria.

## Install

From the Cursor Marketplace: search for Buy-Box and install it.

Manual setup without the plugin: add this to `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "buy-box": {
      "url": "https://buybox.agentconsult.ai/mcp"
    }
  }
}
```

No API key or other configuration is needed.

## Sign in

Buy-Box uses OAuth, so there is no key to paste. After you install the plugin, Cursor shows that the Buy-Box server needs a login. Click it, and a browser window opens. Sign in with Google. If sign-in fails, remove and re-add the server, then try again. Your buy boxes are private to your account, and no other account can see them.

You can view your boxes, read-only, at https://buybox.agentconsult.ai after signing in. Ask the assistant to change or delete a box at any time.

Don't store health details, account numbers or passwords in a buy box.

## Example prompts

- Save a buy box for cars: budget about $20k, at least 7 seats, under 75,000 miles.
- Add "third-row seating" to the must-haves in my cars box.
- Here are 5 listings. Score them against my cars box.
- Show me my homes buy box as text.
- What buy box categories do I have?
- Delete my homes buy box.

## Pricing

Buy-Box is free during early access. See the Terms of Service for details.

## Privacy, terms and support

- Privacy Policy: https://buybox.agentconsult.ai/privacy
- Terms of Service: https://buybox.agentconsult.ai/terms
- Support: https://buybox.agentconsult.ai/support or tyler@agentconsult.ai

## License

The plugin files in this repository are MIT licensed. See [LICENSE](../../LICENSE). The hosted Buy-Box service is covered by its Terms of Service.
