# pre-commit-trivy

Add this to your [pre-commit](https://pre-commit.com/) `.pre-commit-config.yaml` config.

You can use [trivy fs flags](https://aquasecurity.github.io/trivy/v0.37/docs/target/filesystem/) to configure Trivy.
Insert the required flags in the `args` field.

## trivyfs-docker
pre-commit will use the `aquasecurity/trivy:0.37.1` docker image and run it inside a docker container.

```yaml
repos:
-   repo: https://github.com/mxab/pre-commit-trivy.git
    rev: v0.4.0
    hooks:
    -   id: trivyfs-docker
        args:
          - --skip-dirs
          - ./tests
          - . # last arg indicates the path/file to scan
```
### Cache
The hook will create a cache directory `.pre-commit-trivy-cache` in your repo. Add it to the `.gitignore`.

```
echo ".pre-commit-trivy-cache" >> .gitignore
```

## Example

You can find a sample use case here https://github.com/mxab/trivy-pre-commit-demo
