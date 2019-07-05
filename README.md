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