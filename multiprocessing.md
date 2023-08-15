## Part 3: Parallelism with multiprocessing

In this section, we'll explore parallelism in Python using the multiprocessing module, which allows for concurrent execution using multiple processes.
### 1. Introduction to Parallelism

Parallelism involves executing multiple tasks simultaneously, utilizing multiple CPU cores. The multiprocessing module provides a way to achieve true parallelism by creating separate processes. In this example, we define a function square and use the multiprocessing.Pool to parallelize its execution across multiple processes.

```python
import multiprocessing

def square(number):
    return number * number

if __name__ == "__main__":
    numbers = [1, 2, 3, 4, 5]
    with multiprocessing.Pool() as pool:
        results = pool.map(square, numbers)
    print(results)

```

### 2. Using multiprocessing

The multiprocessing module allows us to create and manage processes in Python. In this example, we define a function worker_function that each process will execute. We create multiple processes and start them using the start method. Finally, we wait for all processes to finish using the join method.

```python
import multiprocessing

def worker_function(number):
    print(f"Worker process {number} is executing")

if __name__ == "__main__":
    processes = []
    for i in range(4):
        process = multiprocessing.Process(target=worker_function, args=(i,))
        processes.append(process)
        process.start()

    for process in processes:
        process.join()

    print("All processes have finished")

```

[Continue to Part 4: Combining Concurrency and Parallelism](combining.md)