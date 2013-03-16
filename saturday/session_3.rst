Mobile Application Testing with Python and Selenium
==================

**Presenter:** Jason Carr

**Track:** IV

**Description:**

Selenium has grown to be a mature platform on the desktop, but with 'mobile
now' being the mantra for so many companies, can we use Selenium to effectively
test mobile apps? What about Native apps? This talk will cover using Python to
test mobile web applications with Selenium, as well as an in depth overview of
the future of Selenium to test Native iOS and Android applications.

   https://us.pycon.org/2013/schedule/presentation/79/


Selenium is Just a Library
+++++

It's a tool, like anything else, and it has its place in your toolbelt.

Selenium RC is the old bustedness.  It doesn't support some mobile browsers,
things like that.

Selenium WebDriver is the new hotness, aka Selenium 2.  It supports mobile
browsers.

It is pruposed that the low level web driver functionality will become a
standard and will be built directly into browsers in the future.

Using Selenium on a Mobile Browser
+++++

Every mobile browser is a webdriver, because it's not running on your computer
that is running the actual Selenium script::

    from selenium import webdriver

    desired_capabilities = {}
    desired_capabilities['browser'] = 'android'
    desired_capabilities['platform'] = 'linux'
    desired_capabilities['version'] = '4.0'

iOS
^^^^^

iOS Webdriver is gimped, won't even let you quit, clear cache, etc, and it requires Xcode.

Android
^^^^^

* Requires the Android SDK
* An APK is created that you run in the emulator
* Setup is hard and annoying

**Setup**

* Boot up emulator
* Connect to adb server
* Install the .apk file
* Forward tcp:8080 to tcp:8080 on the phone
* Run your Selenium test

Limitations
+++++

WebViews - A window to the internet provided by the OS that you can put in your
app, they aren't maintained the same way as full fledged browsers.  Second
class citizens.

They are hard to accurately test, and it's hard to test on hardware devices.

Native App Testing
^^^^^

*iOS**

Currently the only option is UI Automation

* Javascript only
* Limited command line control
* No interaction with test

**Android**

Not much better, UI Automator

* Java tests, compiled and pushed as jars
* No interaction
* No test interoperability

**Alternativess**

* Require recompiling apps to add code
* Varias APIs
* Mixed community and limited help
* Forced language implementation, so you can't use the tools you want

**This is all BAD**

Enter Appium
+++++

* No recompilation of app required, so what you test against is what you can
deploy to the app store
* Use Selenium API
* All methods are first class citizens, they wrap the test frameworks that the
companies provide to you
* Any language and OS, supported by Selenium
* Open source

Wraps UI Automation and UI Instruments

Because it uses the native testing framework (and wraps it), it supports all of
the browser and device functionality that the native testing framework exposes.

**iOS**

Your Script -> Appium Server -> iOS UI Instruments -> Test App

**Android**

Your Script -> Appium Server -> Android UI Automator -> Test App


What's Next
+++++

They not only wrapped the native UI Automation functionality, but they also
wrapped the Mobile Webkit implementation, because they want it to work on real
devices.  We want ito test W3C compliant browsers whenever possible.

* Drive a real browser
* Actual rendering
* Standards compliant

