# PART A: Code Reading & Debugging
1. Code Reading
Question A : What will be logged to the console, and why?
Answer: Will logged -> 1 0

Question B : When will double be re-computed?
Answer: When calling `double`

------------------------------------

2. Debugging
Question A : Does this code contain a bug?
Answer: Yes, it does.

Question A : If there is any bug, how would you fix it to make it safe?
Answer: Change props title like this
```
title: {
      type: String,
      required: true
    }
```
because from code example, title have probably to be undefiend

-------------------------------------