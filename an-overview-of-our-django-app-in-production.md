# An overview of our Django Application in production

This is an overview of how we set up our Django application on a virtual private server.

At the heart of the setup is the Django application itself, it uses a MySQL database to store records, a Redis server for temporarily caching frequently used records, and a Rq-worker service for queuing tasks that take time to perform.

We are running Django using a virtual environment using Python 2.3 on an Ubuntu server environment. It is a good practice not to use Python the system is using the reason we isolated the app inside a virtual environment and include project dependencies inside.

In development mode, Django can spawn its own web server for testing only.  This is discouraged to use in a production setting because of its inability to handle multiple requests and security risks compared to that of a true web server. Two popular production-grade web servers are Apache and Nginx. We use Nginx in this setup.

Nginx has the ability to communicate with some server-side applications, unfortunately, this excludes Python applications. Django, being a Python application, can not directly interface with Nginx as well. This is where an Application Server is used, it acts as a proxy between Nginx and the Django application. The application server that we used in this setup is called Gunicorn.

Now we already established the routing of requests and responses between the client and the Django App.

Sometimes things happen to cause applications or services in the server crash or shutdown. Manually restarting everything is a tedious process and unreliable. We use a utility called Supervisored to automate restarting the app and services. This is a convenient server utility to make sure the whole service is running.

Additionally, resources such as photos, videos, etc are hosted on a separate content delivery network provider. This reduces disk usage and bandwidth consumption on our server. We also use API services provided by third-party vendors such as for sending transactional emails and logging.

So that is how we set up our monolithic Django Application.
