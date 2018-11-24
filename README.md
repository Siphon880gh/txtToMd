txtToMd
===
By Weng Fei Fung. Command line tool that converts a textfile to Markdown file and opens it in the web browser. It can also accept copy and pasted multiline text in the command line and convert that (limitation: can't have the same enclosing quotes inside the text, but you can alternate between single vs double quotes, such as using single quotes to enclose the text passing to the command and having double quotes as part of inside the text).

Dependencies
---
- concurrently (sudo npm install -g concurrently)
- http-server (sudo npm install -g http-server)
- web browser markdown extension (eg. Markdown Preview Plus for Chrome)

Use cases
---
You like to take study or meeting notes in a text editor. You also took fancy signifying what's a title vs subtitle using symbols. Say for example, placing `===` under titles and `---` under subtitles, listing bullets with `- ` and the various conventions of Markdown that's as intuitive to non-programmers or is just easy to speedily take notes without formatting them manually. You want to pretty up what you see in a web browser with a table of contents that you can use to click between sections of your notes based on the various titles and subtitles. You want the `*` highlighting and listing format that Markdown provides. Simply copy and paste all your notes (doesn't matter if there are multiple lines) into your Terminal and you'll see the pretty Markdown version on the web browser. Or, provide the file path to the command.

File example
---
```
txtToMd test-me.md
```

Multitext example
---
```
txtToMd 'Title1
===

Subtitle
----

List
- a
- b
- c'
```

Installation
---
1. Move these files to a permanent folder. A shell script will generate MD files to this folder and serve to your browser.
2. Add this script to ~/.bash_profile, changing the Freelance path to the permanent folder (do not end in forward slash /):  
```
    function txtToMd() {
                    dir=~/Freelance/htdocs/repos/txtToMd
                    rm $dir/temp.md
                    if [[ -f "$dir/$1" ]]
                    then
                        cp "$1" $dir/temp.md
                    else
                        echo "$1" > $dir/temp.md
                    fi
                    concurrently "http-server -c-1 $dir" "open http://127.0.0.1:8080/output-reader.html"
                    };
```
3. Then execute the new configuration:
`
source ~/.bash_profile
`

That's it!