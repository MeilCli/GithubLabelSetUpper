# GithubLabelSetUpper
[![Build Status](https://dev.azure.com/MobileAct/GithubLabelSetUpper/_apis/build/status/MobileAct.GithubLabelSetUpper?branchName=master)](https://dev.azure.com/MobileAct/GithubLabelSetUpper/_build/latest?definitionId=4&branchName=master) [![NuGet version](https://badge.fury.io/nu/MobileAct.GithubLabelSetUpper.svg)](https://badge.fury.io/nu/MobileAct.GithubLabelSetUpper)  
This tool is motivated by [Financial-Times/github-label-sync](https://github.com/Financial-Times/github-label-sync)

## Usage
1. Install .NET Core 2.2 or higher.
1. Install [this package](https://www.nuget.org/packages/MobileAct.GithubLabelSetUpper).

Installed `hublabel` command.

### Environment Variables
- `GITHUB_HOST`: using environment variable instead of argument `--host`
- `GITHUB_TOKEN`: using environment variable instead of argument `-t|--token`

### Commands

#### List labels

```
List the all labels

Usage: hublabel list [options]

Options:
  -h|--help        Show help information
  --host           Host of Github instance, default value is https://github.com
  -t|--token       Token of Github
  -r|--repository  Target repository, value format: {Owner}/{RepositoryName}
  -o|--output      Output file name, including file extension
```

Look up current repository labels and output file.

You can [response file parsing](https://natemcmaster.github.io/CommandLineUtils/docs/response-file-parsing.html?tabs=using-attributes). Make file `list.txt`, example:
```
list
--host
https://github.com
-t
YOUR_GITHUB_TOKEN
-r
REPOSITORY_OWNER/REPOSITORY_NAME
-o
output.yml
```
Execute command: `hublabel @list.txt`

#### SetUp Labels

```
Setup Github labels by option value

Usage: hublabel setup [options]

Options:
  -h|--help        Show help information
  --host           Host of Github instance, default value is https://github.com
  -t|--token       Token of Github
  -r|--repository  Target repository, value format: {Owner}/{RepositoryName}
  -l|--label       The labels configuration file, support json or yml file.
  -d|--dry-run     Calculate the required label changes, but do not apply Github
```

Look up current repository labels and output file.

You can [response file parsing](https://natemcmaster.github.io/CommandLineUtils/docs/response-file-parsing.html?tabs=using-attributes). Make file `setup.txt`, example:
```
setup
--host
https://github.com
-t
YOUR_GITHUB_TOKEN
-r
REPOSITORY_OWNER/REPOSITORY_NAME
-l
LABEL_FILE
```
Execute command: `hublabel @setup.txt`

### Label file
Support file type: JSON or YAML

example of yaml:

```yml
- name: 不具合
  color: d73a4a
  description: Something isn't working
  aliases:
    - bug
- name: 機能
  color: a2eeef
  description: New feature
  aliases:
    - enhancement
- name: Feature Request
  color: 7057ff
  description: New feature request
```

The `name` and `color` property is required. `color` property value is color code without `#`.

The `description` property is optional.

The `aliases` property is optional. If this property was set, its label will change to `name` from alias name. So it mean label is kept.

## License
This tool is under MIT License.

This tool is using libraries:

- [Utf8Json](https://github.com/neuecc/Utf8Json) is published by [MIT License](https://github.com/neuecc/Utf8Json/blob/master/LICENSE)
- [YamlDotNet](https://github.com/aaubry/YamlDotNet) is published by [MIT License](https://github.com/aaubry/YamlDotNet/blob/master/LICENSE)
- [Octokit](https://github.com/octokit/octokit.net) is published by [MIT License](https://github.com/octokit/octokit.net/blob/master/LICENSE.txt)
- [CommandLineUtils](https://github.com/natemcmaster/CommandLineUtils) is published by [Apache License v2.0](https://github.com/natemcmaster/CommandLineUtils/blob/master/LICENSE.txt)

## Contribute
ToDo: Write

### Development Environment
- C# 8.0
- Visual Studio 2019 Preview

## Other
Author: [@MeilCli](https://github.com/MeilCli)
