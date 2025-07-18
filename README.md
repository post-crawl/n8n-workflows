# n8n Workflows Collection

A collection of automated workflows for n8n automation platform.

## Files

- [`README.md`](#readme) - This documentation file
- [`workflows/reddit-story-podcast.json`](#reddit-story-podcast) - Ultra-short podcast generator from Reddit stories
- [`workflows/youtube-script-generator.json`](#youtube-script-generator) - Reddit-based YouTube Shorts script generator

## Workflows

### Reddit Story Podcast

**File:** [`workflows/reddit-story-podcast.json`](./workflows/reddit-story-podcast.json)

An automated workflow that creates ultra-short podcast episodes (under 1 minute) from Reddit stories using PostCrawl API and OpenAI text-to-speech.

#### What It Does

This workflow automatically:
- Fetches trending short stories from Reddit using PostCrawl
- Selects the best story based on engagement and brevity
- Generates a punchy 45-second script using OpenAI
- Creates high-quality audio using text-to-speech
- Outputs a ready-to-share audio file

#### How It Works

1. **Manual Trigger**: Start the workflow on-demand
2. **Configuration**: Set subreddit, voice model, and speech parameters
3. **Story Fetching**: Uses PostCrawl to search for "best short" stories
4. **Story Selection**: Scores stories based on engagement and word count
5. **Script Generation**: OpenAI creates a 45-second podcast script
6. **Audio Creation**: Converts script to speech using OpenAI TTS
7. **Final Output**: Provides audio data URI with metadata

#### Prerequisites

1. **n8n instance** - Running n8n automation platform
2. **PostCrawl API account** - For Reddit content extraction
3. **OpenAI API account** - For script generation and text-to-speech

#### Setup Instructions

1. **Import the workflow**:
   - Open your n8n instance
   - Go to Workflows → Import from file
   - Select `reddit-story-podcast.json`

2. **Configure authentication**:
   - **PostCrawl API Node**: Add your PostCrawl Bearer token in credentials
   - **OpenAI Nodes**: Configure your OpenAI API credentials

3. **Configure parameters**:
   - Edit the "Short Podcast Configuration" node
   - Set `subreddits`: Target subreddit (default: "AskReddit")
   - Set `numberOfStories`: How many stories to fetch
   - Set `voiceModel`: TTS voice (default: "nova")
   - Set `speechSpeed`: Playback speed (default: 1.15)

#### Output Format

The workflow produces:
- **Audio Data URI**: Ready-to-play audio file
- **Metadata**: Title, subreddit, date, original score
- **Duration**: Estimated length in seconds
- **Script**: Full text for reference

#### Features

- **Ultra-short format**: Optimized for under 45-second episodes
- **Smart story selection**: Prioritizes engaging yet brief content
- **High energy delivery**: Fast speech rate (1.15x) for dynamic listening
- **Single story focus**: Maximum impact with one great story

#### Use Cases

- Social media shorts and reels
- Story previews and teasers
- Daily quick listens
- Testing podcast concepts
- Bite-sized content for busy audiences

### YouTube Script Generator

**File:** [`workflows/youtube-script-generator.json`](./workflows/youtube-script-generator.json)

An automated workflow that searches multiple Reddit subreddits for trending content and uses OpenAI to generate engaging scripts for YouTube Shorts based on the discovered content.

#### What It Does

This workflow automatically:
- Searches multiple Reddit subreddits using PostCrawl API
- Extracts popular posts with engagement metrics and top comments
- Analyzes Reddit content to identify viral-worthy themes
- Generates multiple script variations for YouTube Shorts (under 60 seconds)
- Formats scripts with hooks, body content, and call-to-actions
- Outputs production-ready scripts for various content categories

#### How It Works

1. **Manual Trigger**: Start the workflow on-demand
2. **Configuration**: Set search topic, content category, target subreddits, and number of posts
3. **Reddit Search**: Uses PostCrawl to search multiple subreddits simultaneously
4. **Post Filtering**: Removes posts with extraction errors
5. **Data Preparation**: Extracts titles, descriptions, scores, and top comments
6. **AI Generation**: OpenAI GPT-4o-mini creates 3-5 script variations
7. **Script Formatting**: Outputs structured scripts with metadata

#### Prerequisites

1. **n8n instance** - Running n8n automation platform
2. **PostCrawl API account** - For Reddit content extraction
3. **OpenAI API account** - For AI-powered script generation

#### Setup Instructions

1. **Import the workflow**:
   - Open your n8n instance
   - Go to Workflows → Import from file
   - Select `youtube-script-generator.json`

2. **Configure authentication**:
   - **PostCrawl API Node**: Add your PostCrawl Bearer token in credentials
   - **OpenAI Node**: Configure your OpenAI API credentials

3. **Configure search parameters**:
   - Edit the "Configuration" node
   - Set `topic`: Your search terms (e.g., "yeti bigfoot")
   - Set `category`: Content type (e.g., "conspiracy theories", "jokes", "today i learned")
   - Set `subreddits`: Space-separated list (e.g., "HighStrangeness Cryptozoology bigfoot")
   - Set `numberOfPosts`: 15-20 recommended for multi-subreddit searches

#### Output Format

Each generated script includes:
- **Title**: Catchy title for the content
- **Hook**: Opening line to grab attention
- **Body**: Main content (optimized for 60-second delivery)
- **Ending**: Call-to-action or closing thought
- **Metadata**: Category, topic, estimated duration, and creation timestamp

#### Popular Multi-Subreddit Searches

**Conspiracy Theories:**
- Topic: "yeti bigfoot" → Subreddits: "HighStrangeness Cryptozoology bigfoot conspiracy"
- Topic: "ancient aliens pyramids" → Subreddits: "conspiracy AlternativeHistory AncientAliens"
- Topic: "UFO sightings" → Subreddits: "UFOs aliens conspiracy HighStrangeness"

**Today I Learned:**
- Topic: "weird historical facts" → Subreddits: "todayilearned history AskHistorians"
- Topic: "space discoveries" → Subreddits: "space astronomy todayilearned"

**Jokes:**
- Topic: "best puns wordplay" → Subreddits: "dadjokes puns Jokes"

#### Important Notes

- PostCrawl searches can take up to 5 minutes to return results
- Multi-subreddit searches provide more diverse content
- Subreddit names are automatically quoted in the search query
- Scripts are optimized for text-to-speech narration
- Content is kept under 200 words (approximately 60 seconds when spoken)