---
title: "Cinemark Careers Bookmarklet"
date: 2018-05-13T19:49:14-07:00
draft: true
---

Cinemark has two locations in the valley.  The quickest way of searching for job opportunities at La Quinta and the River is to enter a zip code.  Here are the zip codes that will be used:

&nbsp;

* La Quinta: 92253
* Rancho Mirage: 92270

&nbsp;

![Cinemark Careers Search](/img/cinemark_careers.PNG)

Scrolling down to the career search area of the page, there is a form with an input element to enter the zip code and a button to click to search along with a few select elements that are not relevant.  The input element has an id of "keyword" and the value inside of it can be changed like so:

&nbsp;

    document.getElementById('keyword').value=92270;

&nbsp;

The submit button does not have an id and running the .submit() function on the form element does not work in this scenario because when a user clicks the button, the job search results are displayed on the page instead of refreshing the page with the results of the query.  To get around this, the button can be targeted using the document.forms[].elements[].click() method which would result in:

&nbsp;

    document.forms[0].elements[7].click();

&nbsp;

Put these two lines of code together and the template for the bookmarklet is formed.  After changing the zip code, the end result is two bookmarklets that will save a few keystrokes.

&nbsp;

{{<gist jobsinthedesert 8cf714590549ffee6bd3a10e218cedc8>}} 

&nbsp;

<a href="javascript:(function(){document.getElementById('keyword').value=92253;document.forms[0].elements[7].click();})();">Cinemark Careers at La Quinta, 92253 Bookmarklet</a>

&nbsp;

<a href="javascript:(function(){document.getElementById('keyword').value=92270;document.forms[0].elements[7].click();})();">Cinemark Careers at The River, 92270 Bookmarklet</a>
