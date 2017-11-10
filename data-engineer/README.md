# Welcome to the BBC data journey!

We are excited that you are interested in helping us on our data journey and are looking forward to getting to know you better.

These exercises give you the opportunity to show us your technical skills. While we would like you to attempt all of the exercises, we do not expect you to be an expert on all of these techniques. Instead, we are keen to see the breadth and the depth of your technical knowledge and how you go about solving the sorts of challenges this role is likely to entail.

Please document and explain the steps as you undertake them showing which tools and processes you have used. You may find it helpful to take notes in a [Jupyter notebook](http://jupyter.org/) as this will allow us to see the code as well as the output, but a text file, PDF, or similar method of documenting your methods is also acceptable. Please make sure that the answers to our questions are clearly visible in what you provide to us.

Once you are done, please upload the resulting files to our [dropbox](https://www.dropbox.com/request/iu2Edq1GwXqR8bR4ZjjZ). If you have created multiple files, we appreciate if you could upload one zipped file.

Please let us know if you have any questions or comments.

## A Few Tips

* Once you've checked out this repository, you shouldn't need to fetch any additional data from the Internet in order to complete the tasks (but you can of course look things up!)

* Don't assume that because we've asked for things in a certain order that answering later questions always depends upon the steps you took in earlier ones.

* There aren't any trick questions, only tricky ones! If a question seems ambiguous, that's probably an error on our part — do let us know if that's the case!

* If you are working on a 32-bit system (or using 32-bit tools on a 64-bit system), you may run into problems.

## 1. Working with data

Several internal flat files have been provided:

* [`s4c`](s4c)
* [`dtt`](dtt)
* [`pidmap.txt`](pidmap.txt)

These files purportedly contain information about television programmes that have been broadcast. However, the encoding, schema and compression schemes used are unknown. This is all data from a real BBC system, so you should not assume that it's in any way pristine.

The files may contain non-ASCII characters; if this is the case, you should attempt to determine the correct encoding of each as part of any data import process. Remember that the BBC has to deal with text in multiple languages on a regular basis, so non-ASCII characters are quite commonplace.

### a) For all candidates

You should examine the file [`dtt`](dtt) and import its contents into a relational database.

Provide notes showing that the data has been imported, the database schema that you've used, and how non-ASCII characters have been handled (feel free to choose entries at random to use to demonstrate this).

Import the contents of the file [`pidmap.txt`](pidmap.txt) into the database in whichever way you feel is most appropriate.

Assume the public-facing URL of a page about a programme has the form:

	http://www.bbc.co.uk/programmes/{:episode_pid}

Assuming BBC Two has `channel_id` = `2`, produce a listing of BBC Two programme UUIDs, titles, and page URLs, ordered lexigraphically by UUID, and limited to at most 100. Don't include any URLs without URLs.

### b) For Senior & Lead Data Engineer candidates

Also import the [`s4c`](`s4c`) file into your database. If the schema used by this file matches that of `dtt`, you should ultimately import it into the same table that you created previously.

As before, provide notes showing that the data has been imported, the database schema that you've used, and how non-ASCII characters have been handled (feel free to choose entries at random to use to demonstrate this).

### c) For Lead Data Engineer candidates

The file [`progsubjects.nt`](progsubjects.nt) contains simple data in N-Triples format.

Import the contents of these files into your database, and produce a list of UUIDs and titles of all of the programmes—if any—which fall into one of the following categories:

* David Hockney
* Politics
* BBC Philharmonic
* Astronomy

## 2. Productionising Machine Learning

### For All Candidates

Machine-learning techniques are becoming an increasingly important way for the BBC to extract insight and value from the large amount of data that we generate on a daily basis. As a data engineer at the BBC you will be responsible for helping us to make sure that the models we build can be deployed quickly and at scale.

Diversity is important to the BBC both in the hires we make and the content we produce. One way of measuring the diversity of the content we produce might be to monitor the number of men and women that appear in our publications. [In this repository](https://github.com/felixmercermoss/genderClassifier) you will find code for a machine-learning model that classifies face images as either male or female. This code works well if clean input images are stored locally, but there are new challenges if we want to classify the faces of 30 million photos attached to BBC articles over the past 50 years.

For this task we would like you to describe (without writing code) how you would turn this algorithm into a production-ready system. Make sure that you highlight the specific problems that you would encounter, together with the method and approach you would employ to solve them. You should consider tooling, availability, performance, scalability, how you might organise various components of the system and any security constraints, and session state.
