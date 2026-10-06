[![StepSecurity Maintained Action](https://raw.githubusercontent.com/step-security/maintained-actions-assets/main/assets/maintained-action-banner.png)](https://docs.stepsecurity.io/actions/stepsecurity-maintained-actions)

# Replace in files

This GitHub Action allows you to find and replace text in files by matching a string.

It can be useful for automating repetitive tasks such as updating version numbers, replacing placeholders, or modifying configuration files during deployment.

## Features

- Specify the files to be searched using a glob pattern. You can also specify files to be excluded from the search.
- Find and replace all the occurrences of a string in the repository files.
- Supports different file encodings, including UTF-8, UTF-16, and ASCII.
- Works on every platform that supports JavaScript actions, including Linux, macOS, and Windows.

## Inputs

- `files`:
(**Required**) The files to be searched. It can be the path to a single file, or a glob pattern matching one or more files (e.g. `**/*.txt`).

- `replacement-text`:
(**Required**) The text that will replace the matched text.

- `search-text`:
(**Required**) The text that will be replaced.

- `encoding`:
(Optional) The encoding of the files to be searched. The following values are supported: `utf8`, `utf16le`, `latin1`, `ascii`, `base64`, `hex`. Defaults to `utf8`.

- `exclude`:
(Optional) The files to be excluded from the search. It can be the path to a file or a glob pattern matching one or more files (e.g. `**/*.md`). Defaults to an empty string.

- `max-parallelism`:
(Optional) The maximum number of files that will be processed in parallel. This can be used to control the performance impact of the operation on the system. It should be a positive integer. Defaults to `10`.

## Example usage

```yaml
# Replace all the occurrences of 'hello' with 'world' in all the txt files, 
# excluding the node_modules folder
- name: Replace multiple files
  uses: step-security/replace-in-files@v3
  with:
    files: '**/*.txt'
    search-text: 'hello'
    replacement-text: 'world'
    exclude: 'node_modules/**'
    encoding: 'utf8'
    max-parallelism: 10

# Replace all the occurrences of '{0}' with '42' in the README.md file
- name: Replace single file
  uses: step-security/replace-in-files@v3
  with:
    files: 'README.md'
    search-text: '{0}'
    replacement-text: '42'
```
