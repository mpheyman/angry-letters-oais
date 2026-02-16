Perform a security + privacy + CSP review of the change. Be concrete.

## Checklist
- **Secrets**: no keys/tokens/passwords committed; no `.env*` in context; placeholders only.
- **PII**: no logging/storing/analytics of PII; emails/addresses protected.
- **AuthZ/AuthN**: admin vs creator separation preserved; token verification correct.
- **Rate limiting**: sensitive endpoints limited.
- **CSP**: no inline scripts/styles; scripts loaded via files; `defer` where appropriate.
- **Input validation/sanitization**: especially user text + AI prompts.
- **Prompt injection**: treat external/user content as untrusted; enforce output schema.

## Output format
### Findings
- ✅ …
- ⚠️ …
- ❌ …

### Recommended tests
- …

