---
layout: classic-docs
title: "Testing Config Locally"
description: "Testing Config Locally"
---

Use the instructions in the following video to test your configuration file locally as you get started with more complex [example configuration files]({{ site.baseurl }}/2.0/example-configs/), [database configuration examples]({{ site.baseurl }}/2.0/postgres-config/), [sample `config.yml` template files]({{ site.baseurl }}/2.0/sample-config/), and [tutorials]({{ site.baseurl }}/2.0/tutorials/).

### Video: Test Your Config File Locally

<div class="video-wrapper">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/HB5DehCufG0" frameborder="0" allowfullscreen></iframe>
</div>
## Steps
1. Add a shell script in your `.circleci` directory, for example, `run-build-locally.sh`.
2. [Create a personal API token]({{ site.baseurl }}/2.0/managing-api-tokens/#creating-a-personal-api-token).
3. Export the token on the command line `export CIRCLE_TOKEN=<token-from-step-above>`.
4. Gather the following information:
  - Commit hash from which to build
  - Username
  - Source for project
  - Project name
  - Branch from which to build
5. Add those values into your shell script.

```bash
#!/usr/bin/env bash
curl --user ${CIRCLE_TOKEN}: \
    --request POST \
    --form revision=<commit hash>\
    --form config=@config.yml \
    --form notify=false \
        https://circleci.com/api/v1.1/project/<source, eg. github>/<user name>/<project name>/tree/<branch name>
```

Now you can run the shell script and debug your `config.yml` file without having to push through the repo.
