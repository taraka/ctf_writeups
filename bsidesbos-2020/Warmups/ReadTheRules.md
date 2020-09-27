# Read the Rules

```
Please follow the rules for this CTF!

Connect here:
https://bsidesbos.ctf.games/rules
```

When we go to the web page we don't see the flag as rendered by the browser.

Looking in the source for the page we find the flag in a HTML comment

We can retrive the flag with the following oneliner 

`curl -s https://bsidesbos.ctf.games/rules | grep -Eo 'flag{[^}]+}'`