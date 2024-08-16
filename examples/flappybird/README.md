# Flappy Bird

    by Max00355
    via https://github.com/Max00355/FlappyBird
    ported to pgzero by Daniel Pope

**2024-08-13 fixed the highscore bug by Naohiro2g**

## Story about the highscore bug

When you run flappybird.py of the original Pygame Zero repository as of 2024-08-13 or earlier, you will get the following error message:
```NameError: name 'storage' is not defined```

What is it and why, and how to fix it?

### The reason for the error

flappybird.py uses the ```storage``` module to save the highscore into the file system of PC but there is no such module in the latest released version of pgzero package(Pygame) at Pypi.org. It's so simple.

### Where is the storage module, or ```storage.py```??

Again, the question is simple, too.
It is included in the source code of pgzero at GitHub(here) to be released in the future version of 1.2.2, 1.3.0, or like that. But the development of pgzero seems to be stopped suddenly. The last commit was made on Jun 30, 2022 and the last release was 1.2.1 on March 3, 2021.
https://pypi.org/project/pgzero/#history

### How could it be fixed?

A. Use simpler way to save the highscore using the dictionary instead of the storage module.
B. Ignore the highscore feature and remove some lines from the code.
C. Put the ```storage.py``` in the same directory of ```flappybird.py``` and fix the code to use it.
D. Fix the codes and upload the new version of pgzero package to Pypi.org.

Plan A is simple and the easiest to do. Only one line of the code is needed to be changed like this:

```python
# storage.setdefault('highscore', 0)
storage = {'highscore': 0}
```
It uses the dictionary instead of the storage module, but the highscore is not carried after the game is closed. The dictionary is one of the basic feature of Python in the standard library.

Plan B is not good, because it not just loses the highscore feature but also lines to be edited increase.

Plan C is the way I chose. I put the storage.py in the directory of flappybird.py and fixed the code to use it. The highscore is saved in the file and it is carried after the game is closed. The storage.py was not finalized, so I had to fix it to work with flappybird.py. The highscore is saved in the file named like ```~/AppData\Roaming\pgzero\flappybird-804034bc.json``` on Windows.

Finally, Plan D is the most thorough solution, but it is not easy and will take time to complete.
