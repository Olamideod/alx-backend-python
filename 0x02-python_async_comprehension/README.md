```
# 0x02. Python - Async Comprehension

## Description
This project focuses on understanding and implementing asynchronous programming in Python. Specifically, it covers asynchronous generators and comprehensions, which are powerful features introduced in Python 3.6 and 3.7. By the end of this project, you should be able to write and use asynchronous generators, comprehend async comprehensions, and apply type annotations for async generators.

## Learning Objectives
- How to write an asynchronous generator
- How to use async comprehensions
- How to type-annotate generators

## Requirements
- **Editors**: vi, vim, emacs
- **Interpreter**: Python 3.7 on Ubuntu 18.04 LTS
- **Coding Style**: pycodestyle (version 2.5.x)
- **Documentation**: All modules, functions, and coroutines must have appropriate documentation

## Tasks

### Task 0: Async Generator
Write a coroutine called `async_generator` that takes no arguments. This coroutine should loop 10 times, each time asynchronously waiting 1 second, then yielding a random number between 0 and 10.

**File**: `0-async_generator.py`

```python
#!/usr/bin/env python3
import asyncio
import random
from typing import Generator

async def async_generator() -> Generator[float, None, None]:
    """Yield a random number between 0 and 10 asynchronously."""
    for _ in range(10):
        await asyncio.sleep(1)
        yield random.uniform(0, 10)
```

### Task 1: Async Comprehensions
Import `async_generator` from the previous task and then write a coroutine called `async_comprehension` that takes no arguments. The coroutine should collect 10 random numbers using an async comprehension over `async_generator`, then return these 10 random numbers.

**File**: `1-async_comprehension.py`

```python
#!/usr/bin/env python3
import asyncio
from typing import List
from 0_async_generator import async_generator

async def async_comprehension() -> List[float]:
    """Collect 10 random numbers from async_generator."""
    return [num async for num in async_generator()]
```

### Task 2: Run Time for Four Parallel Comprehensions
Import `async_comprehension` from the previous file and write a coroutine called `measure_runtime` that will execute `async_comprehension` four times in parallel using `asyncio.gather`. Measure and return the total runtime.

**File**: `2-measure_runtime.py`

```python
#!/usr/bin/env python3
import asyncio
import time
from 1_async_comprehension import async_comprehension

async def measure_runtime() -> float:
    """Measure the runtime of executing async_comprehension four times in parallel."""
    start_time = time.time()
    await asyncio.gather(*(async_comprehension() for _ in range(4)))
    return time.time() - start_time
```

## How to Use
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/alx-backend-python.git
    cd alx-backend-python/0x02-python_async_comprehension
    ```
2. Run the provided main scripts to see the results:
    ```bash
    ./0-main.py
    ./1-main.py
    ./2-main.py
    ```

## License
This project is licensed under the MIT License.

## Author
[Olamide David Oluwamusiwa]
```

