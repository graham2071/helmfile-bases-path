# helmfile-bases-path

Demonstrate how combining [State template files](https://helmfile.readthedocs.io/en/latest/writing-helmfile/#layering-state-template-files) and [Sub-helmfiles](https://helmfile.readthedocs.io/en/latest/writing-helmfile/#re-using-environment-state-in-sub-helmfiles) fails because bases uses path relative to default file.

```console
$ helmfile -e development -f releases/release-a/helmfile.yaml lint
in releases/release-a/helmfile.yaml: failed to read ../../env/environments.yaml: environment values file matching "development.yaml" does not exist in "."
```

Solution: prevent using file relative reference in environments file, and use global values in sub-helmfiles.
