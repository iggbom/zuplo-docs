---
title: Deployment Commands
---

```bash
zup --help
zup <command>

Commands:
  zup delete    Deletes the zup at the URL
  zup deploy    Deploys current Git branch of the current directory
  zup list      Lists all deployed zups
  zup test      Runs the tests under /tests against an endpoint
```

Use these commands to help your manage your deployed zups. They must be run from
the root of your Zuplo project. And, they assume that you already have Git setup
for the project.

See concrete end-to-end examples of how to use this in your CI/CD job at
[Custom CI/CD](../articles/custom-ci-cd.md).

## Common Use Cases

The following examples assume that you are passing in your --api-key either as
an argument or through the `ZUPLO_API_KEY` environment variable.

### Deploying your Gateway

```
# The following will use the current Git branch as the name of the environment
git checkout -b my-new-branch
zup deploy
```

```
# If you do not wish to use the current Git branch as the name of the
# environment, you can specify one using --environment
zup deploy --environment my-env-name
```

```
# If you have configured your remote origin differently from portal.zuplo.com,
# you can still force it to deploy. Be aware that this could make merging changes impossible if the remote do not share a common ancestor.
git remote -v

zup deploy --no-verify-remote
```
