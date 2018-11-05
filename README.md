# matplotlib-flask-demo

The smallest possible demo of doing matplotlib in the context of a Flask webapp

We want to show this in a way that it will work on Heroku.  That means that we have to avoid touching the filesystem.

Fortunately, there is a feature in Python called Binary I/O.  

Binary I/O is documented on this page: <https://docs.python.org/3/library/io.html#binary-i-o>

Here is an excerpt:

<blockquote markdown="1">

Binary I/O (also called buffered I/O) expects bytes-like objects and produces bytes objects. 
No encoding, decoding, or newline translation is performed. 
This category of streams can be used for all kinds of non-text data, 
and also when manual control over the handling of text data is desired.

The easiest way to create a binary stream is with `open()` with `'b'` in the mode string:

```
f = open("myfile.jpg", "rb")
```

In-memory binary streams are also available as BytesIO objects:

```
f = io.BytesIO(b"some initial binary data: \x00\x01")
```

The binary stream API is described in detail in the docs of `BufferedIOBase`.

Other library modules may provide additional ways to create text or binary streams. 
See `socket.socket.makefile()` for example.
</blockquote>

This demo uses a Binary I/O object to store the `.png` output of the plot instead of writing it to the disk.

We got the code from this Stack Overflow answer, and adapated it by adding a Flask Template: <https://stackoverflow.com/questions/50728328/python-how-to-show-matplotlib-in-flask>
