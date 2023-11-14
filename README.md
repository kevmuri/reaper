# Reaper

Reaper is a Bash script for managing processes based on the port they are using. It allows for viewing or ending any processes tied to a specific port number provided as input.

## Prerequisites

Basic knowledge of Bash is beneficial but not strictly necessary. Familiarity with the command line and commands used to manipulate processes (such as `lsof` and `kill`) is also beneficial.

## Installation

1. Save the script to a file on your local machine named `reaper`.
2. Make the file executable: `chmod +x reaper`
3. Move the script to `/usr/local/bin` directory: `mv reaper /usr/local/bin/reaper`

## Usage

You can use Reaper either to view the processes running on a particular port or to kill the processes running on a specific port. This behavior is controlled by passing the appropriate flag when calling the script. The format is as follows:

```bash
reaper {mode} {port number}
```

Replace `{mode}` with `-v`, `-view`, `-k`, or `-kill` depending on if you want to view the processes running on a specific port or if you intend to kill the processes running on a particular port. 

Replace `{port number}` with the port number you want to examine or whose processes you would like to stop.

**Examples:**

To view the processes running on port 8080, use the following command:

```bash
reaper -view 8080
```

If you would like to stop the processes running on port 8080, use the following command instead:

```bash
reaper -kill 8080
```

## Note

Please note that the `-kill` option uses `kill -9`, which forcibly and immediately stops the process. It does not allow the process to terminate in a controlled manner, which can lead to various problems such as data loss if the process was writing to a file.

If possible, it is recommended to use the regular `kill` command first, which allows the process to terminate gently. Please use Reaper responsibly to avoid unintended consequences.

For more information about command usage and their risks, see [man kill](https://linux.die.net/man/1/kill) and [man lsof](https://linux.die.net/man/8/lsof).