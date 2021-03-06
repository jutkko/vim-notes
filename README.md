# Notes From Reading the Vim Manual
## Intro
### Vim
I have been using vim for some years now. It is only recently, when I started
working I started to seriously look into it. Vim is a very powerful and
opinionated editor. I want to learn a lot about it. OK now it's time to ditch
this document if you don't agree with me, we are still friends and everything
is still fine.

### Vim manuals
I knew the most basic ways to use vim before I started reading the
[manuals][manual]. I am not sure how suitable this will be for a person who is
just starting to learn vim. I will try to explain where I am referencing stuff
if I find it necessary.

The manual for vim is not the easiest way to start vim. It is very vim style.
For me, the experience has been: I wanna learn vim -> I read manual -> I start
reading some instructions how to read the vim manual. Then we can go backwards
to learn vim. :) We can go to the vim manual by typing `:help` in vim's command
mode. The **home** page for vim's manual consists of three sections:

- BASIC
- USER MANUAL
  - Getting Started
  - Editing Effectively
  - ...
- REFERENCE MANUAL
  - General Subjects
- LOCAL ADDITIONS
  - ctrlp.txt
  - airline.txt
  - ...

Note that the last section is the section for your local plugins. The sections
are meant to be suitable for different use cases. If we compare the level of
advanceness, we would have BASIC `<` USER MANUAL `<` REFERENCE MANUAL. However
this does not mean that the things covered are mutually exclusive between the
sections. That being said, in the following chapter I will try to combine the
good bits from different sections about a topic together.

I am going to write some of the useful commands I learned while digging through
the manuals.

## Selected Commands
It is interesting to see that many people think the power-users are good
at something because they know a lot of tricks. And you can find a bunch of
link on the internet that tries to teach you those cool tips and tricks. I
dispute that. I selected **commands** to be in this section's name, believing
that the **tips** are not **tips**. They are just a collection of usual
commands, used in an efficient way. For example

```
ggvG
```

Selects the whole file. Why? Why don't we use `:h gg`, `:h v` and `:h G` to
find out!

### Motions
`e` moves the curser to the end of the work you are currently at. If you
specify a number `n` before `e`, vim jumps to the end of the `n`th word.

The difference between `d2w` and `d2e`,
```
You need a computer.
    ^
```

After `d2w`,
```
You computer.
    ^
```

After `d2e`,
```
You  computer.
    ^
```

`$` moves the curser to the end of the line. The use case for this is simple,
after `d$` (note that `$` in inclusive)
```
You
   ^
```

The information above comes from usr_04.txt.

A special way to move around a file is to use the power of vim's text object
motions. Here are some examples:

`)` moves your cursor to the start of the next sentence

```
You need a computer. He doesn't need one.
   ^
```

After `)`

```
You need a computer. He doesn't need one.
                     ^
```

`}` moves your cursor to the next paragraph
`%` moves your cursor to the next matching brace, this is really useful

See more in quickref.txt.

### Changing text
When it comes to `c` command, which is the changing text character, it does not
matter if you use `c2e` or `c2w` to replace two words. Let's start with the
good old example,

```
You need a computer.
    ^
```

After `c2w`,
```
You computer.
```

After `c2e`,
```
You computer.
```

The information above comes from 04.2.txt.

### Now repeat
How to use `.`? We need to embrace its power and make most use out of it!
So what is it for? It repeats the last command you ran. Looking the example
from the manual, we want to remove the `\<B\>` tags from the line,

```
To <B>generate</B> a table of <B>contents.
```

We can do `/<`, `df>`, `n`, `.`, `n`, `.` on the line.

The information above comes from 04.3.txt.

### Visual Mode and Text Objects
In block visual mode, try out `o` and find something exciting!

In line visual mode, while having something selected, you can press `o` to jump
to the other end of your selected words, while keeping your text selected.
When is this going to be useful? I need to try this out and come back to
this section after I find something exciting!

SWAPPING TWO CHARACTERS

Frequently when you are typing, your fingers get ahead of your brain (or the
other way around?).  The result is a typo such as "teh" for "the".  Vim
makes it easy to correct such problems.  Just put the cursor on the e of "teh"
and execute the command `xp`.  This works as follows: `x` deletes the
character e and places it in a register.  `p` puts the text after the cursor,
which is after the h.

```
teh     th     the
 x       p
```

The information above comes from 04.4.txt.

Ever find yourself in the middle of a word and want to delete that word? Use
`daw` which stands for "Delete A word"!

Ever find yourself in the middle of a sentence and want to delete the whole
sentence? Use `dis` which stands for "Delete A Sentence"!

For more text objects see motion.txt:6. Text object selection.

When you find yourself repeating one or a few keys many times in a row, you
should stop. Most of the times this means you're doing something that can be
done in a more efficient way. Commands `c`, `h`, `l`, `b`, `f`, `j` and `k` are
the perfect examples.

The following commands can be used after `c`, `v` and `d` in different scenario
in different scenarios.

`aX` commands does something around a text object surrounded by `X`, where `X`
can be `"`, `'`, `(`, `[`, `w`, `p` and `s` (there are probably more). For
example `va"`

```
The quick brown fox jumps over the "lazy" dog.
                                     ^
```

Will select in visual

```
The quick brown fox jumps over the "lazy" dog.
                                   [    ]
```

`iX` commands does something inside a text object surrounded by `X`.

And `di"`

```
The quick brown fox jumps over the "lazy" dog.
                                     ^
```

Gives us
```
The quick brown fox jumps over the "" dog.
```

The information above comes from index.txt.

To be continued...

[comment]: #(Links)
[manual]: http://vimdoc.sourceforge.net/htmldoc/help.html
