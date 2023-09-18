# Terraform Beginner Bootcamp 2023

## Semantic Versioning

This project will utilze semati versioning for its tagging. Changes added

[semver.org]https://semver.org/

TRhe format will be: 
Given a version number **MAJOR.MINOR.PATCH**, e,g: `1.0.1`

   - **MAJOR** version when you make incompatible API changes
   - **MINOR** version when you add functionality in a backward compatible manner
   - **PATCH** version when you make backward compatible bug fixes

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## Install the Terraform CLI

### Considerations with the Terraform CLI changes

The Terraform CLI Installation instructions have changed due to gpg key ring changes.
So we needed to refer to the latrest install CLI instructions via TF Doco and change the scripting for install.

[Install Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

### Considerations for Linux Distribution

This project is built aganist Ubuntu
Please consider checking your Linux Distro and change accordingly

[How to Check OS version in Linux](https://www.cyberciti.biz/faq/how-to-check-os-version-in-linux-command-line/)

Example of checking OS Version:
```sh
$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

### Refactoring into Bash Scripts

While fixing the Terraform CLI gpg deprecation issues, we notice that bash script steps were a considerable amount more code.
So we decided to create a bash script to install the Terraform CLI.

- This will keep the Gitpod Tsk file [gitpod.yml](.gitpod.yml) tidy.
- This allows easily debug and manually execute Terraform CLI install.
- This will allow better portability for other projects that need to install Terraform CLI

#### Shebang Considerations

A shebang (pronoucecd Sha-bang) tells the bash script what program will interprete the script. e.g. `#!/bin/bash`

ChatGPT recommended this format for bash: `#!/usr/bin/env bash`

 - for portability for different OS distro
 - Will search the user's PATH for bash executable.

#### Execution Considerations 
When executing the bash script we can use the `./` shorthand notation to execute the bash script.

e.g. `./bin/install_terraform_cli.sh`

If we are using a script in .gitpod.yml we need to point the script to a programto interprete it.

e.g. `source ./bin/install_terraform_cli.sh`

#### Linux Permissions Considerations
We need to make Linux Permissions executable ayt the user mode.

```sh
chmod u+x ./bin/install_terraform_cli.sh
```

alternatively:
```sh
chmod 744 ./bin/install_terraform_cli.sh
```
### Github Lifecycle (Before, Init Command)
We need to be careful when using init because it will no rerun if we restart an existing workspace.


https://www.baeldung.com/linux/bash-shebang-lines
https://en.wikipedia.org/wiki/File-system_permissions
https://www.gitpod.io/docs/introduction


