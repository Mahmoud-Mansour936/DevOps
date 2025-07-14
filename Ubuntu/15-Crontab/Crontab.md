# Crontab

A crontab is a configuration file that specifies shell commands to run periodically at specified times. The crontab command is used to create, view, edit, and delete these files.

## Basic Syntax

The crontab syntax consists of five time fields followed by a command:

```bash
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of the month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday)
# │ │ │ │ │
# │ │ │ │ │
# * * * * * command to execute or give the path of file we need to excute 

```

## Common Commands

View your crontab:

```bash
crontab -l
```

Edit your crontab:

```bash
crontab -e
# it opens crontab file then we write we need as its syntax then we save it 
```

Remove your crontab:

```bash
crontab -r
```

## Special Characters

- *****: any value
- **,**: value list separator (e.g., 1,3,5)
- **-**: range of values (e.g., 1-5)
- **/**: step values (e.g., */5 means every 5 units)

## Examples

Run a script every day at 3:30 AM:

```bash
30 3 * * * /path/to/script.sh
```

Run a script every Monday at 8:45 PM:

```bash
45 20 * * 1 /path/to/script.sh
```

Run a script every hour:

```bash
0 * * * * /path/to/script.sh
```

Run a script every 15 minutes:

```bash
*/15 * * * * /path/to/script.sh
```

## Special Strings

You can also use these special strings:

```bash
@reboot    Run once at startup
@yearly    Run once a year (0 0 1 1 *)
@annually  Same as @yearly
@monthly   Run once a month (0 0 1 * *)
@weekly    Run once a week (0 0 * * 0)
@daily     Run once a day (0 0 * * *)
@midnight  Same as @daily
@hourly    Run once an hour (0 * * * *)

```

## Tips

- Always include the full path to your scripts and executables