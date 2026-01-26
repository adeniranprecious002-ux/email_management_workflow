**Email Management Automation Workflow Using n8n**

**📌 Overview**

This project demonstrates an intelligent email management automation system built using **n8n**. The workflow automatically monitors incoming Gmail messages, categorizes them based on content analysis, and routes notifications to appropriate department Slack channels. Customer service inquiries receive immediate automated acknowledgment emails to improve response time perception.

**🛠 Tools & Technologies Used**

- **n8n** - Workflow automation platform
- **Gmail API** - Email monitoring and automated responses (OAuth2)
- **Slack API** - Team notifications and channel routing (OAuth2)
- **Regular Expressions** - Content-based email classification

**🔄 Workflow Logic**

**1\. Email Monitoring**

- Gmail account is polled every minute for new messages
- Incoming emails trigger the automation workflow

**2\. Intelligent Classification**

Email content (subject + snippet) is analyzed using keyword pattern matching and categorized into:

- **Sales** - Keywords: price, quotation, buy, purchase, order
- **Marketing** - Keywords: campaign, promotion, marketing, brand, advertisement
- **Human Resources (HR)** - Keywords: job, application, resume, cv, recruitment, applied
- **Customer Service** - Keywords: complaint, issue, problem, support, refund, not working
- **General (Fallback)** - Unclassified emails requiring manual review

**3\. Automated Notifications**

- Slack notifications sent to department-specific channels:
  - #sales
  - #marketing
  - #hr
  - #customer-support
  - #general (fallback)
- Each notification includes sender, subject, and 150-character summary

**4\. Customer Acknowledgment**

- Customer Service emails automatically trigger acknowledgment response
- Professional email sent to original sender confirming receipt
- Improves customer experience with immediate feedback

**📂 Project Structure**

.

├── workflow/

│ └── email_management_workflow.json # Exported n8n workflow

├── screenshots/ # Execution proof

│ ├── workflow-canvas.png

│ ├── slack-notifications.png

│ └── acknowledgement-email.png

├── docs/

│ └── workflow-report.md # Detailed analysis

├── .gitignore

└── README.md

**🚀 Setup Instructions**

**Prerequisites**

- n8n installed (local or cloud instance)
- Gmail account with API access enabled
- Slack workspace with appropriate channels created

**Required Slack Channels**

Create the following channels in your Slack workspace:

- #sales
- #marketing
- #hr
- #customer-support
- #general

**Installation Steps**

- **Clone the repository**
- git clone &lt;repository-url&gt;
- cd &lt;repository-folder&gt;
- **Import workflow into n8n**
  - Open n8n interface
  - Go to Workflows → Import from File
  - Select workflow/Assignment TS Academy.json
- **Configure Gmail credentials**
  - Add new Gmail OAuth2 credential in n8n
  - Authorize access to your Gmail account
  - Update Gmail Trigger and Gmail Send nodes with your credential
- **Configure Slack credentials**
  - Add new Slack OAuth2 credential in n8n
  - Authorize access to your Slack workspace
  - Update all Slack message nodes with your credential
  - Verify channel IDs match your workspace channels
- **Activate the workflow**
  - Test with sample emails first
  - Monitor execution logs
  - Activate for production use

**✅ Assignment Requirements Covered**

- ✓ Email trigger implemented (Gmail polling every minute)
- ✓ Department categorization logic (4 categories + fallback)
- ✓ Slack notifications per department (5 channels)
- ✓ Customer Service acknowledgement email (automated response)
- ✓ Complete documentation and workflow export

**📊 Workflow Statistics**

- **Total Nodes:** 14
- **Action Nodes:** 7
- **Classification Categories:** 4 + 1 fallback
- **Integrations:** Gmail + Slack
- **Polling Frequency:** Every 1 minute
- **Average Response Time:** < 1 minute

**🔒 Security Notes**

- OAuth2 authentication used for all integrations
- Credential IDs are abstracted (not exposed in workflow JSON)
- Actual tokens and API keys stored securely in n8n credential system
- Never commit .env files or actual credentials to Git

**📸 Screenshots**

See the screenshots/ folder for:

- Complete workflow canvas view
- Slack notification examples for each department
- Customer service acknowledgment email
- Execution logs and test results

**🎯 Future Enhancements**

- Machine learning-based classification for improved accuracy
- Priority/urgency detection
- Multi-language support
- Analytics dashboard for email volume tracking
- Spam detection and sender verification
- Custom response templates per department

**👤 Author**

Adeniran Precious Adebayo

**📝 License**

This project is for educational purposes.

**Status:** ✅ Complete and Ready for Demonstration  
**Last Updated:** January 26, 2026

