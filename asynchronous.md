## Part 2: Asynchronous Programming with asyncio

In this section, we'll dive into asynchronous programming using the asyncio module, enabling concurrent execution without relying on multiple threads.

### 1. Introduction to Asynchronous Programming

Asynchronous programming allows non-blocking execution of tasks, making efficient use of system resources. The asyncio module provides a framework for working with asynchronous operations. In this simple example, we define an asynchronous function main that prints "Hello," waits for a second using await asyncio.sleep(1), and then prints "World."

```python
import asyncio

async def main():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(main())

```

### 2. Getting Started with asyncio

To work with asyncio, we can use the async and await keywords. In this example, we define an asynchronous function fetch_data that simulates fetching data from a URL asynchronously. The asyncio.gather function is used to run multiple asynchronous tasks concurrently and gather their results.

```python
import asyncio

async def fetch_data(url):
    # Simulate fetching data from a URL
    await asyncio.sleep(2)
    return f"Data from {url}"

async def main():
    tasks = [fetch_data("url1"), fetch_data("url2"), fetch_data("url3")]
    results = await asyncio.gather(*tasks)
    print(results)

asyncio.run(main())

```

[Continue to Part 3: Parallelism with multiprocessing](multiprocessing.md)