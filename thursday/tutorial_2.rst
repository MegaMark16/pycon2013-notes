Tutorial: Integrating Selenium and Sauce Labs into your Continuous Integration Build
===========================================

**Presenter:** Jason Carr, Sauce Labs

**Track:** Sponsor Tutorials

**Description:**

CI can be hard. Making Selenium a part of your CI infrastructure is even harder. This tutorial will cover the end-to-end process of adding Selenium infrastructure to your CI build using Sauce Labs, and integrations with Jenkins and Travis CI.

Selenium WebDriver
-----

WebDriver lets you send your script to a WebDriver server to execute.  The
script gets translated into commands to drive the browser, which then returns
a json response.

Sometimes you have to wait for the internet, but Selenium tests are run as
procedural scripts, so you will often have to put in explicit waits for things
to load.

Selenium in the Cloud
^^^^^

It's possible to run your tests in the cloud on SauceLabs infrastructure, you
just specify desired_capabilities to the different features you want:

* browserName - Firefox
* platform - Linux
* etc


**Security Through Purity** They completely destroy a VM when you are done
running your tests, so your VM never gets used again, and you never get a VM
that was used by someone else.

Selenium is just a library, it's not only for testing, it's just for
controlling a browser from a script.

Quick Intro to Selenium
^^^^^

Some simple code examples::

    >>> from selenium import webdriver
    >>> driver = webdriver.Chrome()
    >>> driver.get('http://www.google.com')
    driver.title
    >>> driver.title
    u'Google'
    >>> driver.find_element_by_name('q').send_keys('pycon')
    >>> driver.title
    u'pycon - Google Search'


Cloud Meets Local Deve
^^^^^

It's possible to run tests on the SauceLabs cloud that are hitting your local
dev machine, using a built in vpn solution.

You can watch the tests running through a browser based VPN session directly
to the VM.

Tools To Use
-----

* Jenkins Server
    * Github plugin
    * InjectEnv plugin
    * Sauce OnDemand plugin
* virtuaenv/pip/distribute
* Selenium client library
* Sauce Connect
* Sauce Labs Account
* sauceclient library

Basic Steps
^^^^^

* Install Jenkins
* Install Sauce OnDemand plugin
* Configure Sauce OnDeminad plugin in Jenkins
    * Enter your api username and api key
    * Test your connection (button in the config page)
* Configure the git[hub] plugin
* Configure the github webhook configuration so that your tests get run on
  every push

It's possible to get unique ids for accessing test runs without passing
credentials around, which is good on a large team where you don't want
everyone to have to log in to see test run output.


Dynamic Test Classes
^^^^^

https://github.com/santiycr/cssify/blob/master/tests/test_cssify_web.py

