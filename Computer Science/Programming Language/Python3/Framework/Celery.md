---
alias: []
tags: []
---

# Celery
----
## Starting the worker

```bash
celery -A proj worker -l INFO
```

## Background workers
```bash
celery multi start w1 -A proj -l INFO
```

### Restart Background workers
```bash
celery  multi restart w1 -A proj -l INFO
```

### Stop Background workers
```bash
celery multi stop w1 -A proj -l INFO
```

### Wait and Stop Background workers
```bash
celery multi stopwait w1 -A proj -l INFO
```

## Logging
```bash
mkdir -p /var/run/celery
mkdir -p /var/log/celery
celery multi start w1 -A proj -l INFO --pidfile=/var/run/celery/%n.pid \
                                        --logfile=/var/log/celery/%n%I.log
```

## Retry Upon Fail
```python
@celery_app.task(bind=True, default_retry_delay=10 * 60)
def foo():
	return
```

## Postponed Task Execution
```python
from datetime import datetime

send_mail_task.apply_async(

(('noreply@example.com', ), 'Celery cookbook test', 'test', {}),

countdown=15 * 60

)

send_mail_task.apply_async(

(('noreply@example.com', ), 'Celery cookbook test', 'test', {}),

eta=datetime(2019, 5, 20, 7, 0)
```

## Setting Up Queues

Celery can be distributed when you have several workers on different servers that use one message queue for task planning. You can configure an additional queue for your task/worker. For example, sending emails is a critical part of your system and you don’t want any other tasks to affect the sending. Then you can add a new queue, let’s call it `mail`, and use this queue for sending emails.
```python
CELERY_TASK_ROUTES = {
'myproject.apps.mail.tasks.send_mail_task': {'queue': 'mail', },
}
```

Run two separate celery workers for the default queue and the new queue:

```bash
celery -A myproject worker -l info -Q celery
celery -A myproject worker -l info -Q mail
```

## Long-Running Tasks

It’s always better to write tasks like these in a way that allows working with data chunks. The easiest way is to add an offset and limit parameters to a task. This will allow you to indicate the size of the chunk, and the cursor to get a new chunk of data.

```python
@celery_app.task
def foo(offset=0, limit=100):
	User.objects.filter(is_active=True).order_by('id')[offset:offset + limit]
	task.delay(offset + limit, limit)
```

## Logging

```python
from celery.utils.log import get_task_logger

logger = get_task_logger(__name__)
@app.task

def add(x, y):
	logger.info('Adding {0} + {1}'.format(x, y))
	return x + y
```

## Retries

```python
@app.task(autoretry_for=(FailWhaleError,),
          retry_kwargs={'max_retries': 5})
def refresh_timeline(user):
	return
```

## Avoid Race Conditions in Django
Passing the Model Object to a task may cause race condition. Fixing this problem is easy, just use the object id instead, and re-fetch the object from database in the task body.

## Atomic Transactions
```python
@transaction.atomic
```

## Ignore Result
```python
@app.task(ignore_result=True)
```
