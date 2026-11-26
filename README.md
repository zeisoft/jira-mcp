<div align="center">

<img src="assets/cover.png" alt="Jira through HeyMetra's MCP server" width="100%">

# Jira &times; HeyMetra

**Issues, sprints and who is on what, asked in plain words.**

Connect Jira once, then ask about it in plain language.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.heymetra%2Fheymetra-1f6feb)](https://registry.modelcontextprotocol.io/v0/servers/com.heymetra%2Fheymetra/versions)
[![Transport](https://img.shields.io/badge/transport-Streamable_HTTP-444)](https://modelcontextprotocol.io/)
[![Auth](https://img.shields.io/badge/auth-OAuth_2.1-444)](https://heymetra.com/security/)
[![Connector page](https://img.shields.io/badge/heymetra.com-jira-1f6feb)](https://heymetra.com/connectors/jira/)

```
https://mcp.heymetra.com/mcp
```

</div>

---

## Ask it things like

> Which issues are still open in this sprint?

> What is assigned to me and not done?

> Which bugs were reported this week?

> What did people say on this issue?

No dashboard, no export, no query language. You ask in the assistant you already use and the answer comes back with the account it came from.

## Connect Jira

**1. Press Connect and sign in to Atlassian**

You are sent to Atlassian's own screen. Nothing is typed into HeyMetra: the grant is made there and Atlassian tells us what it covers.

**2. Pick the site this connection is for**

If your account has more than one, such as acme.atlassian.net and acme-dev.atlassian.net, Atlassian asks which. The one you pick is the one this connection covers, and the others stay out of reach until you connect them too.

> Connect the site your team actually works in first. A second connection costs another minute and can be added whenever it is wanted.

**3. Name the connection after the site**

'Acme' rather than 'Jira'. That name is what you say when you ask a question about it, and it is what tells two connections apart.

The same steps are on the docs page: [Jira setup guide](https://heymetra.com/docs/jira/).

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

### One command

```bash
npx add-mcp https://mcp.heymetra.com/mcp
```

[`add-mcp`](https://www.npmjs.com/package/add-mcp) is a third-party installer that writes the configuration for Claude Code, Codex, Cursor, Antigravity, VS Code and seventeen other agents. It infers the name from the address, so the server lands as `heymetra`. Run against this endpoint before it was written here.

### Or by hand

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans, an owner adds the connector for the whole organization under Organization settings → Connectors, and each member then connects to it._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — chatgpt.com/plugins → + → Add custom MCP server</summary>

Paste the address above into chatgpt.com/plugins → + → Add custom MCP server.

_Add it on chatgpt.com in a browser, because the mobile app cannot add one. Every ChatGPT plan can, Free included. In a Business, Enterprise or Edu workspace, an admin or owner decides whether members can add custom MCP servers. ChatGPT needs the full address, including /mcp at the end._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_On Grok Business and Enterprise, a team admin has to provision the connector in xAI's cloud console before members can use it._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Plugins → Add custom → Connector → Add MCP connector → Remote</summary>

Paste the address above into Plugins → Add custom → Connector → Add MCP connector → Remote.

_In an organization, members can add a custom connector only after an admin turns on Allow members to add custom connectors, which is off by default._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_You can also add the server to a .mcp.json file at the project root. Run /mcp in a session to sign in and to check that it connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Codex reads the server from an [mcp_servers.<name>] section in config.toml, and you sign in with codex mcp login <name>._

Full walkthrough: [heymetra.com/mcp/codex/](https://heymetra.com/mcp/codex/)
</details>

<details>
<summary><b>Cursor</b> — ~/.cursor/mcp.json, or .cursor/mcp.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "url": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Cursor signs in to HeyMetra without a client ID or secret, so the server entry needs no auth block._

Full walkthrough: [heymetra.com/mcp/cursor/](https://heymetra.com/mcp/cursor/)
</details>

<details>
<summary><b>Antigravity</b> — ~/.gemini/config/mcp_config.json, or .agents/mcp_config.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "serverUrl": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Antigravity's documented key for the address is serverUrl, though it also accepts url._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## What it may and may not touch

Jira is a read-only source. HeyMetra reads it to answer your questions and never changes anything in it.

Permissions are switched on per connection, and one you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Full account access** | Lets your assistant read anything in this account to answer your questions. The figures are the provider's own, not ones HeyMetra has checked. It cannot change anything in this account — Read-only. This connection asks Atlassian for no permission to change anything, so no card can propose one; The grant covers the one site picked when it was made. Another site on the same account is another connection. | No, read only |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Ask anything about this account and get the answer from its live data. Reads only, and the figures are the provider's own rather than ones HeyMetra has checked.
</details>

## When something goes wrong

<details>
<summary>The site you wanted is not in the list Atlassian showed.</summary>

**Why:** The grant is made by the person signing in, and it covers the sites that person can open. A site nobody added you to is not one of them.

**Fix:** Ask a Jira admin to add you to that site, then connect again so the list is read afresh.

</details>

<details>
<summary>Issues answer, but the assignee comes back as an id.</summary>

**Why:** Naming a person is a separate permission from reading the work itself, and this connection was made before it was asked for.

**Fix:** Reconnect. The current grant asks for both, and a connection made before one of them was added keeps the narrower one until it is replaced.

</details>

<details>
<summary>You want the assistant to create or move issues.</summary>

**Why:** This connector asks only to read. The write permission is not requested, so no card can propose a change here.

**Fix:** Tell us. It is a decision about personal data rather than a technical limit, and knowing somebody wants it is what would reopen it.

</details>

## What HeyMetra reads from Jira

Connecting sends you to Atlassian, where you pick the site this connection covers. The others on your account are not included, so a company with two sites makes two connections. Then ask your assistant about your work: issue searches, a project's issues, what is in a sprint, and what was said in an issue's comments. The answers are Jira's own rather than figures HeyMetra has checked.

**Read-only, and that is a decision rather than a limit.** Atlassian offers a write permission and this connector does not ask for it, because approving a change would store personal data about Atlassian users in HeyMetra. Reading keeps that from happening at all.

<details>
<summary>About Jira</summary>

Jira is where the work is written down: issues and their status, projects, sprints, who a thing is assigned to, and what was said in the comments. It answers "what is actually in flight" without anybody building a report for it.
</details>

## One connection, not seven

The reason to read Jira through HeyMetra rather than through a server that only knows Jira is everything else it can answer in the same breath:

**Ads** — [Google Ads](https://github.com/zeisoft/google-ads-mcp) · [Meta](https://github.com/zeisoft/meta-ads-mcp)

**Analytics** — [Google Analytics 4](https://github.com/zeisoft/google-analytics-4-mcp) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp) · [PostHog](https://github.com/zeisoft/posthog-mcp)

**Ecommerce** — [Trendyol](https://github.com/zeisoft/trendyol-mcp) · [n11](https://github.com/zeisoft/n11-mcp) · [Çiçeksepeti](https://github.com/zeisoft/ciceksepeti-mcp) · [Amazon Seller Central](https://github.com/zeisoft/amazon-seller-central-mcp) · [ikas](https://github.com/zeisoft/ikas-mcp) · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — [Stripe](https://github.com/zeisoft/stripe-mcp) · [Zoho CRM](https://github.com/zeisoft/zoho-crm-mcp) · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · [Zoho Marketing Automation](https://github.com/zeisoft/zoho-marketing-automation-mcp)

**Mobile** — [AppsFlyer](https://github.com/zeisoft/appsflyer-mcp) · [RevenueCat](https://github.com/zeisoft/revenuecat-mcp) · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Work** — **Jira**

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · [Telegram](https://github.com/zeisoft/telegram-mcp)

The full catalogue is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [Jira connector page](https://heymetra.com/connectors/jira/)
- [Jira setup guide](https://heymetra.com/docs/jira/)
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup for every assistant](https://heymetra.com/mcp/)
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/)
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>Built by <a href="https://zeisoft.com">Zeisoft</a>, who make HeyMetra. Not affiliated with Jira. This README is generated from HeyMetra's live connector catalogue and refreshed daily; corrections are welcome as issues.</sub>
