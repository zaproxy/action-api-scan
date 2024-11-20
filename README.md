# Action API Scan

A GitHub Action for running the ZAP [API scan](https://www.zaproxy.org/docs/docker/api-scan/) to perform
Dynamic Application Security Testing (DAST). 
 
**WARNING** this action will perform attacks on the target API.
You should only scan targets that you have permission to test.
You should also check with your hosting company and any other services such as CDNs that may be affected before running this action.

## Inputs

### `target`

**Required** target API definition, OpenAPI or SOAP, local file or URL, e.g. https://www.example.com/openapi.json
or target endpoint URL, GraphQL, e.g. https://www.example.com/graphql

### `format`

**Optional** The format of the defintion, `openapi`, `soap`, or `graphql`. Default is `openapi`.

### `docker_name`

**Optional** The name of the Docker image to be executed. By default the action runs the stable version of ZAP. But you can
configure the parameter to use the weekly builds.

### `rules_file_name`

**Optional** You can also specify a relative path to the rules file to ignore any alerts from the ZAP scan. Make sure to create
the rules file inside the relevant repository. The following shows a sample rules file configuration.
Make sure to checkout the repository (actions/checkout@v2) to provide the ZAP rules to the scan action.

```tsv
10011	IGNORE	(Cookie Without Secure Flag)
10015	IGNORE	(Incomplete or No Cache-control and Pragma HTTP Header Set)
```

### `cmd_options`

**Optional** Additional command lines options for the scan script

### `allow_issue_writing`

**Optional** By default the action will file the report to the GitHub issue using the `issue_title` input.
Set this to false if you don't want the issue to be created or updated.

### `issue_title`

**Optional** The title for the GitHub issue to be created.

### `token`

**Optional** ZAP action uses the default action token provided by GitHub to create and update the issue for the api scan.
You do not have to create a dedicated token. Make sure to use the GitHub's default action token when running the action(`secrets.GITHUB_TOKEN`).

### `fail_action`

**Optional** By default ZAP Docker container will fail with an [exit code](https://github.com/zaproxy/zaproxy/blob/7abbd57f6894c2abf4f1ed00fb95e99c34ef2e28/docker/zap-api-scan.py#L35),
if it identifies any alerts. Set this option to `true` if you want to fail the status of the GitHub Scan if ZAP identifies any alerts during the scan.

### `artifact_name`

**Optional** By default the action will attach the report to the build with the name `zap_scan`. Set this to a different string to name it something else. Consult [GitHub's documentation](https://github.com/actions/toolkit/blob/main/packages/artifact/docs/additional-information.md#non-supported-characters) for which artifact names are allowed.

## Environment variables

If set, the following [ZAP authentication environment variables](https://www.zaproxy.org/docs/authentication/handling-auth-yourself/#authentication-env-vars)
will be copied into the docker container:

- `ZAP_AUTH_HEADER_VALUE`
- `ZAP_AUTH_HEADER`
- `ZAP_AUTH_HEADER_SITE`

## Example usage

** Basic **

```
steps:
  - name: ZAP Scan
    uses: zaproxy/action-api-scan@v0.9.0
    with:
      target: 'https://www.zaproxy.org/'
```

** Advanced **

```
on: [push]

jobs:
  zap_scan:
    runs-on: ubuntu-latest
    name: Scan the webapplication
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          ref: master

      - name: ZAP Scan
        uses: zaproxy/action-api-scan@v0.9.0
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          docker_name: 'ghcr.io/zaproxy/zaproxy:stable'
          format: openapi
          target: 'https://www.zaproxy.org/'
          rules_file_name: '.zap/rules.tsv'
          cmd_options: '-a'
```
