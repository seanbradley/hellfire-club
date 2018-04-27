Welcome to the Hellfire Club code repository
==================================================

Hellfire Club is a Django web application living on an Amazon EC2 instance and deployed by AWS Elastic Beanstalk.

What does that mean? It means the site is infinitely extensible, scalable, and all the assets that are part and parcel
of the site are recoverable and transferable. The code, the logo, the pictures, the copywriting--you keep them all here,
in this repository, which works like a vault. Changes to the code are pushed up from the developer's local machine to the
repository and are then automagically and instantly deployed on a machine you lease from Amazon. You always have full 
access to any part of the stack...and each and every little change made to the site by any developer is immediately deployed. 
If you lose your developer, you don't lose your site.

Django is the probably the leading website framework for purpose-built, custom e-commerce sites. It has a steeper learning 
curve than Wordpress, but runs on Python--which is more readable and more easily maintained than PHP (used by Wordpress).
Python developers familiar with Django are just as easy to find as PHP developers familiar with Wordpress. The same 
cannot be said about frameworks like Magneto, Joomla, etc.

The site does not yet have...

* any custom styling and/or artwork; a style guide is necessary to instruct your developer.
* a custom URL; DNS settings must be adjusted in the dashboard of your URL provider (recommended: GoDaddy).
* AWS IAM permissions that transfer everything on Amazon to you; Amazon is the host.
* this code should live in *your* own Github account, not mine.
 
What's Here
-----------

This sample includes:

* README.md - this file
* ebdjango/ - this directory contains your Django project files. Note that this
  directory contains a Django config file (settings.py) that includes a pre-defined
  SECRET_KEY. Before running in a production environment, you should replace this
  application key with one you generate
  (see https://docs.djangoproject.com/en/1.11/howto/deployment/checklist/#secret-key for details)
* hellfire-club/ - this directory contains your Django application files
* manage.py - this Python script is used to start your Django web application
* .ebextensions/ - this directory contains the Django configuration file that
  allows AWS Elastic Beanstalk to deploy your Django application
* buildspec.yml - this file is used by AWS CodeBuild to build and test
  your application
* requirements.txt - this file is used to install Python dependencies needed by
  the Django application


Getting Started
---------------

These directions assume you want to develop on your local computer, and not
from the Amazon EC2 instance itself. If you're on the Amazon EC2 instance, the
virtual environment is already set up for you, and you can start working on the
code.

To work on the sample code, you'll need to clone your project's repository to your
local computer. If you haven't, do that first. You can find instructions in the
AWS CodeStar user guide.

1. Create a Python virtual environment for your Django project. This virtual
   environment allows you to isolate this project and install any packages you
   need without affecting the system Python installation. At the terminal, type
   the following command:

        $ virtualenv .venv

2. Activate the virtual environment:

        $ activate ./venv/bin/activate

3. Install Python dependencies for this project:

        $ pip install -r requirements.txt

4. (Optional) Enable Django's debug mode for development:

        $ export DJANGO_DEBUG=True

5. Start the Django development server:

        $ python manage.py runserver

6. Open http://127.0.0.1:8000/ in a web browser to view your application.

What Do I Do Next?
------------------

Once you have a virtual environment running, you can start making changes to
the sample Django web application. We suggest making a small change to
/hellfire-club/templates/index.html first, so you can see how changes pushed to
your project's repository are automatically picked up and deployed to the Amazon EC2
instance by AWS Elastic Beanstalk. (You can watch the progress on your project dashboard.)
Once you've seen how that works, start developing your own code, and have fun!

To run your tests locally, go to the root directory of the sample code and run
the `python manage.py test` command, which AWS CodeBuild also runs through
your `buildspec.yml` file.

To test your new code during the release process, modify the existing tests or
add tests to the tests directory. AWS CodeBuild will run the tests during the
build stage of your project pipeline. You can find the test results
in the AWS CodeBuild console.

Learn more about AWS CodeBuild and how it builds and tests your application here:
https://docs.aws.amazon.com/codebuild/latest/userguide/concepts.html

Learn more about AWS CodeStar by reading the user guide.  Ask questions or make
suggestions on our forum.

User Guide: http://docs.aws.amazon.com/codestar/latest/userguide/welcome.html
Forum: https://forums.aws.amazon.com/forum.jspa?forumID=248

What Should I Do Before Running My Project in Production?
------------------

AWS recommends you review the security best practices recommended by the framework
author of your selected sample application before running it in production. You
should also regularly review and apply any available patches or associated security
advisories for dependencies used within your application.
