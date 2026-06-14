# 🤖 AI-Powered Technology Research Analyst

**Author: Palak Rathod**

---

## 📖 Overview

The AI-Powered Technology Research Analyst is a fully automated, scheduled workflow designed to reduce manual effort in discovering, analyzing, and distributing technology news. Built on n8n, this agent automatically aggregates RSS feeds from top tech sources, processes the data through Google Gemini AI, and delivers highly readable summaries along with trending technology insights directly to a Discord channel every morning.

---

## ✨ Key Features

- **Automated Data Aggregation:** Pulls live articles from top tech RSS feeds (TechCrunch, The Verge, Hacker News).
- **AI-Powered Categorization:** Uses Google Gemini to classify each article into categories like AI, Cybersecurity, Cloud, Startups, Programming, and Gadgets.
- **AI Summarization:** Generates concise 3-sentence summaries with an importance score out of 10 for each article.
- **Trending Tech Detection:** Identifies the Top 3 trending technologies from the day's news with reasoning.
- **Automated Distribution:** Pushes the final daily report to Discord via Webhooks.
- **Zero-Touch Scheduling:** Runs autonomously every morning at 9:00 AM daily.

---

## 🛠️ Tech Stack & Concepts

- **n8n:** Visual workflow orchestration and automation.
- **Google Gemini API:** Large Language Model for AI summarization, categorization, and trend detection.
- **RSS Feeds:** Standardized syndication protocols for reliable news ingestion.
- **Discord Webhooks:** For seamless delivery of the final daily report.
- **Prompt Engineering:** Custom prompts designed for research analyst-style output.

---

## 🗺️ Workflow Architecture

The pipeline consists of a linear sequence of nodes:

1. **Schedule Trigger:** Initiates the workflow every morning at 9AM.
2. **RSS Feed Nodes:** Fetches articles from TechCrunch, The Verge, and Hacker News.
3. **Limit Node:** Caps articles to 5 for optimized AI processing.
4. **Google Gemini (Analysis):** Categorizes and summarizes each article with importance score.
5. **Aggregate Node:** Combines all summaries into a single data object.
6. **Google Gemini (Trending):** Identifies Top 3 trending technologies from the day's news.
7. **Discord Webhook:** Delivers the finalized daily report.

![n8n Workflow](n8n-workflow.png)

---

## 📡 Output Preview

The final output is a clean, structured daily tech report delivered directly to Discord, including article summaries by category and a trending technologies section.

![Discord Preview](discord-preview.png)

---

## 📰 News Sources

| Source | RSS URL |
|--------|---------|
| TechCrunch | https://techcrunch.com/feed/ |
| The Verge | https://www.theverge.com/rss/index.xml |
| Hacker News | https://hnrss.org/frontpage |

---

## 🤖 AI Prompts Used

### Article Analysis Prompt

```
You are a technology research analyst.
Title: {{$json.title}}
Content: {{$json.contentSnippet}}
Return:
1. Category
2. 3 sentence summary
3. Importance score out of 10
```

### Trending Technologies Prompt

```
From all articles identify:
Top 3 trending technologies
Explain why they are trending.
```

---

## 🚀 How to Run

1. **Prerequisites:**
   - An active [n8n](https://n8n.io/) instance (Cloud or Self-Hosted)
   - A free [Google Gemini API Key](https://aistudio.google.com/)
   - A Discord Server with permission to create a Webhook

2. **Import Workflow:**
   - Open your n8n workspace, click Add Workflow, and select Import from File
   - Upload the `main.json` file from this repository

3. **Configure Credentials:**
   - Open the Gemini node and input your Gemini API key
   - Open the Discord node and paste your Discord Webhook URL

4. **Customize Feeds:**
   - Edit the RSS Feed nodes to add or swap news sources as needed

5. **Activate:**
   - Toggle the workflow to Active in the top right corner — it will run automatically every morning!

---

## 🏷️ Tags

`n8n` `google-gemini` `rss-feeds` `discord` `automation` `ai-agent` `workflow-automation` `prompt-engineering` `tech-news`
