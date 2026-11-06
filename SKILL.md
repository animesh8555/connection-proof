---
name: "connection-proof"
description: "Use when establishing whether an integration works in the intended agent or when a connected status conflicts with missing tools or failed results. Diagnose whether an MCP integration is configured, authorized, exposes tools, and returns the expected result in the intended client."
---

# Connection Proof

Verify tool availability and a read-only result in the intended client.

Use this for missing connector tools, contradictory connection status, or a requested delivery test. A normal successful call does not need an extra diagnostic ceremony.

## When to apply this workflow

Use when establishing whether an integration works in the intended agent or when a connected status conflicts with missing tools or failed results. If the host makes this skill available, use it for matching work without waiting for a tag.

Before relying on the integration, report which stages passed and what remains unverified. If an expected result is missing, pause dependent work and identify the failed stage. Continue authorized work that does not depend on the unresolved result.

## Check the actual path

Identify the intended client, account, service, endpoint or documented connection method, and harmless operation the user wants to prove. Use the service's current official setup instructions. Do not assume a tool name from an old example.

Check these stages separately:

1. **Configured:** the intended client has the expected connection configuration.
2. **Authorized:** that client/account has the necessary current permission, not merely a browser login.
3. **Tools available:** the intended client actually exposes the required tools and their current argument contracts.
4. **Operation verified:** an explicitly selected authorized read-only call returned the expected identity and content.

For each stage, report verified, failed, or not checked, with the observed evidence. A tool returning success with the wrong document or publisher does not establish delivery. Browser access to a service does not establish MCP access from this chat.

If portal status and client behavior disagree, refresh the authoritative view that could be stale and inspect the actual tool list. Do not keep reconnecting blindly. Connecting a different agent may disconnect an existing one; surface that consequence before changing the connection.

Distinguish authentication from authorization: HTTP 401 or an expired credential is an authentication failure; HTTP 403 is an authorization failure. Neither proves the tool operation works. Report the exact failing layer.

## Safe diagnostics

Use already authorized credentials through the host's documented mechanism. Never collect tokens, cookies, or passwords for a report. Do not widen permissions or approve an OAuth grant without the required user action. Start with a harmless read and stop before a write merely to prove connectivity.

For Agensi, distinguish the live listing, OAuth connection, tools visible in the intended chat, and complete skill content retrieved with the expected publisher. The listing's presence alone does not prove the last step.

Read [the client playbooks](references/playbooks.md) for guided checks. Report the failing stage and the smallest next action.

## Boundaries

The available tools and authentication flow depend on the host. A generic probe cannot certify every client or force a connector to become available. Never label an untested adapter as supported.
