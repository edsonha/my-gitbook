# Linux

& -- is to run program in the background

```text
find . -name  * -exec ls -a {} \;
```

`{}` means "the output of `find`". As in, "whatever `find` found". `find` returns the path of the file you're looking for, right? So `{}` replaces it; it's a placeholder for each file that the `find` command locates

The `\;` part is basically telling `find` "okay, I'm done with the command I wanted to execute".



