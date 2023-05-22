# A prompt theme for Nushell
[中文说明](README_zh.md)

![](image/p.png)

## Instructions
1. Download the `prompt.nu` file to the `~/.config/nushell` directory.
2. Run `config nu` and add the following content to the configuration file.
    ```nu
    source ~/.config/nushell/prompt.nu
    let-env PROMPT_INDICATOR = {|| "" }
    let-env PROMPT_COMMAND = {|| full-left-prompt }
    ```
3. Save the file and restart Nushell.

## Advanced Usage
Modify the content as follows:

1. Sequential execution of custom options
    ```nu
    let-env PROMPT_COMMAND = {|| left-prompt [
        'user',
        'dir',
        'fast-git'
        'duration',
    ]}
    ```
2. Parallel execution of custom options. Currently, there is no significant difference in performance.
    ```nu
    let-env PROMPT_COMMAND = {|| par-left-prompt [
        'user-host',
        'dir',
        'full-git'
        'duration',
    ]}
    ```

## Option List
```nu
[
    'user', # Only display user name. Always hide the hostname
    'user-host', # Automatically display the hostname when using SSH remote login名
    'dir', # Display Current directory
    'full-git' # More comprehensive Git information, including stage status.
    'fast-git' # Faster Git information, with less information compared to full-git, suitable for Windows systems
               # You can also choose neither of them.
    'duration', # Command execution time.
    'wsl', # WSL environment indicator
]
```
