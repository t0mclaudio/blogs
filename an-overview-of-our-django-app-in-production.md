# How I set up our Django Application on a production server?

This is an overview of how we set up our Django application on a virtual private server running Ubuntu 14.

First, we need to set up a virtual environment where our application and dependencies will run. Isolating the app to a virtual environment prevents it from running into conflict with the system installed Python and libraries.

We also need to install MySQL and Redis servers on the same VPS and configure Django to use a socket connection to communicate with these services.

While Django can spawn a web server intended for local testing, it is not recommended for production because it is unable to handle multiple requests and has no security features expected that of a production-grade web server. This means that we need to install a web server that can handle our requirement to accept Http/s requests from the world wide web. For this set up we will be using Nginx.

Now that we can accept and respond to Http/s requests, we need to configure Nginx to forward these requests to Django for processing. However, Nginx can not  interface directly with Django and other python applications. This is where Gunicorn, an application server, comes in. An application server acts as proxy between Nginx and Django.

By this time, we can route requests/responses between client and app. We only need to start the application and services.

Sometimes things happen to cause applications or services in the server crash or shutdown. Manually restarting everything is a tedious process and unreliable. We use a utility called Supervisored to automate restarting the app and services. This is a convenient server utility to make sure the whole service is running.
Additionally, resources such as photos, videos, etc are hosted on a separate content delivery network provider. This reduces disk usage and bandwidth consumption on our server. We also use API services provided by third-party vendors such as for sending transactional emails and logging.

So that is how we set up our monolithic Django Application.
