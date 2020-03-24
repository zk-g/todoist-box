<p align="center">
  <img width="400" src="screenshot.png">
  <h3 align="center">todoist-box</h3>
  <p align="center">Update a pinned gist to contain your Todoist stats</p>
</p>

---

> 📌✨ For more pinned-gist projects like this one, check out: https://github.com/matchai/awesome-pinned-gists

## Setup

### Prep work

1. Create a new public GitHub Gist (https://gist.github.com/)
1. Create a token with the `gist` scope and copy it. (https://github.com/settings/tokens/new)
1. Create a Todoist account (https://todoist.com/users/showregister)
1. In your account settings, copy the existing Todoist API Token (https://beta.todoist.com/prefs/integrations)

### Project setup

1. Create a Repo in GitHub (https://github.com/new)
1. Go to https://github.com/yohix/todoist-box/actions/new
1. Click Set up a workflow yourself
1. Overwrite the file with below content

```yml
name: Schedule
on:
  schedule:
    - cron: "0 * * * *"
  push:
    branches: master
jobs:
  update-gist:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Update gist
        uses: yohix/todoist-box@master
        env:
          GH_TOKEN: ${{ secrets.GH_TOKEN }}
          GIST_ID: ${{ secrets.GIST_ID }}
          TODOIST_API_KEY: ${{ secrets.TODOIST_API_KEY }}
```
5. Go to Secrets (https://github.com/username/reponame/settings/secrets)
6. Add `GH_TOKEN`, `GIST_ID` and `TODOIST_API_KEY` generated in above steps

## License

MIT © [Yohix](LICENSE)
