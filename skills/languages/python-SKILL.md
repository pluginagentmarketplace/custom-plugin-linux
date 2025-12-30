---
name: python
description: Python development skill - Modern Python 3.11+, type hints, async, data processing
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [code, debug, explain, optimize, review] }
    context: { type: string }
    code_snippet: { type: string }
  required: [task]

output_schema:
  type: object
  properties:
    solution: { type: string }
    explanation: { type: string }
    best_practices: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential
  initial_delay_ms: 1000

timeout_ms: 30000
---

# Python Skill

## PURPOSE
Atomic skill for Python development with modern best practices.

## CORE COMPETENCIES
```
Python 3.11+ Features:
├── Type hints (typing module)
├── dataclasses
├── Pattern matching (match/case)
├── Exception groups
└── Performance improvements

Async Python:
├── asyncio
├── async/await
├── aiohttp, httpx
├── Concurrent.futures
└── Event loops

Data Processing:
├── Pandas, Polars
├── NumPy
├── List comprehensions
├── Generators
└── Context managers
```

## CODE PATTERNS

### Type-Safe Function
```python
from typing import TypeVar, Callable, Optional
from functools import wraps
import logging

T = TypeVar('T')

def with_retry(
    max_attempts: int = 3,
    delay: float = 1.0,
    backoff: float = 2.0
) -> Callable[[Callable[..., T]], Callable[..., T]]:
    def decorator(func: Callable[..., T]) -> Callable[..., T]:
        @wraps(func)
        def wrapper(*args, **kwargs) -> T:
            last_exception: Optional[Exception] = None
            current_delay = delay

            for attempt in range(max_attempts):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    last_exception = e
                    logging.warning(f"Attempt {attempt + 1} failed: {e}")
                    if attempt < max_attempts - 1:
                        time.sleep(current_delay)
                        current_delay *= backoff

            raise last_exception
        return wrapper
    return decorator
```

### Dataclass Pattern
```python
from dataclasses import dataclass, field
from typing import List, Optional
from datetime import datetime

@dataclass
class APIResponse:
    data: dict
    status_code: int
    timestamp: datetime = field(default_factory=datetime.now)
    errors: List[str] = field(default_factory=list)

    @property
    def is_success(self) -> bool:
        return 200 <= self.status_code < 300
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| ImportError | Missing package | `pip install package` or check venv |
| IndentationError | Mixed tabs/spaces | Use consistent indentation |
| MemoryError | Large dataset | Use generators, chunking |
| GIL bottleneck | CPU-bound | Use multiprocessing |

## TESTING TEMPLATE
```python
import pytest
from unittest.mock import Mock, patch

class TestFunction:
    def test_normal_input(self):
        result = function("input")
        assert result == "expected"

    def test_invalid_input(self):
        with pytest.raises(ValueError):
            function(None)

    @pytest.mark.asyncio
    async def test_async_operation(self):
        result = await async_function()
        assert result is not None

    @patch('module.external_call')
    def test_with_mock(self, mock_call):
        mock_call.return_value = "mocked"
        result = function_using_external()
        assert result == "mocked"
```

## OBSERVABILITY
```python
import logging
import functools
import time

def log_execution(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        logger = logging.getLogger(func.__module__)
        logger.info(f"Calling {func.__name__}")
        start = time.perf_counter()
        try:
            result = func(*args, **kwargs)
            elapsed = time.perf_counter() - start
            logger.info(f"{func.__name__} completed in {elapsed:.3f}s")
            return result
        except Exception as e:
            logger.error(f"{func.__name__} failed: {e}")
            raise
    return wrapper
```
