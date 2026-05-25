# Security Policy

## Scope

This repository contains a skill definition and helper scripts for local Grok account workflows.

## Secret handling guarantees

- Never print or log `AUTH_TOKEN`, `CT0`, or `XAI_API_KEY`
- Never commit secrets to this repository
- Never write secrets to generated artifacts
- Always validate credentials through command success/failure, not by outputting values

## Threat model

1. **Accidental token disclosure**
   - Mitigation: scripts only report `set/missing`; no token echo.
2. **Unsafe fallback from cookie mode to API mode**
   - Mitigation: explicit opt-in requirement for API mode.
3. **Session misuse**
   - Mitigation: mandatory `bird whoami` preflight before execution.
4. **State-changing actions without consent**
   - Mitigation: draft -> confirm -> execute workflow.

## Incident response

If credentials are exposed:
1. Rotate X/Twitter cookies (logout/login)
2. Replace `AUTH_TOKEN` and `CT0` in local secret stores
3. Rotate `XAI_API_KEY` if used
4. Review shell history and logs for leakage

## Reporting

Open a private security report via GitHub Security Advisories if enabled, or contact repository maintainers directly.
