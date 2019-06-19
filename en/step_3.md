## Choosing a tolerance

If there are two similar colours in your image (such as a red and a dark orange), `ImageRecolor` may treat them as the same colour and change them both. To prevent this, you can set a **tolerance level**, so that a colour is only changed if it is close enough to the one you have chosen.

--- task ---

Use `ColorsNear` to set a tolerance level. (Try something small like 0.1.)

```
ImageRecolor[
myImage,
ColorsNear[<first colour>, <tolerance>] -> <second colour>
]
```

--- /task ---

--- task ---

Try setting the tolerance level to 0.1, then 0.2, ... all the way to 1.
What happens to the image?

--- /task ---