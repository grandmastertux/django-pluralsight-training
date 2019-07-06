
# django-pluralsight-training

Django Pluralsight Training - Django Fundamentals

Issues in starting off the Training:

    Issue 1

    PS P:\Python\django\django-pluralsight-training\django-fundamentals-course> python -m venv django-env
        Error: [Errno 2] No such file or directory: 'C:\\dev\\anaconda3\\lib\\venv\\scripts\\nt\\python.exe'

    Came across this Stackoverflow answer - https://stackoverflow.com/questions/55380296/how-to-fix-error-errno-2-no-such-file-or-directory-c-program-files-pytho
        conda remove anaconda
        conda update python
        conda list --show-channel-urls | findstr python
        python -m venv django-env

    Which solved this issue.

    Issue 2

    PS P:\Python\django\django-pluralsight-training\django-fundamentals-course> .\django-env\Scripts\Activate.ps1           
    .\django-env\Scripts\Activate.ps1 : File                                                                                P:\Python\django\django-pluralsight-training\django-fundamentals-course\django-env\Scripts\Activate.ps1 cannot be 
    loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at  
    https:/go.microsoft.com/fwlink/?LinkID=135170. 
    At line:1 char:1 + .\django-env\Scripts\Activate.ps1 
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        + FullyQualifiedErrorId : UnauthorizedAccess
    
    By opening the Powershell (Run As Administrator) and running the following:
        PS P:\Python\django\django-pluralsight-training\django-fundamentals-course> Get-ExecutionPolicy
        Restricted 
        PS P:\Python\django\django-pluralsight-training\django-fundamentals-course> Set-ExecutionPolicy -ExecutionPolicy Unrestricted
        PS P:\Python\django\django-pluralsight-training\django-fundamentals-course> Get-ExecutionPolicy -List                                                                   Scope ExecutionPolicy
        ----- ---------------                                                                                           
        MachinePolicy       Undefined
        UserPolicy          Undefined
        Process             Undefined
        CurrentUser         RemoteSigned
        LocalMachine        Undefined

    I can then go back to the original PowerShell (non-admin) terminal and run the following:
    PS P:\Python\django\django-pluralsight-training\django-fundamentals-course> .\django-env\Scripts\Activate.ps1           
    (django-env) PS P:\Python\django\django-pluralsight-training\django-fundamentals-course>

    pip install django

    NOTE: If I need a different version of django then I would run
        pip install django==1.9

    django-admin startproject tictactoe
    cd .\tictactoe
    python.exe .\manage.py runserver

    Files of interest created in the new project:
        1. settings.py = how the project is defined to configure the project
        2. urls.py = assigns URL's to the various pages
        3. wsgi.py = used for deploying to a production server
    
    urls.py
        path(r'^welcome$',welcome) - (regex of the url, name of the view function)
            If only using the carrot at the beginning it would force that is had to start with welcome
            If only using the dollar sign at the end, it would force that had to end with welcome
            If using both, it would need to be an exact match of welcome
            If not using either, then any url that contains welcome will work
            If we want welcome to be at the root URL, then keep carrot and dollar sign and remove the word welcome

    When creating a new project, predefined apps will be included with your django project.
    Migrations are Django’s way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema. 
        python.exe .\manage.py showmigrations - Show pending/applied migrations
        python.exe .\manage.py migrate - runs all pending migrations
    
    python.exe .\manage.py startapp gameplay
        admin.py - configure django admin interface
        apps.py - configures the app itself
        models.py - model classes for this app
        tests.py - unit testing
        views.py - gameplay views
        __init__.py - makes this into a Python package

    After updating models.py then run - python.exe .\manage.py makemigrations
    To see the SQL that will be created independent of the platform run - python.exe .\manage.py sqlmigrate gameplay 0001
    After making changes to the model.py run - python.exe .\manage.py makemigrations and then python.exe .\manage.py migrate

    #Step 1: Change Model Code
    #Step 2: Generate Migration Script (check it!)
        python.exe .\manage.py makemigrations
    #Optional: Show Migrations
        python.exe .\manage.py showmigrations
    #Optional: Show SQL for specific migration
        python.exe .\manage.py sqlmigrate appname(gameplay) migrationame(0001)
    #Step 3: Run Migrations
        python.exe .\manage.py migrate


    -------------------------------------
    Enabled the Admin interface already and creating a super user by doing:
        python.exe .\manage.py createsuperuser
    Starting a shell for your current project
        python.exe .\manage.py shell

    In this tutorial we created a Game Model
        Game.objects = (class attribute objects)
        Game.objects.get(pk=5) = get() returns a single instance and will throw an exception when no matched or more than 1 match occurs
        Game.objects.all() = all() returns all rows
        Game.objects.filter(status='A') = filter() returns matching objects
                                          exclude() does the opposite 

    -------------------------------------
    
