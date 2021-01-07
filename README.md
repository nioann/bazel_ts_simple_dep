# Repo for reproducing bug: https://github.com/bazelbuild/rules_nodejs/issues/2388
Module resolution breaks at runtime, with a "Cannot find module" error.

The repo now builds, after implementing the suggestion of @mattem. Issue introduced in version 3.0.0 of rules_nodesjs

Fix:
In the nodejs_binary targets add one of the two following parameters:

- templated_args = ["--bazel_patch_module_resolver"]
- link_workspace_root = True

# Project setup
Run the following commands
```
yarn create @bazel bazel_ts_simple_dep
cd  bazel_ts_simple_dep
yarn build
yarn add -D typescript
yarn add -d @bazel/typescript
```
