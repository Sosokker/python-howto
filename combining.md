## Part 4: Combining Concurrency and Parallelism

In this final section, we'll discuss how to leverage both concurrency and parallelism to optimize Python applications.
### 1. Concurrency vs. Parallelism: When to Use Which?

Concurrency is suitable for I/O-bound tasks that involve waiting, such as network requests. Parallelism is ideal for CPU-bound tasks that can be divided into smaller units of work. In some cases, combining both approaches can provide the best performance.

### 2. Real-world Application: Web Scraping with Concurrency and Parallelism

As a practical example, let's consider web scraping. We can use asynchronous programming (`asyncio`) to handle multiple requests concurrently, and then use parallelism (`multiprocessing`) to process the scraped data in parallel. This combination can significantly speed up the entire scraping process.

```python
import asyncio
import aiohttp
import multiprocessing

async def fetch_url(session, url):
    async with session.get(url) as response:
        return await response.text()

def process_data(data):
    # Process the scraped data
    pass

async def main():
    urls = ["url1", "url2", "url3"]
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        responses = await asyncio.gather(*tasks)
    
    with multiprocessing.Pool() as pool:
        processed_data = pool.map(process_data, responses)
    
    print("Processed data:", processed_data)

asyncio.run(main())
