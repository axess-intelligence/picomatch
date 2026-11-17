# Axess security patch

This fork starts at upstream 4.0.7 (6bb40679c218cefba5d4e9662408c5fdf699a8bb). It extends the existing risky-extglob guard to parsed wildcard tokens inside repeated groups, including single branches and wildcard alternatives (CVE-2026-112366 / GHSA-fc5q-39xc-vjpf).

These unsafe patterns are matched literally by default, consistent with the existing safeguard. This intentionally changes previously accepted repeated-wildcard matches such as `+(*)c`, `*(a*|b)` and `*/*(W*, *)*`. Literal repetition, escaped/quoted stars, capture contexts and existing safe nested-star rewrites remain covered. The upstream trusted-pattern opt-out `maxExtglobRecursion: false` remains available and disables this protection.

Version 4.0.8+axess.1 identifies this patched fork, not an upstream release. Consumers must pin the exact Git commit. Replace the fork with a verified fixed upstream release when available.
