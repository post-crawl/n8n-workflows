# n8n Workflows Collection

A collection of automated workflows for n8n automation platform.

## Files

- [`README.md`](#readme) - This documentation file
- [`workflows/social-media-intelligence-platform-basic-postcrawl-anthropic.json`](#social-media-intelligence-platform) - Social media analysis workflow
- [`workflows/wip-viral-video-postcrawl.json`](#viral-video-creation) - Viral video content creation workflow
- [`workflows/viral-video-sample-template.json`](#ai-automated-short-form-video-generator) - Complete AI-powered video production template
- [`workflows/youtube-script-generator.json`](#youtube-script-generator) - Reddit-based YouTube Shorts script generator

## Workflows

### Social Media Intelligence Platform

**File:** [`workflows/social-media-intelligence-platform-basic-postcrawl-anthropic.json`](./workflows/social-media-intelligence-platform-basic-postcrawl-anthropic.json)

An automated workflow that analyzes social media posts using PostCrawl API and generates comprehensive PR strategy reports using Anthropic AI models.

#### What It Does

This workflow automatically:
- Searches for posts on Reddit and TikTok based on configured topics
- Extracts post content, engagement metrics, and comments
- Processes and filters comments to optimize AI analysis
- Performs three-stage AI analysis using Anthropic Claude models
- Generates comprehensive reports with PR opportunities and strategic insights

#### How It Works

1. **Schedule Trigger**: Runs weekly on Mondays at 6 AM
2. **Topic Processing**: Splits configured topics for parallel processing  
3. **Data Collection**: Uses PostCrawl API to search and extract social media posts
4. **Comment Processing**: Filters and limits comments (max 3, 50 chars each) to optimize AI processing
5. **AI Analysis**: Three-stage analysis using Anthropic Claude:
   - Comments sentiment and engagement analysis
   - Content evaluation and narrative opportunities  
   - PR strategy report generation
6. **Final Report**: Combines all analysis into a comprehensive report

#### Prerequisites

1. **n8n instance** - Running n8n automation platform
2. **PostCrawl API account** - For social media data extraction
3. **Anthropic API account** - For AI-powered analysis

#### Setup Instructions

1. **Import the workflow**:
   - Open your n8n instance
   - Go to Workflows → Import from file
   - Select `social-media-intelligence-platform-basic-postcrawl-anthropic.json`

2. **Configure authentication**:
   - **PostCrawl API Node**: Update the authentication secret with your PostCrawl Bearer token
   - **Anthropic Chat Model Nodes**: Add your Anthropic API key to all three Anthropic nodes:
     - Anthropic Chat Model 1 (Comments Analysis)
     - Anthropic Chat Model 2 (Content Analysis)  
     - Anthropic Chat Model 3 (Generate Stories Report)

3. **Configure topics**:
   - Edit the "Set Configuration" node
   - Modify the `Topics` field with your research topics (default: "mcp\nagents")
   - Adjust `Min_Engagement_Score` and `Max_Results_Per_Topic` as needed

#### Output Format

The workflow generates a structured JSON output containing:

- **Post Details**: Platform, engagement metrics, author info
- **Comments Analysis**: Sentiment, engagement patterns, audience insights
- **Content Analysis**: Quality assessment, viral factors, competitive landscape
- **PR Strategy Report**: Immediate opportunities, strategic recommendations, execution roadmap
- **Final Report**: Combined markdown report with all analysis

#### Customization Options

- **Topics**: Modify research topics in "Set Configuration" node
- **Comment Limits**: Adjust `MAX_COMMENTS` and `MAX_COMMENT_LENGTH` in "Process Comments" node
- **AI Models**: Change model settings in Anthropic Chat Model nodes
- **Schedule**: Update trigger timing in "Schedule Trigger" node

#### Token Optimization

The workflow is optimized for Anthropic's token limits:
- Comments limited to 3 most engaging (50 characters each)
- AI models configured with 4,000 token limit
- Smart data filtering to prevent timeouts

#### Troubleshooting

- **Token limit errors**: Reduce comment limits further in "Process Comments" node
- **API authentication errors**: Verify PostCrawl Bearer token and Anthropic API keys are correctly configured
- **No results**: Check topic keywords and engagement thresholds in configuration

### Viral Video Creation Workflow

**File:** [`workflows/wip-viral-video-postcrawl.json`](./workflows/wip-viral-video-postcrawl.json)

An automated viral video content creation workflow that generates complete video packages using PostCrawl API and OpenAI services for content generation, audio narration, and image creation.

#### What It Does

This workflow automatically:
- Generates viral-ready topics from predefined categories
- Searches for trending content using PostCrawl API
- Creates engaging video scripts using OpenAI GPT-4
- Generates audio narration with text-to-speech
- Creates relevant images for video content
- Produces marketing copy and social media assets
- Prepares complete video packages ready for production

#### How It Works

1. **Topic Generation**: Randomly selects from viral topic categories (space, history, science, etc.)
2. **Content Research**: Uses PostCrawl to extract trending discussions from Reddit
3. **Content Processing**: Analyzes and structures viral content with engagement metrics
4. **Script Creation**: Generates 30-45 second video scripts optimized for social media
5. **Asset Generation**: Creates audio narration and visual content using OpenAI
6. **Video Preparation**: Merges all assets and prepares FFmpeg commands for video creation
7. **Marketing Assets**: Generates platform-specific copy for YouTube, TikTok, and Instagram

#### Prerequisites

1. **n8n instance** - Running n8n automation platform
2. **PostCrawl API account** - For social media content extraction
3. **OpenAI API account** - For script generation, image creation, and audio synthesis

#### Output Format

The workflow produces a comprehensive video package containing:
- **Video Script**: Engaging 30-45 second narration
- **Audio File**: Professional voice narration (MP3 format)
- **Images**: Content-relevant visuals for video production
- **Marketing Copy**: Platform-specific titles and descriptions
- **Production Data**: FFmpeg commands and technical specifications
- **Metadata**: Hashtags, topics, and engagement metrics

#### Current Status

This workflow is currently in development (WIP - Work in Progress). Video generation functionality is being implemented and will be added in future updates.

### AI Automated Short-Form Video Generator

**File:** [`workflows/viral-video-sample-template.json`](./workflows/viral-video-sample-template.json)

A comprehensive AI-powered workflow template that automates the entire process of creating short-form videos for TikTok, YouTube Shorts, and Instagram Reels from ideation to publishing.

#### Who Is This For?

Content creators, digital marketers, and social media managers who want to automate the creation of short-form videos for platforms like TikTok, YouTube Shorts, and Instagram Reels without extensive video editing skills.

#### What Problem Does This Solve?

Creating engaging short-form videos consistently is time-consuming and requires multiple tools and skills. This workflow automates the entire process from ideation to publishing, significantly reducing the manual effort needed while maintaining content quality.

#### What This Workflow Does

This all-in-one solution transforms ideas into fully produced short-form videos through a 5-step process:

1. **Generate video captions** from ideas stored in a Google Sheet
2. **Create AI-generated images** using Flux and the OpenAI API
3. **Convert images to videos** using Kling's API
4. **Add voice-overs** to your content with Eleven Labs
5. **Complete the video production** with Creatomate by adding templates, transitions, and combining all elements

The workflow handles everything from sourcing content ideas to rendering the final video, and even notifies you on Discord when videos are ready.

#### Prerequisites

- **n8n installation** (tested on version 1.81.4)
- **OpenAI API Key** (free trial credits available)
- **PiAPI** (free trial credits available)
- **Eleven Labs** (free account)
- **Creatomate API Key** (free trial credits available)
- **Google Sheets API** enabled in Google Cloud Console
- **Google Drive API** enabled in Google Cloud Console
- **OAuth 2.0 Client ID and Client Secret** from your Google Cloud Console Credentials

#### How To Customize This Workflow

- Adjust the Google Sheet structure to include additional data like video length, duration, style, etc.
- Modify the prompt templates for each AI service to match your brand voice and content style
- Update the Creatomate template to reflect your visual branding
- Configure notification preferences in Discord to manage your workflow

This workflow combines multiple AI technologies to create a seamless content production pipeline, saving you hours of work per video and allowing you to focus on strategy rather than production.

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