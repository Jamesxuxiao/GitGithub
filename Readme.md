# Git and GitHub

## Git
### What Is Git?
* Popular source control system
* Distributed system
* Free and open-source
### Why Use Git?
* Fast
* Disconnected
* Powerful yet easy
* Branching
* Pull requests
### But… Why Not Git?
* Different
* Learning curve
* Tools
* Binary files


## GitHub
### What Is GitHub?
* Hosting service based on Git
* More than just source control for your code
* Free and paid options

## Getting Your Machine Ready
### Git Works Everywhere!
#### Windows
##### What you need
- Download Git from https://git-scm.com/downloads
- An editor Visual Studio Code
- GitHub account
#### Mac
#### Linux

## Foundations of Git
### Centralized Source Code Management
![Centralized Source Code Management](./images/Centralized.PNG)
### Distributed Version Control
![Distributed Version Control](./images/Distributed.PNG)

### The 5 Areas of Git
```mermaid
sequenceDiagram

    participant Stash 
    participant Working Area
    participant Index
    participant Repository
    participant Remote Repository

    Note over Working Area: C:\bitbucket\Documents\gda-airflow-orchestrator-avalanche>
    Note over Repository: .git/objects(blob,tree,commit)
    Note over Index: .git/index(Binary file)

    par commnad-compare
        rect rgb(200, 150, 255)
          Working Area -) +Index: git diff
        end
    AND
        rect rgb(200, 150, 255)
          Working Area --x Repository: git diff --cached
        end
    end

    par move data to the right
        rect rgb(128, 255, 0)
          Working Area -) +Index: git add .
        end
    AND
        rect rgb(128, 255, 0)
          Index --x Repository: git commit -m "add new files"
        end
    AND
        rect rgb(128, 255, 0)
          Repository --x Remote Repository: git push origin main
        end
    AND
        rect rgb(128, 255, 0)
          Stash --x Working Area: git stash apply
        end
    end

    par move data to the left
        rect rgb(255, 128, 0)
          Repository --x Working Area: git reset --hard HEAD
          Repository --x Index: git reset --hard HEAD
        end
    AND
        rect rgb(255, 128, 0)
          Repository --x Index: git reset --mixed HEAD
        end
    AND
        rect rgb(255, 64, 0)
          Index --x   Working Area: git restore --staged $file
        end
    AND
        rect rgb(207, 93, 190)
          Working Area --x Stash: git stash --include-untracked
        end
    end

    loop check stash
      Stash -->> Stash :  git stash list
    end

```