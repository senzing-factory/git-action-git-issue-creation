# Git Action Git Issue Creation

Git Action to create an Issue on a GitHub Repo. This action can be used to create an issue when a build fails in a Git Action workflow. 

## Usage 

This action can be used after any other action. Below is simple example on using it:

1\. Create a `.github/workflows/git-issue-creation.yml`

2\. Add the following properties to `git-issue-creation.yml` file

```yaml
on: push
name: Git Creation Demo
jobs:
  gitIssueCreation:
    name: Git Creation Demo
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Git Creation Demo
        uses: senzing/git-action-git-issue-creation@1.0.0
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          GITHUB_COMMIT_SHA: ${{ github.sha }}
          GITHUB_REPO_OWNER: 'Senzing'
          GITHUB_REPO_NAME: 'git-action-github-issue-creation'
          GITHUB_ISSUE_TITLE: 'Demo''ing Git Issue Creation'
          GITHUB_ISSUE_BODY: 'Demo''ing Git Issue Creation'
```

Go [here](deployment/git-actions/template_github_issue_creation.yml) for a template yml with all environment variables.

## Environment Variables
These are the environment variables that can be set to pass in additional information about the Git Action.

<table>
    <tr>
        <td>
            Variable Name
        </td>
        <td>
            Required
        </td>
        <td>
            Description
        </td>
    </tr>
    <tr>
        <td>
            GITHUB_TOKEN
        </td>
        <td>
            Yes
        </td>
        <td>
            The GitHub access token used by Git Actions workflow. Can use the native token generated by Git Actions or create a custom secret.
        </td>
    </tr>
    <tr>
        <td>
            GITHUB_SHA
        </td>
        <td>
            Yes
        </td>
        <td>
            The commit SHA associated to running the Git Action workflow.
        </td>
    </tr>
    <tr>
        <td>
            GITHUB_OWNER
        </td>
        <td>
            Yes
        </td>
        <td>
            The owner of the repo which is normally seen in the URI as a prefix to the repo.
        </td>
    </tr>
    <tr>
        <td>
            GITHUB_REPOSITORY
        </td>
        <td>
            Yes
        </td>
        <td>
            The name of the repository.
        </td>
    </tr>
    <tr>
        <td>
            GITHUB_ISSUE_TITLE
        </td>
        <td>
            Yes
        </td>
        <td>
            Title of the issue to be created.
        </td>
    </tr>
    <tr>
        <td>
            GITHUB_ISSUE_BODY
        </td>
        <td>
            Yes
        </td>
        <td>
            Body of the issue to be created.
        </td>
    </tr>
</table>

## Reference
* [Using environment variables](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/using-environment-variables) lists the default environment variables set in Git Actions.
* [Authenticating with the GITHUB_TOKEN](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/authenticating-with-the-github_token)

## License
[GPLv3](LICENSE)