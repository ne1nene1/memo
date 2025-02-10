# memo
obtf (one big text file) style logging/journaling script

## background
I read somewhere about an idea of keeping all of your (and other's) idea, thought, journal, and possibly project, essay, and other long-form writing in one single text file. It's ridiculous, but it was too interesting for me to not to try it. While in the end, I did end up split my notes into more atomic, I still use this idealogy of "keeping one's thought in a single text file" to quickly writing thing down. It is amazingly liberating when you didnt't have to think where your idea went, all you need is `ctrl+f` and a good tagging/linking system (haha, "good"). Anyway, that's why I wrote this script. I didn't know anything about bash scripting until i wrote this script. It was a ride of trial and error, but in the end, I learned so much about this language (and why people trying to avoid it, lol). 

## structure
- memo file will only have one 1H header, `# memo` follow by separator `---` and a new line. 
- all 2H header, will be a date in `yyyy-dd-mm` format that surrounded by wikilink.
- the rest of the header type (3H, 4H, 5H, and 6H) will be freely available for you to use
- new entry begin at the top, pushing down old one.
- by default, if no target date specified, memo will inserted its messages under `today` header
- the script will automatically insert date if it doesn't exist
- date header will be inserted where it would make sense chronologically 

## installation
make file executable by changing permission
```shell
chmod +x ./memo
```
add to your path
```shell
mv memo /path/to/your/bin
```
or add alias to your shell config
```shell
alias memo="/path/to/this/script"
```

by default `memo` will use current working directory as a place where it will find a file. you can change this behavior by editing a script or changing MEMO_DIR to the path you'd like to keep your file.
```shell
export MEMO_DIR="path/to/keep/a/file"
```
on first execution, it will check whether there is a `memo.md` file in MEMO_DIR. if didn't find one, it will create one for you
note: you can change file name and extension in the script directly

## usage
open memo in editor
```shell
memo
```
add MESSAGE to memo under today header (quotation of MESSAGE can be omitted)
```shell
memo -m MESSAGE
memo --message MESSAGE
```
add MESSAGE to memo under the date N day(s) before today
```shell
memo -y MESSAGE
memo -y N MESSAGE
memo -yy...y MESSAGE (N number of y)
memo --yesterday N MESSAGE
```
add MESSAGE to memo under the date N day(s) after today
```shell
memo -t MESSAGE
memo -t N MESSAGE
memo -tt...t MESSAGE (N number of t)
memo --tomorrow N MESSAGE
```
add MESSAGE to memo under the date DATE
```shell
memo -d DATE MESSAGE
memo --date DATE MESSAGE
```
fetch content inside MEMO_TEMP file, and paste it to memo, under header
```shell
memo -f                  # today
memo -f -y               # yesterday
memo -f -t               # tomorrow
memo -f MESSAGE          # fetch first, then add MESSAGE
memo -f -t MESSAGE       # both content will be under tomorrow header
memo --fetch
```
create backup of memo
```shell
memo -b
memo -b -f               # the fetched file will be backed up too
memo --backup
```
open temporary scratch pad for long-form writing
```shell
memo -l
memo -l -d DATE          # add under DATE header
memo --long
```
enable verbose logging mode
```shell
memo -v
memo --verbose
```
print help
```shell
memo -h
memo --help
```

## cautions
- depending on your environment, the content of your messages to be put using cli may not contain some special character reserved by your shell such as !,",?,~ etc.
- `-yy 3` will be intreprete as `three days ago (as in -y N format)` not `two days ago (as in -yyy...y formt)`, this is also the same as -t flag.
     this means that if you ommited quote to insert a message, that message
     mustn't start with number

## author
@ne1nene (Soulmine) [github](https://github.com/ne1nene1/)
