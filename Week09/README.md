学习笔记

- Difference between `ReadLine` and `ReadString`
	- `reader.ReadString('\n')`
	If you don't mind that the line could be very long (i.e. use a lot of RAM). It keeps the `\n` at the end of the string returned.
	- `reader.ReadLine()`
	If you care about limiting RAM consumption and don't mind the extra work of handling the case where the line is greater than the reader's buffer size.
  
- solve `use of closed network connection` error

	 per doc: https://golang.org/pkg/io/#Reader
	 Callers should always process the n > 0 bytes returned before considering the error err.
	 Doing so correctly handles I/O errors that happen after reading some bytes and also both of the allowed EOF behaviors.
    
  ```go
    line, err := rd.ReadString('\n')
		connChan <- line   // step 1. read line
		if err != nil {    // step 2. check error
    ...
  ```
