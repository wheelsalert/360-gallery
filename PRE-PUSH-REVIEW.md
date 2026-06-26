# Pre-Push Review Process

This review runs before every `git push`.
Both of us are responsible for it — I run the code review, you run the browser tests.

---

## Step 1 — I review the code (before you see it)

Before presenting any new or changed code, I explicitly check:

### API correctness
- [ ] All library method names verified against source (not assumed from memory)
- [ ] All plugin option names verified (e.g. VideoPlugin config vs adapter config)
- [ ] All navbar button IDs verified (videoPlay, videoVolume, videoTime — not caption)
- [ ] All CDN URLs verified — correct package, correct version, correct filename

### Browser compatibility
- [ ] Any Web API used — checked for Safari/Firefox support
- [ ] File System Access API — fallback in place for Safari/Firefox
- [ ] crossOrigin attribute — not set on blob URL video elements
- [ ] Drag and drop — folder drag handled separately from file drag
- [ ] DeviceOrientationEvent — permission prompt handled for iOS

### State management
- [ ] What happens on second run / second import? (re-import, re-open)
- [ ] What happens if the user clicks the same button twice?
- [ ] What happens if a file is null or missing?
- [ ] Is state fully reset between operations?
- [ ] Are blob URLs revoked when no longer needed?

### Error handling
- [ ] Every async operation has a try/catch or .catch()
- [ ] Every error surfaces a readable message to the user
- [ ] No silent failures (no empty catch blocks)
- [ ] Console errors logged with context

### Threading (Python apps)
- [ ] Background thread never touches UI directly
- [ ] All UI updates go through Queue or self.after()
- [ ] Thread state fully reset between runs
- [ ] App usable again after first run completes

---

## Step 2 — I flag uncertainties (in every response)

At the end of every code delivery I will include a section:

```
⚠️ Test these specifically:
- [specific scenario I am uncertain about]
- [browser-specific behaviour to verify]
- [edge case I couldn't fully reason about]
```

If I have no uncertainties I will write:
```
✅ Review passed — no known uncertainties for this change.
   Run checklist sections: [X.X, X.X]
```

This is mandatory — I never skip it.

---

## Step 3 — You run the browser tests

Using `TESTING.md`, run the sections relevant to what changed:

| Change type | Sections to run |
|---|---|
| Viewer change | 2, 5.2 |
| Gallery change | 3, 5.2 |
| Library change | 4, 5.2 |
| New feature across all | 2, 3, 4, 5 |
| CDN / importmap change | 5.2, 5.3 |
| Bug fix | The specific scenario that was broken + regression check |

**Minimum test run for any change:**
1. Open the file in Chrome — no console errors
2. Open the file in Safari — no console errors
3. Run the specific scenario that changed
4. Run one adjacent scenario (something nearby that could have broken)

---

## Step 4 — Version bump and archive

Before pushing, confirm:
- [ ] Version number bumped in file header comment
- [ ] Changelog entry added describing what changed and why
- [ ] Versioned copy saved to `versions/` folder
- [ ] `TESTING.md` updated if new scenarios were discovered
- [ ] Regression log updated if a bug was found and fixed

---

## Step 5 — Commit message format

```
[verb] [what] - [file] [version]

Examples:
Fix video thumbnail black frame - gallery v1.0.1
Add gyroscope navigation - all files v1.0.3
Fix Safari re-import file reference - library v1.0.2
Add 360-library initial release - v1.0.0
```

---

## What triggers a full test run vs a partial run

**Full test run (all sections):**
- Major version bump (x.0.0)
- Changes to shared code (PSV init, importmap, hidden video element)
- First time testing on a new browser or device
- After fixing a bug that could have affected multiple files

**Partial test run (affected sections only):**
- Patch version bump (x.x.1) — bug fix to one specific scenario
- Minor feature addition that doesn't touch existing functionality
- CSS/style only changes

---

## Current version status

| File | Version | Last tested | Chrome | Safari |
|---|---|---|---|---|
| index.html | — | 2025-06-25 | ✅ | ✅ |
| 360-viewer.html | v1.0.3 | 2025-06-25 | ✅ | ✅ |
| 360-gallery.html | v1.0.3 | 2025-06-25 | ✅ | ✅ |
| 360-library.html | v1.0.2 | 2025-06-26 | ✅ | ✅ |

