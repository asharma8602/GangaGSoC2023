# Challenge for Ganga projects in GSoC 2020

The challenge that forms part of the Ganga projects in GSoC is divided up into three pieces.

1) A part that everybody should attempt that demonstrates the ability to do a basic job in Ganga and work with python
2) A part that is related to the persistent storage project that require a demonstration of how you work with a model database from python.
3) A part that is specific to the GUI project where you will be required to create a webserver that can demonstrate its interaction with Ganga in a simple manner.

You are welcome to do all three parts, but if you are only interested in applying for the GUI project, you will not be disadvantaged by not attempting the one related to the persistent storage.

## Setup
Following the steps below will ensure that you can work freely on your project, can submit code through pushing it to GitHub but at the same time keep it private. Please avoid making your repository public as we want each student to work on this independently.

- Create a fork of this repository which is private in GitHub
- Give the GitHub users `egede`, `alexanderrichards`, `mesmith75` read access to your repository

For performing actual work for the challenge, we suggest something like

```bash
virtualenv -p python3 GSoC
cd GSoC/
. bin/activate
pip install -e git+https://github.com/YOUR-GITHUB-USERNAME-HERE/GangaGSoC2020#egg=gangagsoc
```

Through the dependency, this will install Ganga as well such that you can work with it directly inside the virtualenv.

Communication is an important part of working in GSoC. Please just ask by email to all/any of the developers about anything that you are in doubt about. 

## Completing challenge

To complete the challenge you should push everything to the master branch of your forked repository. Then please send an email to us that you have finished. In the repository, we expect
- That the `setup.py` file is updated with any extra `python` package dependencies that you may have introduced.
- That there is a file `PROJECT.md` that documents what you have done and how we can test it.
- That you have implemented tests of the code that can be tested with `pytest` to illustrate that everything works as expected.
- That anything (like interaction with GUI), that can not easily be made to work with `pytest` is fully explained.

## Ganga initial task

As stated above everybody should attempt to complete this task

1) Demonstrate that you can run a `Hello World` job that executes on a `Local` backend.
2) Create a job in Ganga that demonstrates splitting a job into multiple pieces and then collates the results at the end.
  - Use the included file `CERN.pdf`.
  - In python, or through using system calls, split the pdf file into individual pages. 
  - Create a job in Ganga that will count the number of occurences of the word "the" in the text of the PDF file. It should be counted whether it is capitalised or not. Make sure not to count other words with the same letters. So "The Ganga project is the best" should have a count of two, while "There is nothing here" should have a count of zero.
  - Using the `ArgSplitter` create subjobs that each will count the occurences for a single page.
  - Create a merger that adds up the number extracted from each page and places the total number into a file.

## Ganga persistent storage task



## Ganga GUI task
---

1) For the first part of this task we will not need to use the Ganga framework at all, you will need to show the following:

 - Ability to create a simple webserver using a python based web framework of your choosing
 - Have the webserver render dynamic content using a templating engine (e.g. jinja2)
 - Modify the server to allow updating of the content either by making it a RESTful service (with ajax requests client side) or by utilising WebSockets.


(*__Note__ that the content for this task can be anything that you like and we would very much like to see you be as creative as possible with the actual design of the web page.*)

2) For the second part we will introduce some of the Ganga framework:

 - This time we want the website to be able to submit a simple Ganga job.
   (*__Note__ we don't expect the job to be customisable at this stage, a simple button to submit a new job is all that is required.*)
 - This will mean that server side you will need to include the following code and have ganga as a dependency
 ```python
import ganga.ganga
from ganga import Job
j = Job()
j.submit()
```
 - The server will have to monitor the status of the job and relay it back to the client in real time