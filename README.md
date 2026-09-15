# PayCryptoKit — connect crypto payments with your AI

Give your AI the integration Skill. It inspects your existing website, helps configure supported receiving addresses and server credentials, and verifies the payment flow. You keep your wallet private keys.

[Website](https://paycryptokit.com/) · [Current download manifest](https://paycryptokit.com/downloads/manifest.json) · [Integration Skill](skills/yourpay-integrate/SKILL.md)

## Start with your AI

Open your website project in Codex, Claude Code or another coding agent and give it this instruction:

> Read https://github.com/BarneyD66/paycryptokit-integration/blob/main/skills/yourpay-integrate/SKILL.md and follow its integration workflow. Use https://paycryptokit.com/downloads/manifest.json to locate the current CLI, SDK and MCP packages; verify SHA-256 checksums before installing. Inspect my project without requiring an account first. Preserve existing authentication, server-side prices and order fulfillment. Ask for the receiving addresses I want to enable; never ask for private keys or seed phrases. Report completed, failed and untested steps.

No dashboard is needed for the initial project check. Authenticated setup is still required for private merchant data and configuration. Current production APIs protect website/callback and receiving-address changes with browser-session authorization; do not assume a CLI credential bypasses that protection.

## What is in this repository

- A reviewed snapshot of the public integration Skill.
- SDK, CLI and MCP release tarballs already distributed on the website.
- A manifest containing the original public paths, SHA-256 checksums and file sizes.

The manifest's paths are relative to its sourceOrigin. Local copies are in releases/. The website manifest is the source for newer releases; do not mix a file from one release with another release's checksum. Internal package names remain @yourpay/sdk, @yourpay/cli and @yourpay/mcp. They are not advertised as published npm registry packages.

This is the public integration kit, not the hosted payment service source or an operator deployment repository. No production credentials, merchant data or infrastructure backup material are included.

## Integration boundaries

- Node.js 24 is the verified integration runtime.
- Next.js App Router has a starter adapter. Other frameworks require your AI to adapt the existing server code using the SDK.
- Only configured and accepted payment channels can be offered to customers. Providing an address does not activate an unaccepted network.
- The merchant pays a 0.2% service fee through prepaid service credit. Customers pay their transaction network fees; the platform does not advance customer gas.
- Fulfill an order only after verified payment evidence and authenticated, duplicate-safe webhook processing. A browser redirect does not prove payment.

## Release status

Early access: live payments are not enabled. Use the actual environment information from the API and checkout. Do not send real assets to a test environment or treat installation as mainnet acceptance.

MIT license applies to the distributed integration packages; see LICENSE.
