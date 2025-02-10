# memo
obtf (one big text file) style logging/journaling script

## background
i read somewhere about an idea of keeping all of your (+ other) idea, thought, journal, and possibly project, essay, and other long-form writing in one single text file. it's ridiculous, but it was too interesting for me to not to try it. while in the end, i did end up split my notes to more atomic, i still use this idealogy of "keeping one's thought in a single text file" to quickly writing thing down. it is amazingly liberating when you didnt't have to think where you idea went, all you need is `ctrl+f` and a good tagging/linking system (haha, "good"). anyway, that why i wrote this script. i didn't know anything about bash scripting until i wrote this script. it was a ride of trial and error but at the end, i learned so much about this language (and why people trying to avoid it, lol). 

## structure
- memo file will only have one 1H header, `# memo` follow by separator `---` and a new line. 
- all 2H header, will be date in `yyyy-dd-mm` format that surrounded by wikilink.
- the rest of header type (3H, 4H, 5H, and 6H) will be freely available for you to use
- new entry begin at the top, pushing down the old one.
- by default, if no target date specified, the memo will inserted its message under `today` header
