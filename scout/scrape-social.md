---
name: scrape-social
description: Universal social intelligence API — scrape profiles, videos, posts, ads, trending content across 25+ platforms via ScrapeCreators
---

Universal social intelligence API client for 25+ platforms. Use when any task needs social media data — profiles, videos, posts, comments, transcripts, trending content, ad library research, or competitor scanning.

Use $ARGUMENTS as the platform + action (e.g., "tiktok videos @competitor").

## Quick Start

```bash
# Set API key
echo 'SCRAPECREATORS_API_KEY=your_key' >> .env

# Basic usage
python3 skills/scrapecreators/scripts/scrape.py <platform> <command> [args] [--flags]

# Check credits
python3 skills/scrapecreators/scripts/scrape.py credits
```

## Full Command Reference

### TikTok (20 endpoints + 4 TikTok Shop)

| Command | Endpoint | Credits |
|---------|----------|---------|
| `tiktok profile <user>` | `/v1/tiktok/profile` | 1 |
| `tiktok audience <user>` | `/v1/tiktok/user/audience` | **26** |
| `tiktok videos <user> [--pages N]` | `/v3/tiktok/profile/videos` | 1/page |
| `tiktok video <id>` | `/v2/tiktok/video` | 1 |
| `tiktok transcript <id>` | `/v1/tiktok/video/transcript` | 1 |
| `tiktok comments <id>` | `/v1/tiktok/video/comments` | 1 |
| `tiktok search <query> [--type]` | `/v1/tiktok/search/*` | 1 |
| `tiktok trending [--hashtags|--sounds|--creators|--feed]` | `/v1/tiktok/*/popular` | 1 |
| `tiktok shop <query>` | `/v1/tiktok/shop/search` | 1 |
| `tiktok song <id> [--videos]` | `/v1/tiktok/song[/videos]` | 1 |
| `tiktok following <user>` | `/v1/tiktok/user/following` | 1 |
| `tiktok followers <user>` | `/v1/tiktok/user/followers` | 1 |
| `tiktok live <user>` | `/v1/tiktok/user/live` | 1 |

### Instagram (12 endpoints)

| Command | Endpoint | Credits |
|---------|----------|---------|
| `instagram profile <user>` | `/v1/instagram/profile` | 1 |
| `instagram posts <user>` | `/v2/instagram/user/posts` | 1 |
| `instagram post <shortcode>` | `/v1/instagram/post` | 1 |
| `instagram transcript <shortcode>` | `/v2/instagram/media/transcript` | 1 |
| `instagram comments <shortcode>` | `/v2/instagram/post/comments` | 1 |
| `instagram reels <user>` | `/v1/instagram/user/reels` | 1 |
| `instagram search-reels <query>` | `/v2/instagram/reels/search` | 1 |
| `instagram highlights <user>` | `/v1/instagram/user/highlights` | 1 |

### YouTube (11 endpoints)

| Command | Endpoint | Credits |
|---------|----------|---------|
| `youtube channel <id>` | `/v1/youtube/channel` | 1 |
| `youtube videos <channel_id>` | `/v1/youtube/channel-videos` | 1 |
| `youtube shorts <channel_id>` | `/v1/youtube/channel/shorts` | 1 |
| `youtube video <id>` | `/v1/youtube/video` | 1 |
| `youtube transcript <id>` | `/v1/youtube/video/transcript` | 1 |
| `youtube search <query> [--type]` | `/v1/youtube/search` | 1 |
| `youtube comments <id>` | `/v1/youtube/video/comments` | 1 |
| `youtube trending-shorts` | `/v1/youtube/shorts/trending` | 1 |
| `youtube playlist <id>` | `/v1/youtube/playlist` | 1 |

### LinkedIn (6 endpoints)

| Command | Endpoint | Credits |
|---------|----------|---------|
| `linkedin profile <url>` | `/v1/linkedin/profile` | 1 |
| `linkedin company <url>` | `/v1/linkedin/company` | 1 |
| `linkedin company-posts <url>` | `/v1/linkedin/company/posts` | 1 |
| `linkedin post <url>` | `/v1/linkedin/post` | 1 |
| `linkedin ads <query>` | `/v1/linkedin/ads/search` | 1 |

### Facebook (8 + 4 Ad Library endpoints)

| Command | Endpoint | Credits |
|---------|----------|---------|
| `facebook profile <user>` | `/v1/facebook/profile` | 1 |
| `facebook posts <user>` | `/v1/facebook/profile/posts` | 1 |
| `facebook reels <user>` | `/v1/facebook/profile/reels` | 1 |
| `facebook ads-search <query> [--country]` | `/v1/facebook/adLibrary/search/ads` | 1 |
| `facebook company-ads <company>` | `/v1/facebook/adLibrary/company/ads` | 1 |
| `facebook group <group_id>` | `/v1/facebook/group/posts` | 1 |

### Twitter/X (6 endpoints)

| Command | Endpoint | Credits |
|---------|----------|---------|
| `twitter profile <user>` | `/v1/twitter/profile` | 1 |
| `twitter tweets <user>` | `/v1/twitter/user-tweets` | 1 |
| `twitter tweet <id>` | `/v1/twitter/tweet` | 1 |
| `twitter transcript <id>` | `/v1/twitter/tweet/transcript` | 1 |

### Reddit (7 endpoints)

| Command | Endpoint | Credits |
|---------|----------|---------|
| `reddit subreddit <name>` | `/v1/reddit/subreddit` | 1 |
| `reddit subreddit-details <name>` | `/v1/reddit/subreddit/details` | 1 |
| `reddit search <query>` | `/v1/reddit/search` | 1 |
| `reddit subreddit-search <name> <query>` | `/v1/reddit/subreddit/search` | 1 |
| `reddit comments <post_id>` | `/v1/reddit/post/comments` | 1 |

### Other Platforms

| Command | Credits |
|---------|---------|
| `threads profile/posts/search` | 1 |
| `bluesky profile/posts` | 1 |
| `pinterest search/boards` | 1 |
| `google search/company-ads/advertisers` | 1 |

## Credit Costs

| Endpoint | Credits | Note |
|----------|---------|------|
| Most endpoints | 1 | Standard |
| TikTok audience demographics | **26** | Use sparingly |
| Multi-page pagination | 1/page | Cap with `--pages` |

**Budget rule:** Typical competitor scan (3 profiles + 2 keywords + trending) = ~7 credits.

## Common Flows

### Competitor Analysis (5-7 credits)
```bash
scrape.py tiktok profile @competitor
scrape.py tiktok videos @competitor --pages 2
scrape.py tiktok search "their niche keyword" --type top
```

### Trend Monitoring (3-4 credits)
```bash
scrape.py tiktok trending --hashtags
scrape.py tiktok trending --sounds
scrape.py tiktok trending --feed
```

### Ad Research (2-3 credits)
```bash
scrape.py facebook ads-search "competitor name" --country US
scrape.py google company-ads "competitor name"
```

### Content Research (3-5 credits)
```bash
scrape.py youtube videos UC-channelid
scrape.py youtube transcript dQw4w9WgXcQ
scrape.py reddit subreddit-search "marketing" "ai tools"
```

## Output Formats

```bash
# Force JSON
scrape.py tiktok profile @user --format json

# Pipe to file
scrape.py tiktok videos @user --format json -o data/competitor.json

# Pipe to jq
scrape.py tiktok profile @user --format json | jq '.data.followerCount'
```

Default: Markdown in terminal, JSON when piped.

## Python Import (for other scripts)

```python
import sys
from pathlib import Path
sys.path.insert(0, str(Path(__file__).resolve().parents[2] / "scrapecreators" / "scripts"))
from api import ScrapeCreatorsClient

client = ScrapeCreatorsClient(quiet=True)
videos = client.tiktok_videos("charlidamelio")
profile = client.instagram_profile("nike")

# Generic endpoint
data = client.request("/v1/some/new/endpoint", {"param": "value"})
```

## Error Types

- `AuthError` — Invalid API key (check `.env`)
- `NotFoundError` — User/video/post not found
- `RateLimitError` — Too many requests
- `ServerError` — API server issue (auto-retries once)

## Setup

1. Get API key at https://app.scrapecreators.com
2. Add to `.env`: `SCRAPECREATORS_API_KEY=your_key_here`
3. Install: `pip install requests`
4. Test: `python3 skills/scrapecreators/scripts/scrape.py credits`
