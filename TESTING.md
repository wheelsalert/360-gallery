# 360° Media Suite — Test Checklist

This checklist is run before every push to GitHub.
Check off each item manually in the browser. Add new scenarios whenever a bug is found or a feature is added.

**Browsers to test:**
- Chrome (primary — full feature support)
- Safari (secondary — FSA limitations apply)
- Mobile Safari on iPhone (tertiary — touch, gyroscope)

Mark each with ✅ pass / ❌ fail / ⚠️ known limitation / — not applicable.

---

## Pre-test setup

Before running any tests:
- [ ] Clear browser cache and localStorage for the test origin
- [ ] Use fresh 360° test files (at least 1 photo, 1 video)
- [ ] Open browser DevTools console — watch for errors during each test
- [ ] Note which browser and OS version you are testing on

---

## 1. Landing page (`index.html`)

| # | Test | Chrome | Safari |
|---|---|---|---|
| 1.1 | Page loads without console errors | | |
| 1.2 | All three app cards visible (Library, Gallery, Viewer) | | |
| 1.3 | Clicking Library card opens 360-library.html | | |
| 1.4 | Clicking Gallery card opens 360-gallery.html | | |
| 1.5 | Clicking Viewer card opens 360-viewer.html | | |
| 1.6 | Page renders correctly on mobile screen width | | |

---

## 2. 360° Viewer (`360-viewer.html`)

### 2.1 File loading
| # | Test | Chrome | Safari |
|---|---|---|---|
| 2.1.1 | Page loads — splash screen shown, no console errors | | |
| 2.1.2 | Open a photo via file picker — loads in viewer | | |
| 2.1.3 | Open a video via file picker — loads in viewer | | |
| 2.1.4 | Open a photo via drag and drop | | |
| 2.1.5 | Open a video via drag and drop | | |
| 2.1.6 | Open a second photo after first — replaces correctly | | |
| 2.1.7 | Open a video after a photo — replaces correctly | | |
| 2.1.8 | Open a photo after a video — replaces correctly | | |
| 2.1.9 | Unsupported file type shows error panel | | |

### 2.2 Photo viewer controls
| # | Test | Chrome | Safari |
|---|---|---|---|
| 2.2.1 | Can pan by dragging mouse/finger | | |
| 2.2.2 | Can zoom with scroll wheel / pinch | | |
| 2.2.3 | Autorotate button toggles rotation on/off | | |
| 2.2.4 | Gyroscope button visible in navbar | | |
| 2.2.5 | Fullscreen button works | | |

### 2.3 Video viewer controls
| # | Test | Chrome | Safari |
|---|---|---|---|
| 2.3.1 | Video plays automatically on load | | |
| 2.3.2 | videoPlay button visible — play/pause works | | |
| 2.3.3 | videoVolume button visible — mute/unmute works | | |
| 2.3.4 | videoTime display visible and updates | | |
| 2.3.5 | Gyroscope button visible in navbar | | |
| 2.3.6 | Can pan while video is playing | | |
| 2.3.7 | Fullscreen button works | | |

### 2.4 Error handling
| # | Test | Chrome | Safari |
|---|---|---|---|
| 2.4.1 | Error panel shows real message on failure | | |
| 2.4.2 | Error panel can be dismissed | | |

---

## 3. 360° Gallery (`360-gallery.html`)

### 3.1 Import
| # | Test | Chrome | Safari |
|---|---|---|---|
| 3.1.1 | Page loads — drop zone shown | | |
| 3.1.2 | Import single photo via Add media button | | |
| 3.1.3 | Import single video via Add media button | | |
| 3.1.4 | Import multiple files at once | | |
| 3.1.5 | Import files via drag and drop | | |
| 3.1.6 | Importing same file twice — no duplicate card | | |
| 3.1.7 | Importing a second batch adds to existing gallery | | |

### 3.2 Thumbnails
| # | Test | Chrome | Safari |
|---|---|---|---|
| 3.2.1 | Photo thumbnail generates and shows (not black) | | |
| 3.2.2 | Video thumbnail generates and shows (not black) | | |
| 3.2.3 | Spinner shows while thumbnail generates | | |
| 3.2.4 | Fallback icon shows if thumbnail fails | | |

### 3.3 Filter and sort
| # | Test | Chrome | Safari |
|---|---|---|---|
| 3.3.1 | Filter: All — shows all items | | |
| 3.3.2 | Filter: Photos — shows only photos | | |
| 3.3.3 | Filter: Videos — shows only videos | | |
| 3.3.4 | Filter with no matching items — empty state shown | | |
| 3.3.5 | Sort: Name A–Z | | |
| 3.3.6 | Sort: Name Z–A | | |
| 3.3.7 | Sort: Newest first | | |
| 3.3.8 | Sort: Oldest first | | |
| 3.3.9 | Sort: Type | | |
| 3.3.10 | Item count updates correctly with filter | | |

### 3.4 Viewer (from gallery)
| # | Test | Chrome | Safari |
|---|---|---|---|
| 3.4.1 | Click photo card — opens fullscreen viewer | | |
| 3.4.2 | Click video card — opens fullscreen viewer with sound | | |
| 3.4.3 | Prev / next buttons navigate between items | | |
| 3.4.4 | Prev disabled on first item | | |
| 3.4.5 | Next disabled on last item | | |
| 3.4.6 | Keyboard ← → navigates | | |
| 3.4.7 | Keyboard Esc closes viewer | | |
| 3.4.8 | Swipe left/right navigates on mobile | | |
| 3.4.9 | Close button returns to gallery | | |
| 3.4.10 | Gyroscope button visible for both photo and video | | |
| 3.4.11 | videoVolume button visible for video | | |

---

## 4. 360° Library (`360-library.html`)

### 4.1 Import
| # | Test | Chrome | Safari |
|---|---|---|---|
| 4.1.1 | Page loads — empty state shown | | |
| 4.1.2 | Import folder via Add folder button — album created | | |
| 4.1.3 | Import folder via drag and drop — album created | | |
| 4.1.4 | Album name matches folder name | | |
| 4.1.5 | Import second folder — second album created | | |
| 4.1.6 | Import same folder twice — no duplicate album | | |
| 4.1.7 | Unsorted files (no folder) go to Unsorted album | | |

### 4.2 Albums view
| # | Test | Chrome | Safari |
|---|---|---|---|
| 4.2.1 | Albums grid shows after import | | |
| 4.2.2 | Album card shows folder name | | |
| 4.2.3 | Album card shows item count | | |
| 4.2.4 | Album cover thumbnail generates correctly | | |
| 4.2.5 | All media button shows total item count | | |
| 4.2.6 | Click album card — opens album contents | | |
| 4.2.7 | Breadcrumb shows Library › Album name | | |
| 4.2.8 | Breadcrumb Library link returns to albums grid | | |

### 4.3 All media view
| # | Test | Chrome | Safari |
|---|---|---|---|
| 4.3.1 | All media button opens flat view of all items | | |
| 4.3.2 | Each card shows album name badge | | |
| 4.3.3 | Breadcrumb shows Library › All media | | |
| 4.3.4 | Filter and sort work in All media view | | |

### 4.4 Thumbnails
| # | Test | Chrome | Safari |
|---|---|---|---|
| 4.4.1 | Photo thumbnail generates (not black) | | |
| 4.4.2 | Video thumbnail generates (not black) | | |
| 4.4.3 | Thumbnails persist on page refresh (Chrome) | | |
| 4.4.4 | Thumbnails persist on page refresh (Safari) | | |

### 4.5 Persistence
| # | Test | Chrome | Safari |
|---|---|---|---|
| 4.5.1 | Refresh page — albums still appear | | |
| 4.5.2 | Refresh page — thumbnails still show | | |
| 4.5.3 | Chrome: refresh page — files still playable (FSA) | | |
| 4.5.4 | Safari: refresh page — "File not loaded" expected ⚠️ | | |
| 4.5.5 | Safari: re-import folder — files now playable | | |
| 4.5.6 | Safari: re-import does not create duplicate items | | |

### 4.6 Viewer (from library)
| # | Test | Chrome | Safari |
|---|---|---|---|
| 4.6.1 | Click photo — opens fullscreen viewer | | |
| 4.6.2 | Click video — opens with sound controls | | |
| 4.6.3 | Viewer title shows filename | | |
| 4.6.4 | Viewer subtitle shows album name | | |
| 4.6.5 | Prev / next navigates within current view | | |
| 4.6.6 | Keyboard ← → navigates | | |
| 4.6.7 | Keyboard Esc closes viewer | | |
| 4.6.8 | Swipe left/right on mobile | | |
| 4.6.9 | Gyroscope button visible | | |
| 4.6.10 | videoVolume button visible for video | | |
| 4.6.11 | "File not loaded" message shown when file is null | | |

### 4.7 Filter and sort (inside album)
| # | Test | Chrome | Safari |
|---|---|---|---|
| 4.7.1 | Filter: All / Photos / Videos work | | |
| 4.7.2 | Sort: Name A–Z / Z–A / Type work | | |
| 4.7.3 | Item count updates with filter | | |

---

## 5. Cross-cutting concerns

### 5.1 Mobile (iPhone Safari)
| # | Test | Result |
|---|---|---|
| 5.1.1 | All three apps load via GitHub Pages URL | |
| 5.1.2 | File picker works (no drag and drop expected) | |
| 5.1.3 | Gyroscope button prompts for permission on first tap | |
| 5.1.4 | Gyroscope navigation works after permission granted | |
| 5.1.5 | Pinch to zoom works in viewer | |
| 5.1.6 | Swipe navigation works in gallery and library viewer | |

### 5.2 Console errors
| # | Test | Chrome | Safari |
|---|---|---|---|
| 5.2.1 | No errors on page load | | |
| 5.2.2 | No errors after importing files | | |
| 5.2.3 | No errors after opening and closing viewer | | |
| 5.2.4 | No errors after navigating prev/next multiple times | | |
| 5.2.5 | No [object Event] module load errors | | |

### 5.3 GitHub Pages
| # | Test | Result |
|---|---|---|
| 5.3.1 | index.html loads at wheelsalert.github.io/360-gallery/ | |
| 5.3.2 | All three app links work from landing page | |
| 5.3.3 | No CDN errors in Network tab | |
| 5.3.4 | Apps work on mobile via GitHub Pages URL | |

---

## 6. Known limitations (do not file as bugs)

| Item | Affected | Notes |
|---|---|---|
| File System Access API | Safari, Firefox | Files require re-import each session |
| Drag and drop folders | Mobile Safari | Not supported by iOS — use file picker |
| Gyroscope permission | iOS Safari | Required once per domain — native prompt |
| Autoplay with sound | All browsers | Browsers block — video starts muted, user unmutes |
| [object Event] errors | Claude.ai sandbox | CDN blocked by sandbox CSP — works in real browser |

---

## 7. Regression log

Record bugs found during testing here so we don't re-introduce them.

| Date | Version | Bug | Fix |
|---|---|---|---|
| 2025-06-25 | viewer v1.0.0 | DataCloneError on photo load | Pre-populate PSV Cache before Viewer init |
| 2025-06-25 | viewer v1.0.0 | Blob URL safety check on video | Use DOM-attached video element without crossOrigin |
| 2025-06-25 | gallery/viewer v1.0.1 | autorotate button unknown | AutorotatePlugin not imported — added to plugins array |
| 2025-06-25 | gallery/viewer v1.0.1 | autoplay/muted unknown options | Options belong on VideoPlugin not adapter |
| 2025-06-25 | gallery/viewer v1.0.2 | Volume button not showing | Wrong navbar ID — caption → videoPlay/videoVolume/videoTime |
| 2025-06-25 | gallery v1.0.1 | Black video thumbnails | seeked fires before frame decoded — wait for loadeddata |
| 2025-06-25 | gallery v1.0.1 | No sound in video | hiddenVideo.muted=true persists — set false before PSV init |
| 2025-06-25 | viewer/gallery v1.0.2 | [object Event] on load | Three.js version wrong (0.167) and wrong filename (.min) |
| 2025-06-26 | library v1.0.2 | Re-import on Safari no effect | createAlbum skipped existing items — now updates file ref |

