First you need to create a Slack workflow as follows:
- Automations > Workflows > + New Workflow > Build Workflow
- Start the workflow... > Choose an event > From a webhook
- Set Up Variables > Key: grade > Data type: Text > Done > Continue
- Messages > Send a message to a channel
- Select a channel > choose the channel where you want to send the SecurityScorecard grade
- Add a message > "Current SecurityScorecard grade: Grade " > Insert a variable > {} grade > Save
- Publish the workflow

Then you need to securely store the Slack webhook URL as a GitHub Actions secret:
- Go back to the Automations > Workflows screen, select your workflow and click the `Copy workflow link` button
- Go to the Settings > Secrets and variables > Actions screen on your GitHub repo
- Click the `New Repository secret`
- Give it the name `SLACK_WEBHOOK` and paste the webhook URL you copied from Slack
- Save the secret
- Now copy `securityscorecard-slack-notification.yml` on your repo's `.github/workflows` folder
- Replace `github.com` in `securityscorecard-slack-notification.yml` with the domain of your company
