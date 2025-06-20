# n8n Workflows Collection

A collection of automated workflows for n8n automation platform.

## Files

- [`README.md`](#readme) - This documentation file
- [`workflows/social-media-intelligence-platform-basic-postcrawl-anthropic.json`](#social-media-intelligence-platform) - Social media analysis workflow
- [`workflows/wip-viral-video-postcrawl.json`](#viral-video-creation) - Viral video content creation workflow

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