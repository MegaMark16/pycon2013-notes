Visualizing Github, Part I: Data to Information
==================================================

**Presenter:** Dana Bauer, Idan Gazit

**Track:** III

**Description:**

A treasure trove of data is captured daily by Github. What stories can that
data tell us about how we think, work, and interact? How would one go about
finding and telling those stories? This two-part talk is a soup-to-nuts tour of
practical data visualization with Python and web technologies, covering both
the extraction and display of data in illumination of a familiar dataset.

    https://us.pycon.org/2013/schedule/presentation/112/


Data and Mapping
+++++

Github focuses a lot on charts and graphs because so much of the data that they
have focuses on activity over time.

They didn't even know what data they had.

**Ben Fry - Visualizing Data**

It's important to work with a team of people that have a mix of skills,
no steps in the process should be completed in isolation.

* Acquire
* Prase
* Filter
* Mine
* Represent

Acquiring the Data
+++++

* 3.4 million users
* 5.7 million repos

They pulled down the top 200 repos of the top 10 languages, put it in the cloud
on Amazon EC2, and started cloning all of the repos.

Working With The Data
+++++

Now they wanted to start working with their data.

They worked within iPython Notebook, but if they got disconnected it was still
a problem becuase they couldn't see where they were currently at.

Not all of the information is in the git repos, such as users and github
specific information.

They had to hit Github's API, but rate limiting was still an issue.

The data was changing constantly, so there was some distortion in the snapshot
of the data.




