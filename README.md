TO MD
===
By Weng Fei Fung. Lets you copy and paste your study or meeting notes into Terminal then have a pretty up Markdown version show up on web browser. Can support text with multiple lines.

Supported Platforms
---
- Unix
- MAC OS
- Windows (Instructions not provided)

Use cases
---
You like to take study or meeting notes in a text editor. You also took fancy signifying what's a title vs subtitle using symbols. Say for example, placing `===` under titles and `---` under subtitles, listing bullets with `- ` and the various conventions of Markdown that's as intuitive to the person programming Markdown as it is to the layperson taking notes in a text editor. You want to pretty up what you see in a web browser with a table of contents that you can use to click between sections of your notes based on the various titles and subtitles. You want the `*` highlighting and listing format that Markdown provides. Simply copy and paste all your notes (doesn't matter if there are multiple lines) into your Terminal and you'll see the pretty Markdown version on the web browser.

Command Line example
---
```
toMD 'Title1
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
1. Move these files to a folder on your computer and keep it there. A temp.md will be generated there to be served to the browser every time you copy text to cli with the toMD command.
2. Place this in ~/.bash_profile, changing the path leading to temp.md to the path of this README.md, and that there are two such paths:  
`
function toMD() { echo "$1" > ~/Freelance/htdocs/repos/toMD/temp.md; http-server -o -c-1 ~/Freelance/htdocs/repos/toMD/; };
`
3. Then update BASH:  
`
source ~/.bash_profile
`
4. Install http-server which lets my tool serve files to your browser:  
`
sudo npm install -g http-server
`
5. On your default web browser, install an extension/plugin that displays MD format. I recommend Markdown Preview Plus for Chrome because it generates a clickable Table of Contents for your markdown.

That's it!

Known Issues
---
If your text has quotes, it will break the MD format at that point. For example, if you enclose your text that you pass to toMD with double quotes, then a double quote in the text will break the preview at that point. If you had enclosed with single quotes, then the preview would break at that single quote. Anyone with ideas how to work around this besides escaping the quotes or avoiding quotes in your text or bulk replacing the quotes before copying, because this isn't ideal when you may be copying the text from study notes, then feel free to let me know or push your own commit.