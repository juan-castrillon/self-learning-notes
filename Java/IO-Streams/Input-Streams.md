# Input Streams

As a rule, every program consumes some data as a way to communicate with the outer world. It can be a user's input from a console, configuration file, or something else. Java has a common mechanism for consuming data called input streams. We have already provided some text as data for our programs, and now it is time to dive deeper and explore the whole mechanism.

## Sources

Data can be obtained from many points considered as providers. Besides standard input or file, those can be network connections, in-memory buffers, or even objects. All of them are called sources for input streams. In fact, a source is any data that can be consumed and processed by a program.

Since the implementation of a particular source consuming is quite specific, each source needs a specialized class.

## Character streams

There are several classes for reading text. They are called character input streams and allow reading text data: `char` or `String`. For instance, there are `FileReader`, `CharArrayReader`, `StringReader`, and etc.

> The class name indicates what type of source it uses as input and usually ends with `Reader`, since all such classes extend `java.io.Reader` class.

Each class provides a set of useful methods while they also have common methods for reading data:

- `int read()` reads a single character. If end of stream is reached, the method returns `-1` value. Otherwise, it returns the numerical representation of character according to encoding;
- `int read(char[] cbuf)` reads a sequence of characters into passed array up to its capacity and returns a number of characters that were actually read. It can also return `-1` in case of no data was read;
- `int read(char[] cbuf, int off, int len)` reads characters into a portion of array.

These methods return a number of characters that were actually read or `-1`. They also block program running until some input is available, the end of stream is reached.

Another important method is void `close()` that should be invoked after a stream was used.

## Example of a character stream

Let's consider `FileReader` as an example of the `Reader` classes. `FileReader` has a set of constructors. Here are some of them:

- `new FileReader(String fileName)`
- `new FileReader(String fileName, Charset charset)`
- `new FileReader(File file)`
- `new FileReader(File file, Charset charset)`

As you can see, it can read text data from the file indicated either by path `String` or as a `File` object.

> A charset is a class that declares encoding from sequences of bytes to characters. By default, java uses UTF-16 encoding, suitable for most tasks. However, sometimes the file may have another encoding and you'll have to use a different charset to read the content of the file properly.

Now let's try to read a file. Say we have a `file.txt` with the following content: `input stream`.

```java
Reader reader = new FileReader("file.txt");

char first = (char) reader.read(); // i
char second = (char) reader.read(); // n

char[] others = new char[12];
int number = reader.read(others); // 10
```

After running the code, the `others` will contain `['p', 'u', 't', ' ', 's', 't', 'r', 'e', 'a', 'm', '\u0000', '\u0000']`.

Let's explain the result. Since we've read the first two letters into other variables, the first 10 characters of others are filled starting from the third letter. When stream reached the end of the file it stopped reading, so the last two characters are not updated.

When you create an empty array it is actually filled with default values, which are `'\u0000'` for `char` array. This is a reason why the last 2 elements of others are `'\u0000'`.

The tricky thing here is that `'\u0000'` is interpreted as an empty symbol and not displayed at all, although technically it is present. Remember that when you read data into an array.

Another common way of reading text data stream is to read it `char` by `char` until the stream is not closed:

```java
FileReader reader = new FileReader("file.txt");

int charAsNumber = reader.read();
while(charAsNumber != -1) {
    char character = (char) charAsNumber;
    System.out.print(character);
    charAsNumber = reader.read();
}
reader.close();
```

When `-1` is returned, it means the end of stream was reached, that is there's nothing left to read.

## Byte streams

Byte streams may seem more complicated so let's start with something you already know. To read some text data from standard input we may create a `Scanner` instance. You are familiar with the process:

```java
Scanner scanner = new Scanner(System.in);
```

`System.in` here is actually an example of the byte input stream. There are other specialized byte streams classes: `ByteArrayInputStream` is used for reading from `byte[]`, `FileInputStream` is dedicated for files, `AudioInputStream` is a way of consuming audio input and there's more.

> The class name of a byte stream indicates what type of source it uses as input and usually ends with `InputStream`, since all such classes extend `java.io.InputStreamclass`.

All byte stream classes have methods for reading similar to character input streams:

- `abstract int read()` reads a single byte
- `int read(byte[] b)` reads some number of bytes and stores them in byte array
- `byte[] readAllBytes()` reads all bytes

The method that reads bytes into an array, returns int value. It is the number of bytes that were actually read from the source. If -1 value is returned it is a sign that no bytes were read.

Each input stream class has also `void close()` method to release system resources.

## Example of a byte stream

Suppose we have `file.txt` that contains text: `input stream`. Let's read it using `FileInputStream` class. It can be created by using several constructors, such as:

- `new FileInputStream(String pathToFile)`
- `new FileInputStream(File file)`

Here we create one by specifying the name of a file:

```java
FileInputStream inputStream = new FileInputStream("myfile.txt");
```

We are going to read the first five bytes:

```java
byte[] bytes = new byte[5];
int numberOfBytes = inputStream.read(bytes);
System.out.println(numberOfBytes); // 5
inputStream.close();
```

Now `bytes` contains `['i', 'n', 'p', 'u', 't']`.

Byte by byte approach also works here, similar to character streams example.

## Testing input streams

When testing your programs in IDE, you type the text and then press Enter to push the typed text into the input stream, like when you did with Scanner. In this case, the end-of-line symbol is also appended as the last symbol of the typed sequence of characters and will be read into an array if that's what you do.

> Pressing Enter doesn't close the input stream. It is still opened and waits for input. To actually close the input stream you need to produce an end-of-file event. In IDEA, you should press Ctrl+D (Windows and Linux) or <command>+D (MacOS).

## What type of stream should I use?

The main difference between byte and character streams is that byte ones read input data as bytes while character ones work with characters.

A computer understands only sequences of bytes. From this perspective, any data is a set of bytes and byte input streams are a common way of reading any kind of data. For computers, characters are still combinations of bytes defined by charset specification.

On the contrary, as human beings, we are used to dealing with sequences of characters. Character input streams are aimed to read data which consists of characters. Under the hood, they still read bytes, but they immediately encode bytes to characters.

If you need to read a text, use character input streams. Otherwise, for example, while reading audio, video, zip and etc., use byte input streams.

## Conclusion

Input streams provide a way to read data from a source. The source is a data provider like a console or standard input, file, string, or even network connection. There are two types of sources: byte and character ones. Character input streams are intended for reading text only. Byte input streams allow reading sequences of raw bytes. Character input stream classes usually end with Reader. Similarly, byte input streams end with InputStream.