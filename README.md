# psrw
2D radom walk in Postscript

This is a simple Postscript hack to visualise a 2D random walk. The
interesting part is that you get a different trajectory of the random
walk every time you open the file `psrw.ps`.

You can open the file with `gv`:

```
gv -nosafer -nosafedir psrw.ps
```

where the extra options are needed to disable some security checks. You
can also visualise the document with Ghostscript, if you like:

```
gs psrw.ps
```

Liked it? Now close the file and reopen it ;-)

## WTF?

Postscript is a Turing-complete language. This means that you can do any
feasible computation in Postscript. Hence, simulating a random walk in
Postscript is not a big fuss at all, also because the standard
Postscript definition already includes a pseudo-random number generator,
so you don't need to implement it yourself. The only problem is that the
pseudo-random number generator needs to be initialised with a new seed,
otherwise you would always visualise the _same_ trajectory.   

The simple solution implemented in `psrw.ps` is to store the seed in the
same file as a comment, and _update_ it after every run.  In a word,
`psrw.ps` rewrites itself at each run, changing the seed and allowing to
generate a _new_ random walk trajectory every time you open the file. 

## Why?

Well, there is no particular reason to write anything like `psrw.ps`. I
just tried to do something similar around 2001 or 2002, when I was using
Postscript quite heavily, and at that time I did not find a proper way
through.  The simplicity of the solution implemented in `psrw.ps`
scratches a long-standing personal itch, and tells a lot about my poor
knowledge of Postscript...

## No really, WHY?

I just wanted to make a point about (not) trusting documents written in
formats that you don't understand, or that are not freely accessible or
not documented.  Many _text_ formats out there are Turing-complete or
close-to, and some visualiser (e.g., for PDF or OpenXML) include
interpreters for other Turing-complete languages (like Javascript or
VBScript). This mean that they can do almost anything when you "_open_"
those "_text_" files. 

If it's so easy to craft a document that modifies itself to change a
comment that you can't visualise, what else can be done by "_text_"
files saved in proprietary formats?

## Links

- A brief [summary of Poscript
  commands](http://www.math.ubc.ca/~cass/courses/ps.html)

- A [game of life](https://www.tjhsst.edu/~edanaher/pslife/) written in
Poscript

- An interesting 
  [proof](https://nixwindows.wordpress.com/2018/03/13/ed1-is-turing-complete/ 
) showing that [ed, the standard text
  editor](http://wiki.c2.com/?EdIsTheStandardTextEditor) is indeed
Turing-complete 

## License

This program is (c) 2018 Vincenzo (KatolaZ) Nicosia. You can use,
modify, and redistribute it under the terms of the GNU General Public
License, either Version 3 of the License or, at your option, any later
version.
