First you need to create a Slack workflow as follows:
1. `Automations` > `Workflows` > `+ New Workflow` > `Build Workflow`
2. Name the workflow `SecurityScorecard Slack notification`
3. `Start the workflow...` > `Choose an event` > `From a webhook`
4. `Set Up Variables`
5.  Key: `grade` > Data type: `Text`
6.  Key: `domain` > Data type: `Text`
7. `Done` > `Continue`
8. Right-hand menu: `Messages` > `Send a message to a channel`
9. `Select a channel` > choose the channel where you want to send the SecurityScorecard grade
10. `Add a message` > `Current SecurityScorecard for ` > `Insert a variable` > Select `domain` > `: Grade ` > `Insert a variable` > Select `grade` > `Save`
11. Click `Finish Up` button to publish the workflow

Then you need to securely store the Slack webhook URL as a GitHub Actions secret:
1. Go back to the `... More` > `Automations` > `Workflows` > `Managed by you` screen
2. Click `SecurityScorecard Slack notification` then `Copy workflow link` button
3. Go to the `Settings` > `Secrets and variables` > `Actions` screen on your GitHub repo
4. Click the `New Repository secret` button
5. Give it the name `SLACK_WEBHOOK` and paste the webhook URL you copied from Slack
6. Save the secret
7. Now copy `securityscorecard-slack-notification.yml` to your repo's `.github/workflows` folder
8. Replace `github.com` in `securityscorecard-slack-notification.yml` with the domain of your company
9. Commit the changes

The SecurityScorecard grade of the domain you specified will be posted to the Slack channel you chose above on the first Monday of each month.
