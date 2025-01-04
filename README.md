# Ansible Role: bash_history

This role configures bash history settings on Unix/Linux systems, providing enhanced history functionality and customization options.

## Features

- Configure unlimited or fixed-size bash history
- Set custom history timestamp format
- Specify custom history file location
- Control history behavior (duplicates, space-prefixed commands)
- Enable/disable immediate history writing after each command
- Configure commands to ignore in history

## Requirements

- Ansible 2.9 or higher
- Bash shell

## Role Variables
```yaml
# Size of bash history (set to "unlimited" for no limit)
bash_history_histsize: unlimited
# Size of history file (set to "unlimited" for no limit)
bash_history_histfilesize: unlimited
# Timestamp format for history entries
bash_history_histtimeformat: "[%F %T] "
# Custom history file location
bash_history_histfile: "~/.bash_eternal_history"
# History control settings (optional)
bash_history_histcontrol: null
# Commands to ignore in history (optional)
bash_history_histignore: null
# Path to bash configuration file
bash_history_bash_config_file: "~/.bashrc"
# Write history after each command
bash_history_write_after_each_command: true
```

## Example Playbook

```yaml
- hosts: servers
  roles:
    - role: microhoffman.bash_history
```

## Configuration Examples

### Unlimited History

```yaml
bash_history_histsize: unlimited
bash_history_histfilesize: unlimited
```

### Fixed-Size History

```yaml
bash_history_histsize: 10000
bash_history_histfilesize: 20000
```

### Custom History Control

By default the `bash_history_histcontrol` and `bash_history_histignore` variables are set to empty strings, which resets those variables to the default value, which by default does not filter out any commands.

If you want to change this behavior, you can set the variables to the desired values, for example:

```yaml
bash_history_histcontrol: "ignorespace:ignoredups"
bash_history_histignore: "ls:ll:history:exit:clear"
```

### Custom Timestamp Format

```yaml
bash_history_histtimeformat: "[%Y-%m-%d %H:%M:%S] "
```

## License

MIT

## Author Information

Created by microhoffman

## Contributing

Issues and pull requests are welcome on GitHub.
