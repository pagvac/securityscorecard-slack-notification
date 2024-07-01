First you need to create a Slack workflow as follows:
1. `Automations` > `Workflows` > `+ New Workflow` > `Build Workflow`
2. `Start the workflow...` > `Choose an event` > `From a webhook`
3. `Set Up Variables` > `Key: grade` > `Data type: Text` > `Done` > `Continue`
4. `Messages` > `Send a message to a channel`
5. `Select a channel` > choose the channel where you want to send the SecurityScorecard grade
6. `Add a message` > "Current SecurityScorecard grade: Grade " > `Insert a variable` > `{} grade` > `Save`
7. Publish the workflow

Then you need to securely store the Slack webhook URL as a GitHub Actions secret:
1. Go back to the `Automations > Workflows` screen, select your workflow and click the `Copy workflow link` button
2. Go to the `Settings` > `Secrets and variables` > `Actions` screen on your GitHub repo
3. Click the `New Repository secret`
4. Give it the name `SLACK_WEBHOOK` and paste the webhook URL you copied from Slack
5. Save the secret
6. Now copy `securityscorecard-slack-notification.yml` to your repo's `.github/workflows` folder
7. Replace `github.com` in `securityscorecard-slack-notification.yml` with the domain of your company

The SecurityScorecard grade of the domain you specified will be posted to the Slack channel you chose above on the first Monday of each month.
