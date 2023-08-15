# Concurrency and Parallelism in Python

## Table of Contents

- [Concurrency and Parallelism in Python](#concurrency-and-parallelism-in-python)
  - [Table of Contents](#table-of-contents)
  - [Part 1: Introduction to Concurrency](#part-1-introduction-to-concurrency)
    - [1. Global Interpreter Lock (GIL) Explained](#1-global-interpreter-lock-gil-explained)
    - [2. Threading in Python](#2-threading-in-python)

---

## Part 1: Introduction to Concurrency

In this section, we'll explore the fundamental concepts of concurrency in Python, including the Global Interpreter Lock (GIL) and the `threading` module.

### 1. Global Interpreter Lock (GIL) Explained

The Global Interpreter Lock (GIL) is a mutex that prevents multiple native threads from executing Python bytecodes simultaneously in a single process. While it ensures memory safety, it can limit the parallelism of CPU-bound tasks. In this example, we'll create two threads to perform counting concurrently, but due to the GIL, they won't achieve true parallelism.

```python
import threading

def count_up():
    for _ in range(1000000):
        pass

def count_down():
    for _ in range(1000000):
        pass

thread1 = threading.Thread(target=count_up)
thread2 = threading.Thread(target=count_down)

thread1.start()
thread2.start()

thread1.join()
thread2.join()

print("Counting done!")
```

### 2. Threading in Python

The threading module allows us to work with threads in Python. In this example, we're using a lock (threading.Lock()) to synchronize access to a shared variable (x) across multiple threads. This ensures that only one thread modifies x at a time, preventing data corruption.

```python

import threading

x = 0
lock = threading.Lock()

def increment():
    global x
    for _ in range(1000000):
        with lock:
            x += 1

def decrement():
    global x
    for _ in range(1000000):
        with lock:
            x -= 1

thread1 = threading.Thread(target=increment)
thread2 = threading.Thread(target=decrement)

thread1.start()
thread2.start()

thread1.join()
thread2.join()

print("Result:", x)
``````

[Continue to Part 2: Asynchronous Programming with asyncio](asynchronous.md)