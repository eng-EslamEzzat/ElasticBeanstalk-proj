# AWS Elastic Beanstalk Express Sample App
This sample application uses the [django](https://www.djangoproject.com/) framework to build a simple, scalable django app that is deployed to [AWS Elastic Beanstalk](http://aws.amazon.com/elasticbeanstalk/).

## Prerequisites

- `Python 3.7 or later`
- `pip`
- `pipenv` *for vertual env*
- `awsebcli`


## Activate a Python virtual environment and install Django

1. activate the virtual environment: python.
    
    `pipenv shell`

2. install the requirements. 

    `pip install -r requirements.txt`

3. deactivate the environment.
    
    `deactivate`


## Deploy the project with the EB CLI

1. Initialize your EB CLI repository with the eb init command.

    `eb init -p python-3.8 djangoproj`

2. Create an environment and deploy your application to it with eb create.

    `eb create djangoproj-env`

3. Find the domain name of your new environment.

    `eb status`

    ```
    Environment details for: django-env
    Application name: django-tutorial
    ...
    CNAME: eb-django-app-dev.elasticbeanstalk.com
    ...
    ```

4. Open the `settings.py` file in the ebdjango directory. Locate the `ALLOWED_HOSTS` setting, and then add your application's domain name that you found in the previous step to the setting's value. If you can't find this setting in the file, add it to a new line.

    ```
    ALLOWED_HOSTS = ['eb-django-app-dev.elasticbeanstalk.com']
    ```

5. Save the file, and then deploy your application.

    `eb deploy`

6. When the environment update process completes, open your website.

    `eb open`
    
- If you want to opens the environment in the AWS Elastic Beanstalk Management Console.

    `eb console`

- If there are any issues you can show the logs by. 

    `eb logs`
