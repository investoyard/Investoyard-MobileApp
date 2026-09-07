# Investoyard Mobile

The Expo React Native app for [Investoyard](https://newipo.finwave.co) — India's IPO information and application platform.

## Layout

```
apps/mobile              — the Expo app (SDK 54)
packages/shared-types    — types, bid engine, stage rules, format helpers
packages/i18n            — en + hi translations
scripts/                 — install-time helpers
```

## Getting started

```bash
npm install --legacy-peer-deps
cd apps/mobile
$env:REACT_NATIVE_PACKAGER_HOSTNAME='<your host IP>'
$env:EXPO_OFFLINE='1'
npx expo start --clear
```

Note: after `npm install`, `scripts/link-expo-router.js` re-junctions the Expo packages. If Metro reports "Cannot find module babel-preset-expo", run it manually.

## Relationship to the internal repo

This repository is a **mobile-only subset** of the Investoyard internal monorepo (`Investoyard-WebApp`). It contains everything a mobile developer needs to build and run the app, but excludes the web front-end, backend API, and operator tooling.

`packages/shared-types` is the source of truth for types and business rules shared with the web app; a matching copy lives in the internal monorepo. Any change to shared types should be raised as a PR here (or coordinated with the operator) so the two copies stay in step.

## Design notes

The app is the **task surface** — speed, one clear CTA per stage. Vocabulary and status wording match the web surface exactly (see `packages/shared-types/src/format.ts` for the shared labels and status tones). Do not fork status wording or the semantic colour palette locally.

## Contributing

Open a PR against `main`. The operator reviews and merges.
