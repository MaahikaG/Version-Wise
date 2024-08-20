# Version-Wise

## Description
This repository contains the steps and methodology to deploy the current stage of the VersionWise application. 
It contains information about how the GitChatbot and Web-Terminal repositories connect to this application. 
The current form of this application builds upon the existing LearnGitBranching application, and modifies it to abide by the constructivist ideology.

## Table of Contents
- [Goal](#goal)
- [Installation](#installation)
- [Contributing](#contributing)

## Goal
The topic of this project is "Using the Constructivist Pedagogy to Teach Version Control Software to First-Year Computer Science Students".
Currently, version control is typically taught to students using behaviourist practices, resulting in students lacking knowledge of the underlying fundamental concepts. 
This project aims to create an educational tool to teach students version control software using the constructivist pedagogy. The specific design goals for this project are:
- Specific, unique, and relevant feedback is given to the student when using the device
- The student should be allowed to experiment with their own solutions to problems
- The underlying model and framework used for version control software should be explicitly taught

## Installation
- Please start by cloning the learnGitBranching Github repository on the main branch
- You would only have to modify a few of the HTML files in this application
- Add the code in the index.html file of this repository into the template.index.html file in the learnGitBraching source code under the src directory
- Within the src directory of the learnGitBranching source code, add the terminal.html and style_scroll.css files from this repository
- In order to build this application, I recommend using Docker. These are the commands you must run to do so:
```    
docker build -t learn-git-branching .
docker run -d -p 8080:80 -v $(pwd):/usr/share/nginx/html/ --name version-wise-cont learn-git-branching tail -f /dev/null
docker exec -it version-wise-cont /bin/sh
apk add --no-cache yarn
apk add --no-cache git
yarn install
yarn gulp build
yarn run dev --port 80 --host
```
- You should now be able to access this application on localhost:8080

## Contributing
This application is still under development ands requires many more steps to reach the final product. 
While the GitChatbot and Web-Terminal repositories discuss this briefly, here is a comprehensive list of the further developments in chronological order:
- The Kubernetes integration in the simulated web terminals should allow:
  - User authentication so that each user receives a different server backend pod
  - Automatic scaling of the pods based on the number of registered users
  - Data persistence for the individual user's
- If the web terminals are working as intended, then we could start transitioning away from LearnGitBranching. Instead of building off of their existing interface, we could create numerous scrollable lessons on version control, accompanied with a web terminal where the users will practice the commands. 
- The chatbot should be able to read information about the user's actions on the rest of the website, and answer in a contextualized manner. Once we have transitioned away from LearnGitBranching, we could try to utilize the commands the user typed into the web terminal to prompt the chatbot. 
The goal is that this website will allow each user to have their own web terminal with a personal server backend. This will allow them to practice working with a real terminal without impacting their host machine. This would be accompanied by non-interactive lessons which would teach the users about version control and Git, similar to LearnGitBranching. A lesson about Git Internals has already been designed and can be read in the terminal.html file of this repository. Finally, a RAG chatbot contextualized for Git should provide taylored feedback to the students based on their actions within the web terminal. 




