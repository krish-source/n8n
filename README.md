# AI Tech News to X Poster

Automated n8n workflow that researches AI tech news and posts viral content to X (Twitter) every 24 hours.

## Features

- **Automated News Research**: Uses Tavily API to fetch 10 latest AI tech articles
- **AI-Powered Content Generation**: GPT-4 creates viral posts with strategic hooks and hashtags
- **Auto-Posting**: Publishes directly to X/Twitter
- **Post Tracking**: Logs all posts to n8n Data Table
- **Runs Every 24 Hours**: Set-and-forget automation

## Prerequisites

- [n8n](https://n8n.io/) (self-hosted or cloud)
- [Tavily API](https://tavily.com) account (free tier available)
- [OpenAI API](https://platform.openai.com/) key
- [X/Twitter Developer](https://developer.twitter.com/) account with OAuth 2.0 credentials

## Installation

1. **Import Workflow**
   ```
   n8n → Workflows → Import from File → Select AI_Tech_News_X_Poster_CLEAN.json
   ```

2. **Configure Credentials**

   **Tavily API:**
   - Get API key from [tavily.com](https://tavily.com)
   - Replace `YOUR_TAVILY_API_KEY_HERE` in both locations (header + body parameters)

   **X/Twitter OAuth2:**
   - Create app at [developer.twitter.com](https://developer.twitter.com)
   - Configure OAuth 2.0 with callback URL: `https://your-n8n-url/rest/oauth2-credential/callback`
   - Add credential in "Post to X" node
   
   **OpenAI API:**
   - Get API key from [platform.openai.com](https://platform.openai.com)
   - Add credential in "OpenAI Chat Model" node

3. **Create Data Table**
   - "Save Post to Data Table" node will auto-create on first run
   - Or manually create table named "Twitter_posts_DB"

## Configuration

### Customize Post Generation

Edit the **AI Agent** node prompts to adjust:
- Writing style and tone
- Hook patterns
- Hashtag strategy
- Content focus

### Change Schedule

Edit **Every 24 Hours** node:
- Default: Runs daily
- Adjust interval in hours (e.g., 12 for twice daily)

### Modify News Search

Edit **Tavily News Search** body parameters:
- `query`: Change topic (e.g., "machine learning breakthroughs")
- `max_results`: Adjust article count (1-10)
- `search_depth`: "basic" or "advanced"

## Usage

**Manual Test:**
```
Click "Execute Workflow" to test before activating
```

**Activate:**
```
Toggle workflow to "Active" for automatic 24-hour schedule
```

**Monitor:**
- Check Data Table for post history
- View workflow executions for logs

## Tech Stack

- **n8n**: Workflow automation
- **Tavily API**: News aggregation
- **OpenAI GPT-4**: Content generation
- **X/Twitter API v2**: Social media posting

## Cost Estimate

- Tavily: Free (1000 searches/month)
- OpenAI: ~$0.001 per post (GPT-4o)
- X/Twitter: Free tier (50 posts/month)

**Total: ~$0.03/month for 30 posts**

## Notes

- First run may take 60-90 seconds (news research + AI generation)
- Posts are under 280 characters with 2-3 hashtags
- Data Table tracks all posts for analytics

## License

MIT

## Contributing

Issues and PRs welcome!
