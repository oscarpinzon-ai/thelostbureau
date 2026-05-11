# The Lost Bureau

**Forgotten Knowledge, Documented**

A faceless YouTube channel producing documentary-style videos about forgotten history, banned survival skills, and "what governments don't want you to know."

---

## Quick Start

### 1. Setup
```bash
# Clone repository
git clone https://github.com/oscarpinzon-ai/thelostbureau.git
cd thelostbureau

# Install dependencies
npm install

# Configure API keys
cp .env.example .env.local
# Edit .env.local with your ElevenLabs, Nano Banana, YouTube API keys
```

### 2. Generate First Video
```bash
# Generate script
node automation/claude-script-generator.js \
  --title "This Illegal Survival Skill the Government Doesn't Want You Remembering" \
  --duration 28

# Generate thumbnails
node automation/thumbnail-batch-generator.js \
  --title "This Illegal Survival Skill the Government Doesn't Want You Remembering"

# Generate voiceover
node automation/elevenlabs-batch-tts.js \
  --script content/scripts/video-001-script.md
```

### 3. Edit in CapCut or DaVinci Resolve
1. Import voiceover MP3 + B-roll from `production/raw-footage/`
2. Sync to timeline (2-3 second cuts)
3. Apply color grading + Ken Burns effects
4. Export 1080p60 to `production/final-videos/`

### 4. Publish to YouTube
1. Run: `node automation/youtube-scheduler.js --video video-001`
2. Pick winning thumbnail from `production/thumbnails/video-001/`
3. Schedule in YouTube Studio

---

## Directory Structure

```
├── brand/                 # Logo, colors, style guide
├── content/               # Video ideas, scripts, SEO keywords
├── production/            # Thumbnails, voiceovers, footage, final videos
├── automation/            # Claude Code scripts for workflow
├── analytics/             # Performance tracking & metrics
├── .github/workflows/     # CI/CD pipelines (auto-schedule, analytics)
├── THE-LOST-BUREAU-BLUEPRINT.md  # Full design document
└── CLAUDE.md              # Project instructions for builders
```

See `THE-LOST-BUREAU-BLUEPRINT.md` for complete directory breakdown.

---

## Production Workflow

```
Idea → Script Generation → Thumbnail Batch → Voiceover TTS → B-roll Collection
  ↓                                                               ↓
[Research & Validate]                                    [Organize in Manifest]
  ↓                                                               ↓
  └─────────────────────── Editing (CapCut/DaVinci) ────────────┘
                                    ↓
                            Export Final Video
                                    ↓
                         YouTube Publishing API
                                    ↓
                          Track Analytics Weekly
```

---

## Key Files

| File | Purpose |
|------|---------|
| `THE-LOST-BUREAU-BLUEPRINT.md` | Complete design + 10 video ideas |
| `CLAUDE.md` | Project instructions + rules |
| `content/video-ideas.md` | Approved video concepts (ready to produce) |
| `automation/` | 4 utility scripts (script gen, thumbnails, TTS, scheduling) |
| `analytics/performance-tracker.md` | Weekly metrics + learnings |

---

## Video Ideas (Launch 10)

All pre-researched and ready to produce:

1. ✅ Government Doesn't Want You Remembering This Illegal Survival Skill
2. ✅ Forgotten Americans Did This Weekly — Why They're Hiding It Today
3. ✅ This Banned Skill Could Save Your Life
4. ✅ The Illegal Side Hustle That Made $500/Week Before The IRS Shut It Down
5. ✅ What They Don't Want You Knowing About Ancient Survival Methods
6. ✅ The Government-Banned Technique Americans Used For Centuries
7. ✅ Forgotten Americans Made Thousands With This Lost Skill
8. ✅ This Illegal Knowledge Could Change Everything
9. ✅ The Banned Survival Handbook They Tried To Destroy
10. ✅ Forgotten Ways To Make Money That Still Work Today

See `content/video-ideas.md` for full details (hooks, keywords, duration, publishing schedule).

---

## Tools & Technologies

| Tool | Purpose | Why |
|------|---------|-----|
| **Claude Code** | Script generation, automation | AI-powered content creation |
| **Nano Banana API** | Thumbnail generation | Batch produce variations |
| **ElevenLabs API** | Voiceover TTS | Professional-quality audio |
| **YouTube API** | Publishing + analytics | Direct channel management |
| **CapCut / DaVinci Resolve** | Video editing | Professional quality, free options |
| **Archive.org** | Historical B-roll | Free, high-quality public domain |
| **Veo3** | AI-generated sequences | Dynamic transitions, fills |

---

## Success Metrics (First Month)

| Metric | Target | Source |
|--------|--------|--------|
| Total Views | 50K-100K | YouTube Analytics |
| Subscribers | 100-200 | YouTube Analytics |
| Avg CTR | 6-8% | YouTube Analytics |
| Avg Watch Duration | 50%+ | YouTube Analytics |
| Total Comments | 100+ | YouTube Analytics |

**Weekly tracking:** See `analytics/performance-tracker.md`

---

## Publishing Schedule

- **Frequency:** 2-3 videos per week
- **Days:** Tuesday, Thursday, Friday (proven optimal times)
- **Time:** 6 PM UTC (adjust for your timezone)
- **Consistency:** Same day/time every week

---

## API Configuration

### ElevenLabs
```json
{
  "ELEVENLABS_API_KEY": "sk-...",
  "VOICE_ID": "male-us-neutral",
  "STABILITY": 0.7,
  "SIMILARITY_BOOST": 0.75
}
```

### Nano Banana
```json
{
  "NANO_BANANA_API_KEY": "sk-...",
  "MODEL": "stable-diffusion-xl",
  "OUTPUT_PATH": "./production/thumbnails"
}
```

### YouTube
```json
{
  "YOUTUBE_API_KEY": "AIzaSy...",
  "CHANNEL_ID": "UC...",
  "PLAYLIST_ID": "PL..."
}
```

All keys stored in `.env.local` (never commit to Git).

---

## Editing Standards

✅ **Do:**
- Cut every 2-3 seconds (fast pacing)
- Ken Burns effect on static images
- Desaturate -15% color (nostalgic tone)
- Normalize audio to -3dB peak
- Text overlays every 3-5 seconds
- Target 26-34 minutes (2-3 mid-rolls)

❌ **Don't:**
- Leave silent gaps
- Make font smaller than 40pt
- Use copyrighted music (always credit)
- Fact-check failures (verify 2+ sources)
- Upload without watching full cut

---

## Thumbnail Strategy

**Formula:** Dark background + Bold text + Vintage imagery + "The Lost Bureau" logo

**Batch Process:**
1. Generate 3-5 variations via Nano Banana
2. A/B test first 48 hours (monitor CTR)
3. Lock best performer as upload thumbnail
4. Document results in `analytics/thumbnail-ab-tests.json`

**Example Prompts:**
```
Generate THE LOST BUREAU style thumbnail:
- Dark charcoal background (#2D2D2D)
- Bold white text: "ILLEGAL SURVIVAL SKILL"
- Vintage archive imagery (35% opacity)
- Gold bar accent (bottom)
- "THE LOST BUREAU" logo (bottom-left)
```

---

## First Video Checklist

- [ ] Script written + researched (3+ sources)
- [ ] Thumbnail batch generated (3-5 variations)
- [ ] Voiceover TTS complete (ElevenLabs)
- [ ] B-roll footage collected (Archive.org + stock)
- [ ] Video fully edited (color graded, all cuts synced)
- [ ] Metadata written (title, description, tags)
- [ ] YouTube scheduled 24h before publish
- [ ] Community post created (day before)
- [ ] Launch + monitor for first 48h

---

## FAQ

**Q: How long does each video take to produce?**  
A: ~6-8 hours (research 1h, script 1h, thumbnails 30m, voiceover 30m, editing 3-4h)

**Q: What's the equipment needed?**  
A: None. Everything is software-based. CapCut is free.

**Q: Can I use copyrighted music?**  
A: No. Either use royalty-free music or go silent. Always credit sources in description.

**Q: How do I know if a video title will work?**  
A: Follow the formula: `[BANNED/ILLEGAL] [SUBJECT] [GOVERNMENT] [ACTION]`. If it fits, it works.

**Q: When will I see revenue?**  
A: After 1,000 subscribers + 4,000 watch hours (usually 4-8 weeks at current growth rate).

---

## Support

See `CLAUDE.md` for detailed project instructions.

For script/automation issues, check `automation/` folder examples.

For YouTube API problems, verify credentials in `.env.local`.

---

## Launch Timeline

- **Week 1:** Setup + brand design + write scripts 1-3
- **Week 2:** Generate thumbnails/voiceovers + edit videos 1-3
- **Week 3:** Finalize + test thumbnails + schedule videos 1-3
- **Week 4:** Launch + monitor metrics + continue production

**Target Launch Date:** 2 weeks from blueprint approval

---

**Repository:** github.com/oscarpinzon-ai/thelostbureau  
**Status:** Pre-Launch (Production Phase)  
**Last Updated:** 2025-05-10
