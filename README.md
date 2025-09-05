# Memo
Obtf (one big text file) style logging/journaling script.

## Structure
- Memo file will only have one 1H header, `# memo`, followed by a separator, `---`, and a new line. 
- All 2H headers are date in `yyyy-dd-mm` format surrounded by sqaure brackets.
- The rest of the header types (3H, 4H, 5H, and 6H) will be freely available.
- New entry will begin at the top, pushing down all other old entries.
- By default, if target date is not specified (by using either -y, -t, or -d. See below), `memo` will insert text under today date header.
- The script will automatically insert any specified date if it doesn't exist.
- Date header will be inserted where it would make sense chronologically .

## Installation
Clone repository and make the script executable.
```shell
$ chmod +x ./memo
```
Move script to your path...
```shell
$ mv memo /path/to/your/bin/memo
```
...or create an alias.
```shell
$ alias memo="/path/to/this/script"
```

By default, `memo` will use current working directory as where it find memo files. You can change this behavior by editing a script or defining MEMO_DIR environment variable to where you'd like to keep your files.

```shell
export MEMO_DIR="/path/to/memo/files"
```

On first execution, it will check whether or not there is a `memo.md` file in MEMO_DIR. If it can't find one, it will create new one for you.

Note: To default file name and default file extension, you must edit variable in the script directly.

## Usage
Open memo in default editor.
```shell
$ memo
```

Add MESSAGE to memo under today header (the quotation of MESSAGE could be omitted).
```shell
$ memo -m MESSAGE
$ memo --message MESSAGE
```

Add MESSAGE to memo under the date of N day(s) before today
```shell
$ memo -y MESSAGE
$ memo -y N MESSAGE
$ memo -yy...y MESSAGE (N number of y)
$ memo --yesterday N MESSAGE
```

Add MESSAGE to memo under the date of N day(s) after today
```shell
$ memo -t MESSAGE
$ memo -t N MESSAGE
$ memo -tt...t MESSAGE (N number of t)
$ memo --tomorrow N MESSAGE
```

Add MESSAGE to memo under the date DATE (DATE must be valid `yyyy-mm-dd` date).
```shell
$ memo -d DATE MESSAGE
$ memo --date DATE MESSAGE
```

Fetch contents inside MEMO_TEMP file, and paste it to memo, under a header.
```shell
$ memo -f                  # today
$ memo -f -y               # yesterday
$ memo -f -t               # tomorrow
$ memo -f MESSAGE          # fetch first, then add MESSAGE
$ memo -f -t MESSAGE       # both content will be under tomorrow header
$ memo --fetch
```

Create a backup of memo files.
```shell
$ memo -b
$ memo -b -f               # the fetched file will be backed up too
$ memo --backup
```

Open temporary scratchpad for long-form writing.
```shell
$ memo -l
$ memo -l -d DATE          # add under DATE header
$ memo --long
```

Enable verbose logging mode.
```shell
$ memo -v
$ memo --verbose
```

Print help.
```shell
$ memo -h
$ memo --help
```

## Cautions
- Depending on your environment, the content of your messages when using this script may not contain some special characters reserved by your shell such as !,",?,~ etc.
 - `-yy 3` will be interpreted as `three days ago (as in -y N format)` not `two days ago (as in -yyy...y formt)`, this is also the same for -t flag. This means that if quote is ommited using inputting messages, that messages mustn't start with a number e.g.
```shell
$ memo -yy 10 eggs, 5 cheese bought total     # add "eggs, 5 cheese bought total" under date heading 10 days ago
$ memo -yy "10 eggs, 5 cheese bought total"   # add "10 eggs, 5 cheese bought total" under date heading 2 days ago
```

## Author
@ne1nene (Soulmine) [github](https://github.com/ne1nene1/)



