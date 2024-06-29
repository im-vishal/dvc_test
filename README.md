dvc_test
==============================

#### Steps for DVC + Git tracking:
    1. Cookiecutter Template
        a. cookiecutter -c v1 https://github.com/drivendata/cookiecutter-data-science
        b. Git int    -- initialize git repository
        c. Add "-e ." in requirements.txt
        d. Dvc init
        e. Git first commit - git & dvc initialized
        f. dvc remote add -d myremote tmp
        g. Git second commit - dvc remote added
        h. Dvc install     -- optional
        i. Add data to data/raw folder
        j. Add this to track .dvc file in .gitignore - 
        !data/*.dvc
        k. Dvc add data/raw     # adding data folder to dvc for data versioning
            Optional:
            i. If data is already tracked through Git:
                1) Stop tracking from Git:
                Git rm -r --cached 'data'
                2) Commit this change:
                Git commit -m "stop tracking data"
        l. Dvc push
        m. git add .    -- to add all to staging
        n. Git commit
        o. Git push
        p. Dvc exp run (dvc repro if running without experiment but dvc exp run can be done all the time instead of dvc repro)

    2. DVC to last commit:
        a. git checkout 56d4484a45c8e9dcf95f357b3819208fc1dc9056  --- to see last commit
        b. Dvc pull   -- to go to last commit state
        You can make changes here and commit now. Or if you don't want to make changes and go to master branch (latest commit):
        c. Git checkout master
        But to return to the master changes you need to pull dvc again
        d. Dvc pull
    
    
    3. DVC install automates 3 steps:
        a. Post Checkout Hook- git checkout - automatically runs dvc checkout post git checkout
        b. Pre Commit Hook - git commit - automatically runs dvc status before git commit
        c. Pre Push Hook - git push - automatically runs dvc push before git push