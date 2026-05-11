# The Lost Bureau — CLAUDE.md

## Project Overview

**The Lost Bureau** is a faceless YouTube channel producing 26-34 minute documentary-style videos about forgotten history, banned survival skills, and "what governments don't want you to know."

**Business Model:** AdSense revenue (target $3k-5k/month within 6 months)  
**Language:** English (all content)  
**Target Audience:** 25-55 year old males (US/UK primary)  
**Status:** Pre-Launch (Production Phase)

---

## Core Rules

1. **All content in English** — scripts, voiceovers, titles, thumbnails, metadata
2. **No face, no creator brand** — channel is the brand, not a person
3. **Conspiracy/Forbidden framing** — titles use "Illegal", "Banned", "Government Doesn't Want"
4. **Evergreen focus** — 70% of content should generate views for years
5. **Consistency over perfection** — ship 2-3 videos/week, optimize based on analytics

---

## Tech Stack

| Layer | Tool | Purpose |
|-------|------|---------|
| **Scripting** | Claude Code (AI) | Generate scripts from ideas |
| **Thumbnails** | Nano Banana API | Batch generate variations |
| **Voiceover** | ElevenLabs API | Convert script to MP3 |
| **Video Assets** | Veo3 + Archive.org | B-roll and stock footage |
| **Editing** | CapCut or DaVinci Resolve | Final video production |
| **Publishing** | YouTube API | Schedule uploads, track metrics |
| **Version Control** | GitHub | Repo at github.com/oscarpinzon-ai/thelostbureau |

---

## Production Workflow (Step-by-Step)

### Phase 1: Ideation + Script
1. Pick video from approved list (see `content/video-ideas.md`)
2. Run Claude Code script generator: `node automation/claude-script-generator.js --title "..." --duration 28`
3. Manual research: Wikipedia + Archive.org + Reddit (validate claims)
4. Revise script for flow + tone (conversational, not academic)
5. Save to `content/scripts/video-[id]-script.md`

### Phase 2: Visual Assets
1. Generate thumbnail batch: `node automation/thumbnail-batch-generator.js --title "..."`
2. Collect B-roll footage: Download from Archive.org, Pexels, Unsplash (tag sources)
3. Save manifest: `production/raw-footage/assets-manifest.json` (track all sources)
4. AI-generated transitions: Use Veo3 for gaps or dynamic sequences

### Phase 3: Voiceover
1. Run TTS batch: `node automation/elevenlabs-batch-tts.js --script content/scripts/video-[id]-script.md`
2. Review MP3: Check for pronunciation issues (edit if needed)
3. Save to `production/voiceovers/video-[id]/voiceover.mp3`

### Phase 4: Editing
1. Open CapCut or DaVinci Resolve
2. Import voiceover MP3 + B-roll clips
3. Sync to timeline (match voiceover pacing)
4. Apply edits:
   - Cut transitions every 2-3 seconds
   - Ken Burns effect on static images
   - Color grading: Desaturate -15%, warm cast
   - Text overlays for key claims (3-5 second duration)
5. Target 26-34 minutes (2-3 mid-roll ad breaks)
6. Export: 1080p60 H.264, max bitrate 12Mbps
7. Save to `production/final-videos/video-[id]-final.mp4`

### Phase 5: YouTube Publishing
1. Create metadata: `youtube-metadata.json`
   - Title, description, tags, category
   - Call-to-action in description (3-4 sources linked)
2. Pick winning thumbnail (from batch test results)
3. Schedule in YouTube Studio (same day/time weekly)
4. Add cards: Link to 2 related videos
5. Run analytics tracker: `node automation/youtube-scheduler.js`

---

## File Structure

See `THE-LOST-BUREAU-BLUEPRINT.md` Part 7 for complete directory structure.

Key directories:
- `content/` — Ideas, scripts, SEO keywords
- `production/` — Thumbnails, voiceovers, B-roll, final videos
- `automation/` — Claude Code scripts + config files
- `analytics/` — Performance tracking + upload schedule

---

## Environment Setup

### 1. Install Dependencies
```bash
npm install
```

### 2. Configure `.env.local`
```
ELEVENLABS_API_KEY=sk-...
NANO_BANANA_API_KEY=sk-...
YOUTUBE_API_KEY=AIzaSy...
GITHUB_TOKEN=ghp_...
```

### 3. Test Scripts
```bash
# Generate script
node automation/claude-script-generator.js --title "Test Video" --duration 28

# Generate thumbnails
node automation/thumbnail-batch-generator.js --title "Test Video"

# Generate voiceover
node automation/elevenlabs-batch-tts.js --script content/scripts/test-script.md
```

---

## Key Metrics to Track

| Metric | Tool | Why It Matters |
|--------|------|---|
| CTR | YouTube Analytics | Click-through rate → thumbnail quality |
| Avg View Duration | YouTube Analytics | Watch time → content engagement |
| Comments | YouTube Analytics | Community sentiment → title/hook accuracy |
| Subscriber Growth | YouTube Analytics | Long-term channel health |
| RPM | YouTube Analytics | Revenue per 1,000 views |

**Weekly Review:** Check metrics every Sunday evening, document learnings in `analytics/performance-tracker.md`.

---

## Title + Thumbnail Strategy (Tested Pattern)

### Title Formula
`[BANNED/ILLEGAL/FORBIDDEN] [SUBJECT] [GOVERNMENT/THEY] [ACTION VERB]`

Examples (Proven):
- "This **Illegal** Survival Skill the **Government Doesn't Want** You Remembering"
- "**Forgotten** Americans Made $500/Week With This — **Why It Vanished**"
- "The **Banned** Technique That Could Save Your Life — **Government Hopes You Never** Discover It"

### Thumbnail Formula
- Dark background (charcoal #2D2D2D)
- Bold white/gold text (40pt minimum)
- Archive or vintage imagery (35% opacity)
- Small "THE LOST BUREAU" logo (bottom-left)
- High contrast → high CTR

---

## Editing Standards

**Non-negotiables:**
- ✅ Cut every 2-3 seconds (fast pacing)
- ✅ Audio: -3dB peak level (no clipping)
- ✅ Text: 40pt minimum font size (mobile readable)
- ✅ No silent gaps (every frame purposeful)
- ✅ Color consistent throughout video
- ✅ Final length: 26-34 minutes (2-3 mid-rolls)

**Optional (enhances quality):**
- Ken Burns effect on static images
- Subtle background music (low volume)
- Animated section headers (every 5-7 min)
- Text overlays for key claims

---

## SEO Best Practices

**Title:** 60 characters max (includes target keyword)  
**Description:** 300 words (hook + sources + CTA)  
**Tags:** 8-12 (mix high-volume + niche)  
**Hashtags:** 2-3 (in description, not title)  
**Category:** Documentary  

**Description Template:**
```
[Hook sentence]

Sources:
1. [Source title] - [timestamp in video]
2. [Source title] - [timestamp in video]
3. [Source title] - [timestamp in video]

Want more forgotten history? Subscribe and hit the bell.

Related videos:
- [Link to video 2]
- [Link to video 3]
```

---

## Upload Schedule

- **Frequency:** 2-3 videos per week
- **Days:** Tuesday, Thursday, Friday (based on audience data)
- **Time:** 6 PM UTC (convert to local if different)
- **Consistency:** Same time every upload day

---

## Common Pitfalls to Avoid

❌ **Don't:**
- Make up false claims (algorithm will shadow-ban for misleading info)
- Use copyrighted music or footage (always credit sources)
- Hardcode credentials in scripts (use `.env.local`)
- Ship videos without watching full cut (QA matters)
- Ignore analytics (CTR/watch time drives algorithm)

✅ **Do:**
- Research every claim (Wikipedia + 2 other sources minimum)
- Properly credit archive footage in description
- A/B test thumbnails (first 48 hours, pick winner)
- Monitor comments (community sentiment → next video ideas)
- Update analytics tracker weekly

---

## Deployment Checklist (Before Every Upload)

- [ ] Video fully edited + color graded
- [ ] Voiceover synced correctly
- [ ] All B-roll sources credited in metadata
- [ ] Thumbnail A/B tested (pick best CTR)
- [ ] Title optimized for SEO (includes keyword + hook)
- [ ] Description written (300 words, 3+ sources linked)
- [ ] Tags added (8-12, mix high/low volume)
- [ ] YouTube metadata filled in Studio
- [ ] Scheduled 24h in advance
- [ ] Community post created (tease video)
- [ ] Analytics tracker updated

---

## First 4 Videos (Launch Plan)

| Video | Publish | Target | Notes |
|-------|---------|--------|-------|
| 1 | Thu Week 1 | 10K views | Establish brand voice |
| 2 | Fri Week 1 | 15K views | Test thumbnail variations |
| 3 | Tue Week 2 | 20K views | Optimize based on V1+V2 |
| 4 | Thu Week 2 | 25K views | Confirm pattern working |

**Success Metrics (Month 1):**
- 100-200 subscribers
- 50K-100K total views
- 6-8% CTR average
- 50%+ avg view duration

---

## Questions? Escalate to Claude Code

If you're stuck on:
- **Script quality:** Re-run generator with different keywords
- **Thumbnail CTR:** Create new variations with Nano Banana
- **Audio sync:** Check timeline zoom level + voiceover duration
- **Publishing errors:** Check YouTube API credentials in `.env.local`

All tools are documented in `automation/` folder with example usage.

---

**Project Lead:** Oscar Pinzon  
**Repository:** github.com/oscarpinzon-ai/thelostbureau  
**Launch Target:** 2 weeks from blueprint approval
