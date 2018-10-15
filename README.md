# xen-setup

This role sets up a fully running Xen installation.
It automatically reboots the target and waits to come back if Xen was initially installed.
When anything else happens (i.e. change of the cmdline), Xen will not reboot to prevent service outages.

## Requirements

A recent Debian or Ubuntu installation with GRUB as the bootloader

## Role Variables


| Name                 | Default/Required | Description                                          |
|----------------------|:----------------:|------------------------------------------------------|
| `xen_arch`           | `amd64`          | Suffix (architecture) of the Xen package             |
| `xen_reboot_delay`   | `10`             | Wait n seconds before checking if the server is back |
| `xen_reboot_timeout` | `3000`           | Wait up to n seconds after the server was rebooted   |
| `xen_cmdline`        |                  | Command line for the Xen kernel                      |

## Example Playbook

```yml
- hosts: xen
  roles:
    - role: xen-setup
      xen_cmdline: dom0_mem=512M,max:512M
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Author Information

- [Janne Heß](https://github.com/dasJ)
