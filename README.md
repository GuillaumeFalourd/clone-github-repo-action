# Clone Github Repository Action

[![Public workflows that use this action.](https://img.shields.io/endpoint?url=https%3A%2F%2Fapi-endbug.vercel.app%2Fapi%2Fgithub-actions%2Fused-by%3Faction%3DGuillaumeFalourd%2Fclone-github-repo-action%26badge%3Dtrue)](https://github.com/search?o=desc&q=GuillaumeFalourd+clone-github-repo-action+path%3A.github%2Fworkflows+language%3AYAML&s=&type=Code) [![Clone Public Repository Workflow](https://github.com/GuillaumeFalourd/clone-github-repo-action/actions/workflows/public-repo.yml/badge.svg)](https://github.com/GuillaumeFalourd/clone-github-repo-action/actions/workflows/public-repo.yml) [![Clone Private Repository Workflow](https://github.com/GuillaumeFalourd/clone-github-repo-action/actions/workflows/private-repo.yml/badge.svg)](https://github.com/GuillaumeFalourd/clone-github-repo-action/actions/workflows/private-repo.yml)

![Title](https://user-images.githubusercontent.com/22433243/117468930-900a9800-af2b-11eb-9bd4-0aa16465f952.png)

Github Action to clone a **public** or **private** Github repository and access its content on others repositories' workflows.

## What changed with the action `v2` ?

This action `v2` is using a **composite action** to be compatible with all operating systems (the `v1` was using a **Dockerfile** that was only compatible with `ubuntu-*` runners).

### What changed with the action `v2.1` ?

You now have a new input parameter called depth, which is optional and has an empty default value. If you specify a depth value when using the action, it will be passed as the value for the **--depth** parameter of the git clone command. Otherwise, the clone will be done with the default depth, which is the full history.

## How to use this action?

Create a new `.yml` file on your `.github/workflows` directory.

Field | Mandatory | Observation
------------ | ------------  | -------------
**owner** | YES | Ex: `octocat`
**repository** | YES | Ex: `clone-github-repo-action` | 
**branch** | NO | 'main' Ex: clone branch main (default) if not defined arg
**depth** | NO | 1 `Ex: most recent commit`
**access-token** | NO | [How to create a PAT](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)

You can use one of those as reference:

- [Clone Public Repo Workflow](https://github.com/GuillaumeFalourd/clone-github-repo-action/blob/main/.github/workflows/public-repo.yml)
- [Clone Private Repo Workflow](https://github.com/GuillaumeFalourd/clone-github-repo-action/blob/main/.github/workflows/private-repo.yml)

### For a public repository (with depth)

```bash
- name: Clone GuillaumeFalourd/poc-github-actions PUBLIC repository
  uses: GuillaumeFalourd/clone-github-repo-action@v2.1
  with:
    depth: 1
    branch: 'main'
    owner: 'GuillaumeFalourd'
    repository: 'poc-github-actions'
```

### For a private repository

To use this action to clone a `PRIVATE` repository the Github User/Admin has access to, it's necessary to create a [PERSONAL ACCESS TOKEN](https://github.com/settings/tokens) with `REPOSITORY` scopes.

```bash
- name: Clone GuillaumeFalourd/formulas-training PRIVATE repository
  uses: GuillaumeFalourd/clone-github-repo-action@v2.1
  with:
    owner: 'GuillaumeFalourd'
    repository: 'formulas-training'
    access-token: ${{ secrets.ACCESS_TOKEN }}
```

### Access repository content

After using this action in your workflow, you can use the following command to access the cloned repository content:

```bash
cd <repository-name>
```

#### Step Example

```bash
- name: Access cloned repository content
  run: |
    cd <repository-name>
    ls -la
```

## Licensed

☞ This repository uses the [Apache License 2.0](https://github.com/GuillaumeFalourd/aws-cliaction/blob/main/LICENSE)

## Contributing

☞ [Guidelines](https://github.com/GuillaumeFalourd/clone-github-repo-action/blob/main/CONTRIBUTING.md)

<a href="https://github.com/GuillaumeFalourd/clone-github-repo-action/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=GuillaumeFalourd/clone-github-repo-action" />
</a>

(Made with [contributors-img](https://contrib.rocks))
