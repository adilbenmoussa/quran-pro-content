# quran-pro-content

Where the Qur'an Pro app finds each reciter's audio, and the ayah timings that go with it.

- `manifest.json`: every reciter, the addresses of its 114 surah files (first address first, fallbacks after), their sizes, and the revision of its timings. The app checks it at most once a day at `https://adilbenmoussa.github.io/quran-pro-content/manifest.json`, with jsDelivr's copy as the second address, and uses it only when its `version` is higher than the one it has.
- `timings/<reciter>-r<revision>.json`: ayah timings per surah, rows of `[ayah, start ms, end ms]`; ayah 0 is the opening before ayah 1.

Do not edit by hand. Both are written by `tools/build-content` in the app's repo (`npm run build`), which raises the version and the revisions only when something changed. A fixed audio file gets a new file name, never the old one overwritten, so phones that downloaded the old file see its size change and download it again.
