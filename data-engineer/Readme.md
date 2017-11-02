# Welcome to the BBC data journey!

We are excited that you are interested in helping us on our data journey and are looking forward to getting to know you better.

These exercises give you the opportunity to show us your technical skills. While we would like you to attempt all of the exercises, we do not expect you to be an expert on all of these techniques. Instead, we are keen to see the breadth and the depth of your technical knowledge and how you go about solving the sorts of challenges this role is likely to entail.

Please document and explain the steps as you undertake them showing which tools and processes you have used. You may find it helpful to take notes in a [Jupyter notebook](http://jupyter.org/) as this will allow us to see the code as well as the output, but a text file, PDF, or similar method of documenting your methods is also acceptable. Please make sure that the answers to our questions are clearly visible in what you provide to us.

Once you are done, please upload the resulting files to our [dropbox](https://www.dropbox.com/request/iu2Edq1GwXqR8bR4ZjjZ). If you have created multiple files, we appreciate if you could upload one zipped file.

Please let us know if you have any questions or comments.

## A few tips

* Once you've checked out this repository, you shouldn't need to fetch any additional data from the Internet in order to complete the tasks (but you can of course look things up!)

* Don't assume that because we've asked for things in a certain order that answering later questions always depends upon the steps you took in earlier ones.

* There aren't any trick questions, only tricky ones! If a question seems ambiguous, that's probably an error on our part — do let us know if that's the case!

* If you are working on a 32-bit system (or using 32-bit tools on a 64-bit system), you may run into problems.

## 1. Working with external data

A supplier has provided us with some geographic data relevant to one of their systems. It appears to be a subset of [GeoNames data](http://www.geonames.org/ontology/documentation.html), provided in ZIP format, split into 100MB chunks.

**Remember that there's no requirement to use any particular tools or languages to complete the task**: you should use whatever methods you would if you were completing the task as part of your role.

As this is a one-off import, you don’t need to worry about how this might integrate into a processing pipeline, but do make sure that we can see how you've approached it.

### 1a) For all candidates

1. Combine the split files (`geonames.000` … `geonames.004`) into a single ZIP file.
2. Extract the dump from the ZIP file.
3. Produce an [N-Quads](https://www.w3.org/TR/n-quads/) format dump containing all of the data. As in the source data, there should be a 1:1 relationship between graphs and   The graph URIs (the fourth datum in the quad) should be set to the canonical location of the RDF/XML serialisation of each entry that is published on sws.geonames.org (e.g., the graph URI for the GeoNames entry #3020251  http://sws.geonames.org/3020251/about.rdf for GeoNames entry #3020251)
4. Supply a count of the number of graphs in the resulting file, as well as providing the file itself.

### 1b) For Senior & Lead Data Engineer candidates

Create a subset of the data, also in N-Quads format, containing only the most prominent three levels of entity ("Earth", continent and country information). Provide a count of the number of distinct entities in this subset.

### 1c) For Lead Data Engineer candidates

In addition to the above, create a series of subsets and counts of the data, made up of:

1. Only _airports_
2. _Canals_ and _caves_
3. _Hotels_ in Yorkshire
4. _Hospitals_ in Germany

## 2. Working with internal data

Several internal flat files have been provided:

* [`s4c`](s4c)
* [`dtt`](dtt)
* [`pidmap.txt`](pidmap.txt)

These files purportedly contain information about television programmes that have been broadcast. However, the encoding, schema and compression schemes used are unknown. This is all data from a real BBC system, so you should not assume that it's in any way pristine.

The files may contain non-ASCII characters; if this is the case, you should attempt to determine the correct encoding of each as part of any data import process. Remember that the BBC has to deal with text in multiple languages on a regular basis, so non-ASCII characters are quite commonplace.

### 2a) For all candidates

You should examine the file [`dtt`](dtt) and import its contents into a relational database.

Provide notes showing that the data has been imported, the database schema that you've used, and how non-ASCII characters have been handled (feel free to choose entries at random to use to demonstrate this).

Import the contents of the file [`pidmap.txt`](pidmap.txt) into the database in whichever way you feel is most appropriate.

Assume the public-facing URL of a page about a programme has the form:

	http://www.bbc.co.uk/programmes/{:episode_pid}

Assuming BBC Two has `channel_id` = `2`, produce a listing of BBC Two programme UUIDs, titles, and page URLs, ordered lexigraphically by UUID, and limited to at most 100. Don't include any URLs without URLs. 

### 2b) For Senior & Lead Data Engineer candidates

Also import the [`s4c`](`s4c`) file into your database. If the schema used by this file matches that of `dtt`, you should ultimately import it into the same table that you created previously.

As before, provide notes showing that the data has been imported, the database schema that you've used, and how non-ASCII characters have been handled (feel free to choose entries at random to use to demonstrate this).

### 2c) For Lead Data Engineer candidates

The file [`progsubjects.nt`](progsubjects.nt) contains simple data in N-Triples format.

Import the contents of these files into your database, and produce a list of UUIDs and titles of all of the programmes—if any—which fall into one of the following categories:

* David Hockney
* Politics
* BBC Philharmonic
* Astronomy

## 3. Productionising machine learning

### For all candidates

Machine-learning techniques are becoming an increasingly important way for the BBC  to extract insight and value from the large amount of data that we generate on a daily basis. As a data engineer at the BBC you will be responsible for helping us to make sure that the models  we build can be deployed quickly and at scale. 

Diversity is important to the BBC, both in the hires we make and the content we produce. One way of measuring the diversity of the content we produce is to monitor the number of men and women that appear in our publications. Please take a look at [this repository](https://github.com/felixmercermoss/genderClassifier). You will find code for a machine-learning model that classifies face images as either male or female. This code works well if clean input images are stored locally, but there are new challenges if we want to classify the faces of 30 million photos attached to BBC articles over the past 50 years.

For this task we would like you to describe (no code) how you would productionise the above algorithm. Make sure that you highlight the specific problems that you would encounter, together with the method, tools and/or services you would employ to solve them. 
