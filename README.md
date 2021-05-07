# Clone Github Repository Action

[![Clone Public Repository](https://github.com/GuillaumeFalourd/clone-github-repo-action/actions/workflows/public-repo.yml/badge.svg)](https://github.com/GuillaumeFalourd/clone-github-repo-action/actions/workflows/public-repo.yml)

[![Clone Private Repository](https://github.com/GuillaumeFalourd/clone-github-repo-action/actions/workflows/private-repo.yml/badge.svg)](https://github.com/GuillaumeFalourd/clone-github-repo-action/actions/workflows/private-repo.yml)

![Title](https://user-images.githubusercontent.com/22433243/117468930-900a9800-af2b-11eb-9bd4-0aa16465f952.png)

Github Action to clone a public or private Github repository and access its content on other workflows.

## How to use this action?

To use this action to clone a `PRIVATE` repository, you need to create a [PERSONAL ACCESS TOKEN](https://github.com/settings/tokens) with `REPOSITORY` scopes.

Then, you can use the cloned repository command to access the cloned repository content.:

```bash
cd <repository-name>
```

### For a public repository

```bash
- name: Clone GuillaumeFalourd/poc-github-actions PUBLIC repository
        uses: GuillaumeFalourd/clone-github-repo-action@main
        with:
          owner: 'GuillaumeFalourd'
          repository: 'poc-github-actions'
```

### For a private repository

```bash
      - name: Clone GuillaumeFalourd/formulas-training PRIVATE repository
        uses: GuillaumeFalourd/clone-github-repo-action@main
        with:
          owner: 'GuillaumeFalourd'
          repository: 'formulas-training'
          access-token: ${{ secrets.ACCESS_TOKEN }}
```

## Licensed

This repository uses the [Apache License 2.0](https://github.com/GuillaumeFalourd/aws-cliaction/blob/main/LICENSE)
