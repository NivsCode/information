### Debugger Interrupt
`import code; code.interact(local=dict(globals(), **locals()))`
### To run the dev server
`python manage.py runserver `
- Helps other users access the url, this cmd will force the server to respond to incoming requests on TCP 5555
- TCP ports under 1024 are all privileged by OS
`python manage.py runserver <your_machines_ip_address>:5555`

### To create and make db migrations
`python manage.py makemigrations`
`python manage.py migrate`

### To create a new project (w/o docker) from projects folder
`django-admin.py startproject <project name>`

### To create an app
`python manage.py startapp <app name>`
- The project should be notified of the app's existence. which is done by adding the `<app name>` to settings.py file under `INSTALLED_APPS` section/ tuple.

### To create a super user
```
python manage.py createsuperuser
pipenv run python manage.py createsuperuser
```

### To run test cases
`python manage.py test` to run all test cases
`python manage.py test invoice.tests.ClientDetailTest.test_clients_update_address` for specific test cases


# Tags
#cheatsheet 