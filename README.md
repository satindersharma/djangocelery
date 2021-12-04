# Django Celery


## Which was complicated
#### https://redis.com/blog/redis-on-windows-10/


## Thus following this
#### https://simpleisbetterthancomplex.com/tutorial/2017/08/20/how-to-use-celery-with-django.html


#### https://www.rabbitmq.com/install-windows.html


## Download the latest rlang(exe file)
#### https://github.com/erlang/otp/releases/
##### (like ) https://github.com/erlang/otp/releases/download/OTP-24.1.7/otp_win64_24.1.7.exe


## download the latest RabbitMQ exe file
#### https://github.com/rabbitmq/rabbitmq-server/releases/

#### (like )https://github.com/rabbitmq/rabbitmq-server/releases/download/v3.9.11/rabbitmq-server-3.9.11.exe



## Add this to your path to use
#### `C:\Program Files\RabbitMQ Server\rabbitmq_server-3.9.10\sbin`



## To use cli 

#### https://rabbitmq.com/management-cli.html



### `rabbitmqctl help`
### `rabbitmq-diagnostics help status`


## To see the status
### `rabbitmq-diagnostics status`


## `pip install celery`
### `celery --help`


#### `settings.py`
```python
CELERY_BROKER_URL = 'amqp://localhost'
```
#### https://docs.celeryproject.org/en/stable/userguide/configuration.html#new-lowercase-settings



### Where mysite is the name of project
#### https://docs.celeryproject.org/en/stable/django/first-steps-with-django.html
#### `celery.py`
```python
import os
from celery import Celery

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'mysite.settings')

app = Celery('mysite')
app.config_from_object('django.conf:settings', namespace='CELERY')
app.autodiscover_tasks()
```


### Now edit the __init__.py file in the project root:
#### `__init__.py`


```python
from .celery import app as celery_app

__all__ = ['celery_app']
```




## Now create `tasks.py` in your any app and celery will detect that automaticaly


## Install celery beat and 
#### https://docs.celeryproject.org/en/stable/django/first-steps-with-django.html#extensions
##  how to start the Celery worker process.
#### where mysite is the project name (Celery('mysite'))
### `celery -A mysite worker -l info`



#### https://medium.com/@rijinswaminathan/use-celery-and-rabbitmq-with-django-rest-api-d803681d8c86


## To start rabbitmq
### `rabbitmqctl start_app`


## To see status
### `rabbitmqctl stop_app`


## To see status
### `rabbitmqctl status`


## Celery Commands
#### https://docs.celeryproject.org/en/stable/userguide/monitoring.html#guide-monitoring





## Celery settings for django
#### https://docs.celeryproject.org/en/stable/userguide/configuration.html#new-lowercase-settings


### https://docs.celeryproject.org/en/stable/django/first-steps-with-django.html#extensions

## Celery
### `celery -A ZKTecoProject worker -l info`

### `celery -A ZKTecoProject status`

#### https://docs.celeryproject.org/en/stable/userguide/monitoring.html#flower-real-time-celery-web-monitor

### `pip install flower`

### `celery -A ZKTecoProject flower`

## Now you can watch task at 
### http://localhost:5555


## Inspect Queues
#### `rabbitmqctl list_queues name messages messages_ready messages_unacknowledged`




## To Shedule a task we need a custom sheduler which makes it easy to shedule from admin
#### https://docs.celeryproject.org/en/latest/userguide/periodic-tasks.html#using-custom-scheduler-classes


#### https://www.caktusgroup.com/blog/2021/08/11/using-celery-scheduling-tasks/



### `celery -A ZKTecoProject beat`


#### https://docs.celeryproject.org/en/latest/reference/cli.html?#celery-control

### `celery -A ZKTecoProject control shutdown`

### `celery -A ZKTecoProject control enable_events`

### `celery -A ZKTecoProject control disable_events`


### `celery -A ZKTecoProject worker -l info -B`



`python manage.py shell`
```python
from django_celery_beat.models import PeriodicTask
PeriodicTask.objects.update(last_run_at=None)
```


### start cmds
### `rabbitmqctl shutdown`
### `rabbitmqctl reset`
### `rabbitmqctl stop`
### `rabbitmqctl stop_app`
### `rabbitmqctl start_app`
### `celery -A ZKTecoProject purge`
### `celery -A ZKTecoProject worker -l info`
### `celery -A ZKTecoProject beat`
### `celery -A ZKTecoProject flower`
