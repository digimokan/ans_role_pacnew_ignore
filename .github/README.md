# ans_role_pacnew_ignore

Ignore specific Arch Linux '.pacnew' files after system upgrade.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_pacnew_ignore.svg?label=release)](https://github.com/digimokan/ans_role_pacnew_ignore/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* After a `pacman -Syu` operation, ignore 'some_file.pacnew' file by moving it
  to 'some_file.pacnew_ignored'.

## Supported Operating Systems

* Arch Linux.

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_pacnew_ignore
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Ignore updated '.pacnew' files after system upgrade"
         include_role:
           name: ans_role_pacnew_ignore
         vars:
           file_paths:
            - "/etc/locale.gen"
   ```

## Role Options

See the role `defaults` file, for overridable vars:

  * [defaults/main.yml](../defaults/main.yml)

Define these _required_ vars for the role:

  * `file_paths`: list of '.pacnew' files to ignore, post-upgrade (_NOTE: do
    not specify '.pacnew' extensions_)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_pacnew_ignore/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

