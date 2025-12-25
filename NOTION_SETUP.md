# Notion Hunt Tracker Setup Guide

## Quick Setup

### Step 1: Create the Hunt Tracker Database

1. Open Notion
2. Create a new page called "Hunt Tracker"
3. Create a database (Table view)
4. Share the page with your Claude Code integration:
   - Click "..." → "Add connections" → Select your integration

### Step 2: Database Properties

Copy this structure into your Notion database:

#### Required Properties

| Property Name | Type | Options/Config |
|--------------|------|----------------|
| **Company** | Title | (default) |
| **Role** | Text | |
| **Status** | Select | Applied, Screening, Interview, Offer, Rejected, Withdrawn |
| **Application Date** | Date | |
| **Platform** | Select | LinkedIn, Direct, AngelList, YC Jobs, Otta, Cord, Referral |
| **Match Score** | Number | 0-100% |
| **Visa Sponsorship** | Checkbox | |
| **Remote** | Select | Full Remote, Hybrid, On-site |
| **Salary Range** | Text | e.g., "$120k-$180k" |
| **Location** | Text | |
| **Job URL** | URL | |

#### Optional Properties

| Property Name | Type | Options/Config |
|--------------|------|----------------|
| **Recruiter Name** | Text | |
| **Recruiter Email** | Email | |
| **Interview Stages** | Multi-select | Phone Screen, Technical, System Design, Behavioral, Team Fit, Final |
| **Follow-up Date** | Date | |
| **Notes** | Text (Long) | |
| **Referral Source** | Text | |
| **Priority** | Select | High, Medium, Low |
| **Response Time** | Number | Days to hear back |
| **Tech Stack** | Multi-select | Python, ML, AI, Cloud, etc. |

### Step 3: Create Views

#### View 1: Active Applications (Default)
- **Filter**: Status is not "Rejected" and Status is not "Withdrawn"
- **Sort**: Application Date (Newest first)
- **Group by**: Status

#### View 2: High Priority
- **Filter**: Priority is "High" AND Status is not "Rejected"
- **Sort**: Follow-up Date (Ascending)

#### View 3: Interview Pipeline
- **Filter**: Status is "Interview"
- **Sort**: Follow-up Date (Ascending)
- **Group by**: Interview Stages

#### View 4: Awaiting Response
- **Filter**: Status is "Applied" OR Status is "Screening"
- **Sort**: Application Date (Oldest first)
- **Properties**: Show Response Time

#### View 5: Visa Sponsors Only
- **Filter**: Visa Sponsorship is checked
- **Sort**: Match Score (Descending)

#### View 6: Remote Roles
- **Filter**: Remote is "Full Remote"
- **Sort**: Application Date (Newest first)

### Step 4: Add Sample Entry

Add this sample entry to test:

```
Company: Anthropic
Role: ML Engineer - AI Safety
Status: Not Applied
Application Date: [Today]
Platform: Direct
Match Score: 95
Visa Sponsorship: ✓
Remote: Full Remote
Salary Range: $150k-$250k
Location: San Francisco (Remote OK)
Job URL: https://www.anthropic.com/careers
Priority: High
Tech Stack: Python, ML, LLMs, PyTorch
Notes: Perfect fit - LLM experience, safety focus, research background
```

## Database Template (CSV Import)

Save this as `hunt-tracker-template.csv` and import:

```csv
Company,Role,Status,Application Date,Platform,Match Score,Visa Sponsorship,Remote,Salary Range,Location,Priority
Anthropic,ML Engineer,Not Applied,2025-12-25,Direct,95,Yes,Full Remote,$150k-$250k,SF (Remote),High
Hugging Face,ML Engineer,Not Applied,2025-12-25,Direct,90,Yes,Full Remote,$130k-$200k,Remote,High
Stripe,ML Engineer - Fraud,Not Applied,2025-12-25,Direct,90,Yes,Hybrid,$140k-$220k,SF/NYC/Remote,High
Databricks,ML Platform Engineer,Not Applied,2025-12-25,Direct,85,Yes,Full Remote,$150k-$230k,Remote,High
Google,ML Engineer,Not Applied,2025-12-25,Direct,80,Yes,Hybrid,$150k-$250k,MTV/NYC,Medium
OpenAI,Applied ML Engineer,Not Applied,2025-12-25,Direct,85,Yes,Hybrid,$200k-$350k,SF,High
Meta,ML Engineer - CV,Not Applied,2025-12-25,Direct,75,Yes,Hybrid,$150k-$250k,Menlo Park,Medium
Amazon,ML Engineer - AWS,Not Applied,2025-12-25,Direct,75,Yes,Varies,$130k-$210k,Seattle/Remote,Medium
Microsoft,AI Engineer - Azure,Not Applied,2025-12-25,Direct,75,Yes,Hybrid,$120k-$200k,Redmond/Remote,Medium
Notion,Full-stack ML Engineer,Not Applied,2025-12-25,Direct,80,Yes,Hybrid,$130k-$210k,SF/NYC,High
```

## Formulas (Advanced)

### Days Since Application
```
dateBetween(now(), prop("Application Date"), "days")
```

### Status Emoji
```
if(prop("Status") == "Offer", "🎉",
  if(prop("Status") == "Interview", "💼",
    if(prop("Status") == "Screening", "📞",
      if(prop("Status") == "Applied", "📧",
        if(prop("Status") == "Rejected", "❌", "⏸️")))))
```

### Match Category
```
if(prop("Match Score") >= 90, "🎯 Perfect Fit",
  if(prop("Match Score") >= 75, "⭐ Strong Fit",
    if(prop("Match Score") >= 60, "🔄 Good Fit", "❓ Uncertain")))
```

## Automation Ideas

### Using Notion API (via Claude Code):

1. **Auto-add jobs from links**:
   - Paste job URL
   - Claude extracts company, role, requirements
   - Auto-fills database entry

2. **Resume match scoring**:
   - Claude analyzes job description
   - Compares with your resume
   - Assigns match score

3. **Application tracking**:
   - Monitors email for responses
   - Updates status automatically
   - Sets follow-up reminders

4. **Weekly reports**:
   - Applications sent this week
   - Pending responses
   - Upcoming interviews
   - Success rate

## Integration with Claude Code

### Example Commands:

```
> Add this job to Hunt Tracker: [paste job URL]
> What's my application status with Anthropic?
> Show me all interviews scheduled this week
> Which companies haven't responded in 2+ weeks?
> Update Stripe status to "Phone Screen" with interview on Friday
> Generate weekly application report
> Find jobs matching my ML experience over 85% score
> Remind me to follow up on applications over 1 week old
```

## Best Practices

### Daily
- [ ] Add new applications immediately
- [ ] Update statuses after responses
- [ ] Check follow-up dates

### Weekly
- [ ] Review "Awaiting Response" view
- [ ] Follow up on applications >1 week old
- [ ] Plan next week's applications
- [ ] Update interview prep notes

### Monthly
- [ ] Analyze success rate by platform
- [ ] Review match score accuracy
- [ ] Update strategy based on responses
- [ ] Archive old rejections

## Privacy & Sharing

**⚠️ Important**:
- The Hunt Tracker contains sensitive job search data
- Do NOT share the page publicly
- Only connect with trusted integrations
- Consider using Notion's private pages feature
- Back up data regularly

## Next Steps

1. [ ] Create the database in Notion
2. [ ] Import the template CSV
3. [ ] Set up the 6 views
4. [ ] Add your integration connection
5. [ ] Test with Claude Code
6. [ ] Start adding real job applications

---

Need help? Ask Claude Code:
```
> Help me set up my Hunt Tracker in Notion
> Create a new job entry for [Company]
> Show me my application pipeline
```
