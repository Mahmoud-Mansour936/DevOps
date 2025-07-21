# Comparison

## String Comparison

```bash
| Operator | Description                            | Example                       |
|----------|----------------------------------------|-------------------------------|
| `==`     | Strings are equal                      | `[ "$a" == "$b" ]`            |
| `!=`     | Strings are not equal                  | `[ "$a" != "$b" ]`            |
| `<`      | Less than (alphabetically)             | `[ "$a" \< "$b" ]`            |
| `>`      | Greater than (alphabetically)          | `[ "$a" \> "$b" ]`            |
| `-z`     | String is null (zero length)           | `[ -z "$a" ]`                 |
| `-n`     | String is not null (non-zero length)   | `[ -n "$a" ]`                 |

> ⚠️ Note: Use backslashes for `<` and `>` when using single brackets `[ ]`.
```

## Integer Comparison

Lexigraphically 

```bash
| Operator | Description             | Example                  |
|----------|-------------------------|--------------------------|
| `-eq`    | Equal to                | `[ "$a" -eq "$b" ]`      |
| `-ne`    | Not equal to            | `[ "$a" -ne "$b" ]`      |
| `-gt`    | Greater than            | `[ "$a" -gt "$b" ]`      |
| `-lt`    | Less than               | `[ "$a" -lt "$b" ]`      |
| `-ge`    | Greater than or equal   | `[ "$a" -ge "$b" ]`      |
| `-le`    | Less than or equal      | `[ "$a" -le "$b" ]`      |
```

## Logical Comparison

```bash
| Operator | Description           | Example                                  |
|----------|-----------------------|------------------------------------------|
| `-a`     | Logical AND           | `[ "$a" -gt 5 -a "$b" -lt 10 ]`          |
| `-o`     | Logical OR            | `[ "$a" -gt 5 -o "$b" -lt 10 ]`          |
| `!`      | Logical NOT           | `[ ! "$a" -eq 5 ]`                       |
| `&&`     | Logical AND (modern)  | `[[ "$a" -gt 5 && "$b" -lt 10 ]]`        |
| `||`     | Logical OR (modern)   | `[[ "$a" -gt 5 || "$b" -lt 10 ]]`        |

> ✅ Prefer `[[ ... ]]` with `&&` and `||` in modern scripts for better readability.
```

## File Comparison

```bash
| Operator          | Description                          | Example                   |
|-------------------|--------------------------------------|---------------------------|
| `-e`              | File exists                          | `[ -e myfile.txt ]`       |
| `-f`              | Regular file                         | `[ -f myfile.txt ]`       |
| `-d`              | Directory exists                     | `[ -d /etc ]`             |
| `-r`              | File is readable                     | `[ -r myfile.txt ]`       |
| `-w`              | File is writable                     | `[ -w myfile.txt ]`       |
| `-x`              | File is executable                   | `[ -x myscript.sh ]`      |
| `-s`              | File is not empty                    | `[ -s myfile.txt ]`       |
| `file1 -nt file2` | File1 is newer than File2            | `[ file1 -nt file2 ]`     |
| `file1 -ot file2` | File1 is older than File2            | `[ file1 -ot file2 ]`     |

```