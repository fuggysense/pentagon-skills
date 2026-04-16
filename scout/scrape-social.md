---
name: scrape-social
description: Scrape social media for buyer language via ScrapeCreators API. Reddit, YouTube comments, TikTok, Facebook Ad Library, Instagram. Use when collecting raw buyer language from social platforms.
---

Scrape social media data for $ARGUMENTS.

Available commands:
- reddit subreddit <name> — posts from a subreddit
- reddit search <query> — search across Reddit
- youtube comments <video-id> — comments on a video
- tiktok comments <video-id> — comments on a TikTok
- facebook ads-search "keyword" — Meta Ad Library search
- instagram comments <shortcode> — comments on a post

Process:
1. Identify which platforms match the target audience from ICP
2. Run relevant scrape commands
3. Extract verbatim quotes with source attribution
4. Save raw data to clients/<project>/research/raw/
5. Dedupe and tag quotes by source

Each endpoint = 1 credit. Budget accordingly.
