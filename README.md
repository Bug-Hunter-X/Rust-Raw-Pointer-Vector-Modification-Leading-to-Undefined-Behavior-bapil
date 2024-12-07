# Rust Raw Pointer Vector Modification Leading to Undefined Behavior

This repository demonstrates a common error in Rust involving the unsafe use of raw pointers with vectors.  The code modifies a vector through a raw pointer after the vector might have been reallocated, resulting in undefined behavior.

The `bug.rs` file contains the erroneous code.  The `bugSolution.rs` file provides a corrected version which avoids this pitfall using safe Rust methods.

**Understanding the Problem:**

Rust's ownership and borrowing system prevents many common memory-related errors. However, using `unsafe` code can bypass these safety guarantees.  In this example, obtaining a raw pointer using `as_mut_ptr()` gives you direct access to the vector's memory.  If the vector needs to grow, its internal memory might be reallocated, invalidating the raw pointer. Attempting to dereference the invalid pointer leads to unpredictable behavior.

**Solution:**

The corrected version avoids raw pointers entirely, using safe and idiomatic Rust methods to modify the vector's contents.

This example highlights the importance of careful consideration when working with `unsafe` code in Rust.  Always favor safe alternatives whenever possible.