## 5. Verify completion

[](https://github.com/MattersWorld/SEIR-Foundations/blob/main/module1/lesson3_Jira/jira_install.md#5-verify-completion)

- [x]  I created my own Atlassian account.
- [x]  I can open my Jira Cloud site.
- [x]  I selected or confirmed the Free plan.
- [x]  I created the Balerica AI Incident Management project.
- [x]  I know my **actual** project key.
- [x]  I created and opened a manual test incident.
- [x]  I saved the site URL, email, project key, and test issue key privately.
- [x]  I have **not** shared any passwords or API tokens.





## BAM_5.5
The flow begins with the EC2 instance. I ran incident.py --test which created a ticket in my Balerica Bank Jira. From there, the issue key and url was passed to slack.py by incident.py. Jira is called before slack because it needs to create a ticket and Url for the slack alert to direct you to. The Jira ticket is detailed and in a workplace, they would likely use it due to having story points available. Slack is more of a notification app while Jira holds the rundown of the issue. I verified Jira by checking the new task that was made. It was called BAI-9 and inside of it was the incident report. I verified slack by checking the alert channel for the corresponding message. I checked the time it was posted and the URL that it provided, which bought me to BAI-9.