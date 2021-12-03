# djangocelery

which was complicated
https://redis.com/blog/redis-on-windows-10/

folowoing this
https://simpleisbetterthancomplex.com/tutorial/2017/08/20/how-to-use-celery-with-django.html

https://www.rabbitmq.com/install-windows.html

download the latest rlang(exe file)
https://github.com/erlang/otp/releases/
(like ) https://github.com/erlang/otp/releases/download/OTP-24.1.7/otp_win64_24.1.7.exe
download the latest exe file
https://github.com/rabbitmq/rabbitmq-server/releases/

(like )https://github.com/rabbitmq/rabbitmq-server/releases/download/v3.9.11/rabbitmq-server-3.9.11.exe


add this to your path to use
C:\Program Files\RabbitMQ Server\rabbitmq_server-3.9.10\sbin

to use cli https://rabbitmq.com/management-cli.html

`rabbitmqctl help`
`rabbitmq-diagnostics help status`

## to see the status
`rabbitmq-diagnostics status`

## `pip install celery`
## `celery --help`


`settings.py`
```python
CELERY_BROKER_URL = 'amqp://localhost'
```

### where mysite is the name of project
`celery.py`
```python
import os
from celery import Celery

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'mysite.settings')

app = Celery('mysite')
app.config_from_object('django.conf:settings', namespace='CELERY')
app.autodiscover_tasks()
```

`Now edit the __init__.py file in the project root:`
`__init__.py`

```python
from .celery import app as celery_app

__all__ = ['celery_app']
```

## Now create `tasks.py` in your any app and celery will detect that automaticaly

##  how to start the Celery worker process.
#### where mysite is the project name (Celery('mysite'))
`celery -A mysite worker -l info`



## https://medium.com/@rijinswaminathan/use-celery-and-rabbitmq-with-django-rest-api-d803681d8c86


## to start rabbitmq
### `rabbitmqctl start_app`

## TO see status
### `rabbitmqctl status`
