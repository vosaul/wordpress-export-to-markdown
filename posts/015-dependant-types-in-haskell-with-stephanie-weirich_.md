---
title: "Dependent Types in Haskell with Stephanie Weirich"
date: "2018-06-13"
---

At Strange Loop 2017, I wandered into a talk where I saw some code that deeply surprised me. The code could have been python if you squinted, passing dictionaries around, no type annotations anywhere.

Yet, key lookup in the dictionary was validated at compile time. It was a compile-time error to access elements that didn't exist. Also, the dictionary was heterogeneous, the elements had different types, and it was all inferred and validated at compile time.

What I was seeing was Dependent types in Haskell. In today's interview, Stephanie Weirich explains her efforts to add dependent types to Haskell and how that example worked.

[Podcast Transcript](https://corecursive.com/015-dependant-types-in-haskell-with-stephanie-weirich)

 

- [Dependent Types in Haskell Talk](https://thestrangeloop.com/2017/dependent-types-in-haskell.html)
- [https://www.cis.upenn.edu/~sweirich/](https://www.cis.upenn.edu/~sweirich/)
- [https://github.com/sweirich](https://www.youtube.com/watch?v=wNa3MMbhwS4 "Dependant Types in Haskell Talk ")
- [@fancytypes](http://twitter.com/fancytypes)
- [Dependent Types Regex](https://github.com/sweirich/dth/tree/master/regexp)
