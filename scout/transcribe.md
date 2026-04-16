---
name: transcribe
description: Transcribe video from any URL (YouTube, Instagram, TikTok, X, Facebook, Vimeo, 1000+ sites) into text via yt-dlp + faster-whisper
---

Transcribe any video URL into text. Supports 1000+ sites via yt-dlp. No API keys required.

Use $ARGUMENTS as the video URL to transcribe.

## When to Use

- Transcribing competitor videos for analysis
- Extracting content from social media videos for repurposing
- Creating transcripts for YouTube descriptions (pairs with youtube-content skill)
- Turning video content into searchable text for research

## Dependencies

- Python 3.8+
- `faster-whisper` — `pip3 install faster-whisper`
- `yt-dlp` — `pip3 install yt-dlp`
- `ffmpeg` — `brew install ffmpeg` (macOS)

## Workflow

1. Ask the user: "Include timestamps?" (Yes / No)
2. Run the transcription script:

```bash
python3 <skill_path>/scripts/transcribe_url.py "<url>" [--timestamps]
```

3. Present the transcript output to the user.

## Options

| Flag | Effect |
|------|--------|
| `--timestamps` | Prefix each segment with `[M:SS]` timestamp |
| `--model <size>` | Whisper model size. Default: `medium`. Options: `small` (faster), `large-v3` (max accuracy) |

## Output

The script prints:
- **Metadata header** — platform, title, uploader, duration
- **Transcript text** — grouped into ~30-second paragraphs, or timestamped segments if `--timestamps` used
- **Completion summary** (stderr) — segment count, language detected

## Important: Force English

Always force `language='en'` for English-speaking content. Auto-detect misidentifies some accents (e.g., Singaporean English detected as Malay). If transcription quality is poor, try `--model large-v3`.

## Dependency Errors

If the script exits with missing dependency errors:

```bash
pip3 install yt-dlp faster-whisper
brew install ffmpeg  # macOS
```

## Pairs With

| Task | Skill |
|------|-------|
| Writing YouTube descriptions from transcripts | youtube-content |
| Creating content from video research | content-strategy + transcribe |
| Analyzing competitor video ads | paid-media-audit + transcribe |
| Mining buyer language from videos | buyer-research (transcript input mode) |
