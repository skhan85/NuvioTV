# Fork patches (Apple TV, on top of bobsupra/NuvioTVOS)

Patches are grouped **by file**, not by feature: every upstream file the fork edits lives in
exactly one patch, so an upstream change to a file causes at most one conflict, and the patches
apply in any order. `BASE` is the upstream commit they were made against. Fork-only code lives
in `Sources/Fork/*.swift`; the edits to upstream files are mostly small hooks into it.

| Patch | Area | Features in it |
|---|---|---|
| `0001-infuse-and-player` | Core/Player, UI/Player, PlayerViewModel | Infuse hand-off, MPV readahead and prefetch fixes, Dialogue Boost, playback diagnostics, "Are you still watching?" |
| `0002-home-library-and-browse` | NuvioTVApp (Home and app root), Home rows, posters, Library, Discover, repositories, most `Fork/` files | Release calendar and insights, collection See All and legacy source types, Billboard trailer, Top 10 and Trending rows (no Trending Now), kids-friendly Top 10, kids rating limit, Netflix Home ("Continue Watching for", genre line, play circle, red progress), card tags (TOP 10 / New Episode / Coming Soon, saved and fetched ahead), Coming Soon row (Remind Me via the hold menu), "What's new in your fork" note, hide cinema-only films, Play Something (shuffle) button, language tag (KOREAN, HINDI…) on non-English titles, language tags (`Fork/LanguagesFork.swift`), Style (`Fork/StyleFork.swift`), Speed Report timing marks and screen (`Fork/SpeedFork.swift`) |
| `0003-detail-page` | Details screen and view model | Netflix-style details page, Top 10 badge, kids filter on More Like This, Hindi / Multi-audio tags on sources and sources in the profile's audio language listed first |
| `0004-tmdb-and-built-in-key` | Core/TMDB, Fork/ForkSecrets | Built-in TMDB key everywhere, trending / kids popular, Coming Soon (streaming dates), certifications, card freshness and original language, studio logos |
| `0005-search` | UI/Search and search view models | Faster search (Cinemeta started alongside, shorter debounce), kids filter on results |
| `0006-profiles` | UI/Profile | "Who's watching" polish (Kids tag, greeting, bigger avatars, focus hint, entrance), Speed Report mark when the picker appears |
| `0007-settings-screen` | UI/Settings/SettingsView | All fork switches (Netflix Style, Play Something, Card Tags, Kids options, Ask If Still Watching, …), the Style picker (Netflix Style / Custom; Disney+ and Max Style were dropped 2026-11-13), Speed Report row under Advanced |
| `0008-sync-and-trakt` | Core/Sync, Core/Trakt | Sync and Trakt fixes; Remind Me sends the full release date |
| `0009-appearance` | Core/AppLanguage, SplashScreen storyboard and colour | Avenir Next as an app typeface; the launch screen background (#141414) |

To change a feature, edit the patched source and regenerate the patch for that file's group
(`git diff BASE HEAD -- <files in the group>`).
