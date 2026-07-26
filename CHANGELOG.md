# Changelog

Versioning for this fork tracks the upstream version it's based on, plus a
`+sod.N` build tag for this fork's own patch revisions (e.g. `4.0.1+sod.1`
is upstream 4.0.1, first SoD-compat patch on top of it).

## 4.0.1+sod.2

- Fixed `LEARNED_SPELL_IN_TAB` -> `LEARNED_SPELL_IN_SKILL_LINE`, the event's
  new name as of patch 1.15.9. The old name no longer exists on the client,
  so `RegisterEvent` threw and (depending on Lua's hash iteration order)
  could abort the rest of event registration before `ADDON_LOADED` itself
  got registered — the actual cause of the "attempt to index global
  'AutoBiographer_Settings' (a nil value)" error on login.
- Hardened event registration: each `RegisterEvent` call is now wrapped in
  its own `pcall`, so a single renamed/removed client event in the future
  can't cascade into blocking every event registered after it.

## 4.0.1+sod.1

- Forked from [AaronV-T/AutoBiographer](https://github.com/AaronV-T/AutoBiographer) (upstream by Tollski).
- Bumped `AutoBiographer_Vanilla.toc` Interface to 11509 for Season of Discovery / Classic Era patch 1.15.9.
- Added CurseForge/GitHub Actions release automation (`.pkgmeta`, `X-Curse-Project-ID`, packager workflow).
