Tutorial: Managing Python App Performance
===========================================

**Presenter:** Graham Dumpleton, New Relic

**Track:** Sponsor Tutorials

**Description:**

    There's no longer any question of whether dynamic languages are appropriate for both large and small scale apps--you use the languages and tools that get the job done. Python suits environments where rapid change is the norm.

Introduction to New Relic
-----

New Relic uses monkey patching to inject their performance tracking code.
If you're using gunicorn or wsgi, it's a simple magic wrapper script.

They're not doing full on profiling of the application because there is
too much overhead, so instead they use wrap the wsgi entry point and
monitor that.

They also have instrumentation for monitoring:

* Middlewares
* Database layer
* Templating

They will pull out the view handlers and use those as the transaction
names.

It's not an exhausting stack trace, they try to strip out all sensitive
information, but they do give you a lot of the same information that you
would see in a django stack trace page.


Troubleshooting Common Application Problems
-----

http://newrelic-python-kata.herokuapp.com/

It takes a few minutes for transactions to start showing up on their web
interface.

Once the transactions start showing up in your transaction list, click into
the transaction allows you to see a summary of the view, and you can drill
down into the actual SQL that's being called.

Kata 1
^^^^^

In the example, we see that on the employee_list view, we're getting 50
employees from the database, and for each employee we're making another
request to the BioData and Payroll tables.

We can drill into the template to see that we're making a seperate request
for each employee's bio and payroll info.

Kata 2
^^^^^

A view is loading very slowly, we can drill into the transaction to see that
it is the template rendering that is taking all the time, so we are able to
drill in and see that we're doing filtering in the template that should be
happening in the view.

Kata 3
^^^^^

New Relic will capture your exceptions instead of emailing them to you.  This
way you can set threshholds so that if your application starts throwing a lot
of errors you will be notified.

In this kata, we're using an view that caltulates factorials so that we can
pass in invalid values and see that some requests are throwing exceptions that
we can see the stack trace for them.

Kata 4
^^^^^

Making a request to a weather api to pull the weather for 10 different cities,
and it's taking a while to load.  We can see in the transaction breakdown that
it is the API call that is taking so much time.  We can implement caching of
weather data to speed up page load times.


