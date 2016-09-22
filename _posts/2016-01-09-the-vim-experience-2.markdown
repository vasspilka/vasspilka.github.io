---
layout: post
title: "The Vim Experience 2"
date: "2016-01-09 20:43:21 +0200"
---

Alright I'll be honest with you, I did not trust Vim, I mostly work with Rails project, that means huge directories with tons of files.
While I occasianally edited individual files in vim I rarely used it in general, I did use it for my personal journal, and for  my blog, but
in general programming (where vim shines) I consistantly found my self using a mainstream editors like Atom. That ofcourse meant my vim experience
did no go far past basic knownledge, yes I became familiar at using HJKL to navigate and xxG to move lines dddddddddddd to get rid of that faulty 
paragraph but lets face it, that is a shitty use of this powefull text editor like vim.

That is until last week. Last week I made an OS refresh (I do that about once a year), and was also researching new stuff that could aid my work environment.
That was where I stumbled upon a video describing how to use vim efficiently with tmux, that was a revelation for me, and I will explain why.

### Vim + Tmux Your specialized IDE

As a Rails developer I am constantly on the command-line and not just one. I use it update my gems, run the server among other services and ofcourse deploy
the new updates, and that esspesially becomes true when I have to manage both the backend Rails application and a javascript front. 
To solve this I used to have multyple tabs in my console, sometimes even in multyple windows. That soon however became hard to navigate.
Finding what I wanted often took me more time than executing or reading what I wanted. 

This is where tmux makes its apearence, tmux is a terminal multiplexer. In other worlds it handles multiple consoles.
So how does if differ from just using a terminal and tabs you ask?
Well it works by creating session, each session can have many tabs and each tab can split to multiple windows called panes.
You can quickly switch between tabs and most importantly you can detach from the session while it runs in the background.
That can be extremely useful on remote machines where you want to have running processes even while logged out or want to have 
an open development session.
But that alone would not be that impressive, the reasons tools like tmux can be so powerful is customization.
Lets set an example, I am a ruby developer, running tests often is more frequent that switching to the browser.
Switching tabs, hitting the up-arrow then enter can be pretty fast, but also quite distracting and sets you to a diferent environment espessially if
you are in an non-terminal text editor. You could customize tmux to let you type a prefix (Ctrl+b by default) and a key to instantly type the test you want to run
and then let it open a small pane at the bottom of your window with the results, and if all is successfull close it imidiatly, you could further customize that to run the 
last test you run when you specify no file. That is amazing you can run tests imidiatly without turning focus away from your code!! A huge productivity boost!
By creating scripts like the one I described above you can progressivly make a highly specialized, customazable and personal developement enviroment to suit
your every need.

But lets talk vim! So what made me give vim another chance? Like I said it all started with a video (I'll share a link at the end).
When I first tried vim for Rails development I found it unbearable to navigate through different files, I've heard of plugins like NerdTree but did not find them of
much use, furthermore while I knew tabs existed I found it timeconsuming and confusing to use them plus NerdTree opens in a single tab, that left me with a single vim tab and window to work with.
No wonder I found vim being unproductive opening a diferent file either meant using NerdTree and slowly navigating through diferent files, this involved moving my right hand away 
from the "jk" keys to hit enter everytime I wanted to open or close a subdirectory, or using the edit command like so `:e path/to/file/with_big_name`. Everytime I wanted to switch between files.
I believe you understand how annoying that can become.  

Acknowledging the leader.
In vim there a special key called <leader> key which is used to execute personal shortcuts, by default it is assigned to the backslash key '\', however becouse of its position
I often pressed enter instead and it also is pretty far away of the rest of the keyboard. One of the first things I did was remap the leader to comma ',' which is a lot closer,
that made me see leader as a what it should be, a tool to enable me to make quick shortcuts! With having an easily accessible leader key I mapped `:tabnew` to `,t` making it only 2 keystokes long.
That also came with the next relevation. 

The Fuzzy Finder!! When I first started learning about vim, for some strange and unfortunate reason, I did not stumble upon a fuzzy finder, at least not while realizing its power.
A fuzzy finder is a vim plugin that give you the ability to type a file roughly and performs a fuzzy search to find the best suited file. You can easily map it to a leader command
and then execute it in almost no time, I have mine mapped at <leader>f so typing `,f mu` and enter will open the file `app/models/user.rb` simmilarly typing `,f cont` will display all 
my controller files and I can move and chose the one I want. Ctrl-P the fuzzy finder I use also remembers the files you open, and progresivly learns your behaveyior making your file opening better
each time you open a file.



Getting in and out

The silver searcher

Windows with windows key


Continious Improvement

C-m for enter
