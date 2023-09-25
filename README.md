[![CI](https://github.com/nogibjj/python-template/actions/workflows/cicd.yml/badge.svg)](https://github.com/nogibjj/python-template/actions/workflows/cicd.yml)
## Template for Python Projects 

### Goal of the template 
Prepare a Python template for the future use of the data engineering course, or other Python projects.


### Setting up the Project
* Makefile: Rules for building the system. Use `make` to run the commands.
* requirements.txt: Specifies the package used by the program. Used by Makefile for installation `pip install -r requirements.txt`
* .github/workflow: contains the cicd.yml file which set up the CI process. When push or merge to the main branch, a GitHub Action will be triggered running install, lint, test, format, and deploy 

  *Testing on Git Action*
  * Check for GitHub Actions after the first build. Status is success and each step is working.
  <img width="1096" alt="Screenshot 2023-09-08 at 7 32 44 PM" src="https://github.com/lisawym/data-engineering/assets/46847817/eb4a7a60-9c6d-4f8e-bbba-251a01b2c96f">


### Setting up Docker
* DockerFile: Script that creates a docker image. Used Alpine as the base image.
* repeat.sh: Test script for Docker. `COPY repeat.sh /app` in DockerFile.

  *Testing on Docker*
  1. Download Docker Desktop for MacOS
  2. Create a docker image: `docker build -t data-engineering . ` 
  3. Run the container in the terminal: `docker run -it data-engineering bash`
  4. Run the test script: `./repeat.sh 3 6`
  * Results: The container is created and working well. Test code returns the desired behavior (printing out 6 for 3 times)
  <img width="1440" alt="Screenshot 2023-09-08 at 7 34 46 PM" src="https://github.com/lisawym/data-engineering/assets/46847817/037c7d18-3c02-4966-a01b-e58dd3b288d8">
  <img width="450" alt="Screenshot 2023-09-08 at 7 35 15 PM" src="https://github.com/lisawym/data-engineering/assets/46847817/23a8e7eb-1053-4860-8926-6952dc137784">



### Developing on Codespace
* .devcontainer: A folder that creates a container hosted on the virtual machine (in our case, set up the Codespace for development). DockerFile will create an image of the project and devcontainer.json does the configuration.
*setup.sh: Activate the environment. It will be run after the codespace is created. ` "postCreateCommand": "bash setup.sh"` in devcontainer.json.

  *Testing on Codespace*
  * Result: Codespace was open and configurated
  <img width="1401" alt="Screenshot 2023-09-08 at 7 35 50 PM" src="https://github.com/lisawym/data-engineering/assets/46847817/ecd7dff2-1a9f-45ef-8677-e3169899df48">



### Other Files
* .gitignore: Specifies the files that git should ignore when doing version control
* main.py, test_main.py: Sample Python code and testing code
* LICENSE: Gives permission to other people to reuse the code
* mylib: Libraries used by the code

