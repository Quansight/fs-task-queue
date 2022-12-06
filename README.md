# File Queue

A task queue using the filesystem as the message queue.

# CLI

Starting a worker is as simple as giving a filesystem directory where
the queue will reside.

```shell
file-queue-worker --path ./path/to/queue
```

# API

Creating a queue is as simple as supplying a directory where the queue
will reside.

```python
from file_queue import Queue

queue = Queue("path/to/queue")
```

Next we can submit/enqueue jobs to the queue.

```python
import operator

job = queue.enqueue(operator.add, 1, 2)
```

You can immediately try and fetch the result of the job or get its
status.

```python
print(job.get_status())
print(job.result)
```

You can wait on the job to finish

```python
result = job.wait()
```
