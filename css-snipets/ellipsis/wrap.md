
##word-wrap
The word-wrap CSS property is used to specify whether or not the browser may break lines within words in order to prevent overflow (in other words, force wrapping) when an otherwise unbreakable string is too long to fit in its containing box.
###normal
Indicates that lines may only break at normal word break points.
###break-word
Indicates that normally unbreakable words may be broken at arbitrary points if there are no otherwise acceptable break points in the line.


##word-break
The word-break CSS property is used to specify how (or if) to break lines within words.

###normal
Use the default line break rule.
###break-all
Word breaks may be inserted between any character for non-CJK (Chinese/Japanese/Korean) text.
###keep-all
Don't allow word breaks for CJK text.  Non-CJK text behavior is same as normal.

##white-space
The white-space CSS property is used to to describe how whitespace inside the element is handled.
###normal
Sequences of whitespace are collapsed. Newline characters in the source are handled as other whitespace. Breaks lines as necessary to fill line boxes.
###nowrap
Collapses whitespace as for normal, but suppresses line breaks (text wrapping) within text.
###pre
Sequences of whitespace are preserved, lines are only broken at newline characters in the source and at <br> elements.
###pre-wrap
Sequences of whitespace are preserved. Lines are broken at newline characters, at <br>, and as necessary to fill line boxes.
###pre-line
Sequences of whitespace are collapsed. Lines are broken at newline characters, at <br>, and as necessary to fill line boxes.


## Referers
* https://developer.mozilla.org/en-US/docs/Web/CSS/word-wrap
* https://developer.mozilla.org/en-US/docs/Web/CSS/word-break
* https://developer.mozilla.org/en-US/docs/Web/CSS/white-space
* http://www.w3school.com.cn/cssref/index.asp
