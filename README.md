# pull_request_auto_labeler
Automatically label Github pull requests based on elements of the PR title. Expects Jira style ticket code(PROJ-100) in PR title

This labeler does the following:
 - get all open Pull Requests for all the repositories for an organization/user
 - check each PR to see if it has any matching a Jira style ticket code in the title (PROJ-100)
 - apply a label to the Pull Request matching the uppercase version of the project codes from the title (PROJ)

## Setup
Set the following enviornment vars:
- GITHUB_API_TOKEN : A Github API Token which has access to read the repositories you want and modify pull requests. If you don't have one you see the guide [here](https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line)
- ORGANIZATION the name of the github organization/username that you want to check PRs for.

## Running from command line
`python auto_labeler.py`

## Running as a Cron on AWS Lambda

For convenience I've included setup instructions to run this as a cron using aws lambda made easy by the [serverless](https://serverless.com/framework/docs/) toolkit. If you haven't used serverless, I hava a getting started with serverless guide [here](https://gist.github.com/markddavidoff/0bbfcdfc29bbbdedc8b57e062987b480) 

### Setup your lambda run frequency
- See the notes in the `serverless.yml` file under `functions>pull_request_auto_labeler>events>schedule`.

### Deploy to AWS
`sls deploy`
