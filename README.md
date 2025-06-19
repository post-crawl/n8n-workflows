# n8n Workflows Collection

A collection of automated workflows for n8n automation platform.

## Files

- [`README.md`](#readme) - This documentation file
- [`workflows/social-media-intelligence-platform-basic-postcrawl-anthropic.json`](#social-media-intelligence-platform) - Social media analysis workflow

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