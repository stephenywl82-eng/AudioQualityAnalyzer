# Audio Quality Analyzer

A local audio quality assessment tool for Android. **All analysis and processing happens on your device — your audio is never uploaded.** The only optional network feature is metadata lookups (MusicBrainz / Cover Art Archive).

> **Important:** Every "quality" and "source" verdict in this app is a *probabilistic inference* based on signal characteristics — a clue, **not proof** of audio quality. FLAC integrity verification is the sole exception: it is an objective byte-for-byte comparison.

This repository distributes **binary releases and documentation only** — source code is not public.

## Download

- Get the latest APK from the [Releases page](https://github.com/stephenywl82-eng/AudioQualityAnalyzer/releases) (v1.9, Android 8.0 / API 26+).
- Direct download: [AudioQualityAnalyzer-v1.9.apk](https://github.com/stephenywl82-eng/AudioQualityAnalyzer/releases/download/v1.9/AudioQualityAnalyzer-v1.9.apk)
- The app is not on any app store; Android will ask you to allow installation from unknown sources.
- Each release is a signed, R8-optimized build.

## Features

**Analysis**
- Per-channel peak / RMS, dynamic range, clipping ratio, DC offset
- Spectral cutoff estimation, spectral flatness, spectral cliff detection
- EBU R128 loudness (integrated / short-term max / true peak / ReplayGain)
- BPM & key detection, waveform envelope, spectrogram, goniometer phase scope
- FLAC integrity: STREAMINFO quick check + byte-for-byte MD5 verification (decode the full track, repack the byte stream, compare against the declared checksum)
- Codec fingerprinting (hints about lossy transcoding)

**Library & management**
- Incremental scanning of local audio via MediaStore, with a sortable / filterable / searchable / grouped list
- Library health check: batch-detect clipping, truncation, low loudness, and questionable sources
- Metadata editor: full-format tag and cover read/write, three write-back strategies (in-place / backup-and-restore / save-as-copy), plus filename editing
- Batch rename (template-based, saves copies — never touches originals)
- Online lookup: query MusicBrainz metadata and Cover Art Archive covers by title / artist, filling empty fields only

**Export & playback**
- Four export formats: WAV (16 / 24 / 32-bit float), MP3 (LAME VBR), AAC (m4a), FLAC
- Resampling, independent speed / pitch control, stereo preservation, text tag and cover copying
- Spectrogram / waveform workbench: zoom, draggable viewport, tap-to-seek playback, A–B loop
- Two-file comparison: power-spectrum difference, 30-second synced playback, cross-correlation auto-alignment, difference-signal subtraction, ABX blind test
- External player integration

**Other**
- Bilingual UI (English / 中文), Material 3 Expressive design, system light/dark theme with wallpaper-derived color
- Categorized runtime log (scan / export / error / settings / diagnostics), filterable and shareable for troubleshooting

## Privacy

- Audio files, analysis results, and tag edits are all handled locally. No audio is uploaded.
- Online lookup is explicitly user-triggered: it sends only the title / artist text to MusicBrainz and downloads cover art — never your audio.
- Runtime logs are stored only in the app's private directory and shared only when you choose to share them.

## Third-party components & licenses

The app uses open-source components. Their licenses and notices are in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md), including TagLib (LGPL-2.1 / MPL-1.1), FFmpeg minimal build (LGPL-2.1+), LAME 3.100 (LGPL), dr_flac (Public Domain / MIT-0), libebur128 (MIT), Oboe (Apache-2.0), and Jetpack Compose / Material 3 Expressive (Apache-2.0).

LGPL components are dynamically linked. For corresponding source and relinking materials, contact the maintainer via an issue.
