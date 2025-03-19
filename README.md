# Commit 1 Reflection Notes

## Understanding the `handle_connection` Method

As I reviewed the code in `src/main.rs`, I noticed that the `handle_connection` method is responsible for handling incoming TCP connections. To better understand what's happening inside this method, I've broken it down into smaller parts.

### Step 1: Creating a `BufReader` instance

The method starts by creating a `BufReader` instance from the incoming TCP stream:
```rust
let buf_reader = BufReader::new(&mut stream);
```
According to the Rust documentation, `BufReader` is a type of reader that buffers data from an underlying reader. In this case, the underlying reader is the TCP stream. By using a `BufReader`, we can improve performance by reducing the number of reads from the underlying stream.

### Step 2: Reading lines from the stream

The `buf_reader` is then used to read lines from the stream:
```rust
let http_request: Vec<_> = buf_reader
    .lines()
    .map(|result| result.unwrap())
    .take_while(|line| !line.is_empty())
    .collect();
```
Here, we're using the `lines` method to read lines from the stream. The `map` method is used to unwrap the `Result` values returned by `lines`, and `take_while` is used to stop reading lines when an empty line is encountered. Finally, the `collect` method is used to collect the lines into a vector.

### Step 3: Printing the HTTP request

The final step is to print the HTTP request:
```rust
println!("Request: {:#?}", http_request);
```
This simply prints the collected lines to the console, prefixed with "Request: ".

### Reflection Notes

As I reviewed this code, I realized that I need to check the Rust documentation to understand the specifics of the `handle_connection` method. I've learned about the `BufReader` type and how it's used to improve performance when reading from a stream. I've also seen how the `lines` method is used to read lines from a stream, and how `map`, `take_while`, and `collect` are used to process the lines.