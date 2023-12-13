# Crontab Command Reference

This reference guide covers various commands associated with `crontab` and their respective flags.

## 1. `crontab -e`

### Description:
Edit the crontab file for the current user.

### Flags:
- `-e`: Opens the crontab file in the default text editor (specified by the `EDITOR` environment variable).

### Usage:
```bash
crontab -e
```

## 2. `crontab -l`

### Description:
Display the current user's crontab entries.

### Flags:
- `-l`: Lists the contents of the crontab file.

### Usage:
```bash
crontab -l
```

## 3. `crontab -r`

### Description:
Remove all crontab entries for the current user.

### Flags:
- `-r`: Deletes all crontab entries.

### Usage:
```bash
crontab -r
```

## 4. `crontab -u <username>`

### Description:
Perform crontab operations on behalf of the specified user.

### Flags:
- `-u <username>`: Specifies the user whose crontab is to be edited or viewed.

### Usage:
```bash
crontab -u user2 -l
```

## 5. `crontab -i`

### Description:
Interactive mode - prompts before deleting the crontab.

### Flags:
- `-i`: Enables interactive mode.

### Usage:
```bash
crontab -i
```

---

Feel free to explore more about these commands using the `man` pages:
- `man crontab`: for general crontab command usage
