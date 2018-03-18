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

_Hint 1_: If you enable the "Watch File" option in `gv`, you will get a
nice slideshow, for some definition of nice.

_Hint 2_: Running `gv` with `-nosafer -nodirsafe` might be a very bad
idea.

## WTF?

Postscript is a Turing-complete language. This means that you can
perform any feasible computation in Postscript. Hence, simulating a
random walk in Postscript is not a big fuss at all, also because the
standard Postscript definition already includes a pseudo-random number
generator, so you don't need to implement it yourself. The only problem
is that the pseudo-random number generator needs to be initialised with
a new seed, otherwise you would always visualise the _same_ trajectory.   

The simple solution implemented in `psrw.ps` is to store the seed in the
same file as a comment, and _update_ it at each run.  In practice,
`psrw.ps` rewrites a slightly modified copy of itself every time you
"view" it, but a user would hardly notice it :-)

## Why?

Well, you don't need a particular reason to write anything like
`psrw.ps`. I just tried to do something similar around 2001 or 2002,
when I was using Postscript quite heavily, and at that time I did not
find a proper way through.  So the simplicity of the solution
implemented in `psrw.ps` scratches a long-standing personal itch, and
tells a lot about my very poor understanding of Postscript...

## No seriously, WHY?

I just wanted to make a point about (not) trusting documents written in
formats that you don't understand, or that are not freely accessible or
are poorly or not documented.  

Many _text_ formats out there are Turing-complete or close-to, and some
viewers  (e.g., for PDF or OpenXML files) include interpreters for other
Turing-complete languages (like Javascript or VBScript). This mean that
these viewers can do almost anything when you "_open_" those "_text_"
files. The only chance you have is to understand what is going on behind
the scenes, or to trust the company that provided the smart viewer. But
can you really trust _them_? 

If it was so easy for a Postscript illiterate like me to craft a
document that modifies itself by changing _something_ that you cannot
even visualise, what else can be done by "_text_" files saved in
proprietary formats?

Well, at this point you should start thinking that you cannot really
_trust me_ either, even if I sweared that `psrw.ps` does absolutely
nothing nasty when you "open" it. But how can you be sure I am telling
the truth? ;-) 


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
