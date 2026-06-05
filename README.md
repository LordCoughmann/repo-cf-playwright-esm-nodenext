# Reproduction: @cloudflare/playwright types fail with moduleResolution: NodeNext

Extension-less imports in `@cloudflare/playwright`'s declaration files fail to resolve with `moduleResolution: NodeNext` or `Node16`.

## Steps to reproduce

```bash
pnpm install
pnpm tsc --noEmit
```

## Expected

No type errors. `Browser` type imports successfully.

## Actual

```
index.ts(1,15): error TS2614: Module '"@cloudflare/playwright"' has no exported member 'Browser'.
index.d.ts(2,30): error TS2834: Relative import paths need explicit file extensions in ECMAScript imports when '--moduleResolution' is 'node16' or 'nodenext'.
index.d.ts(3,55): error TS2834: Relative import paths need explicit file extensions...
index.d.ts(6,15): error TS2834: Relative import paths need explicit file extensions...
```

## Environment

- TypeScript 6.0
- Node.js 20+
- `@cloudflare/playwright@1.3.0`
- `moduleResolution: NodeNext`

## Related

- Draft PR: https://github.com/cloudflare/playwright/pull/194