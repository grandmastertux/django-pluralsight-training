# django-pluralsight-training
Django Pluralsight Training - Django Fundamentals

Ran into this issue in starting off the Training:

    PS P:\Python\django\django-pluralsight-training\django-fundamentals-course> python -m venv django-env
        Error: [Errno 2] No such file or directory: 'C:\\dev\\anaconda3\\lib\\venv\\scripts\\nt\\python.exe'

    Came across this Stackoverflow answer - https://stackoverflow.com/questions/55380296/how-to-fix-error-errno-2-no-such-file-or-directory-c-program-files-pytho
        conda remove anaconda
        conda update python
        conda list --show-channel-urls | findstr python
        python -m venv django-env

    Which solved this issue.

