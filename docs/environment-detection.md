# Environment Detection

## Rule

If the required runtime is missing, detect first, then install or download what is needed.

If source references are needed, treat the official GitHub repository as the highest-priority reference source.

## Detection Order

1. detect whether `ruyiPage` is installed in the current Python environment
2. detect whether Firefox is present at the default Windows `C` drive path
3. detect whether that browser should be treated as the fingerprint browser in the current workflow
4. detect whether a fresh `user_dir` should be created for the task
5. detect whether the local `ruyiPage` source copy is behind the official GitHub repository

## If Missing

- install `ruyiPage` if it is missing
- download or prepare the official fingerprint browser when the scenario requires it
- update the local `ruyiPage` reference copy if it is outdated
- avoid continuing with unsupported assumptions about the browser path or identity state
