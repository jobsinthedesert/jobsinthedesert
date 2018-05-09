---
title: "Mathis Brothers Furniture Careers Bookmarklet"
date: 2018-05-08T17:49:30-07:00
---

There are plenty of ways to sort through the job opportunities at Mathis Brothers Furniture.  At the time of writing this post, there are not many positions available in the valley.  In fact, it makes me wonder if having this many job filters for furniture stores is overkill.  There are 27 degree filters and an even greater number of job categories.  I am tempted to create a job alert to see if there are any biotech or pharmaceutical job opportunities in the future.

![Mathis Brothers filters form](/img/mathis_brothers_search.PNG)

According to the site there are potentially three locations in the valley that are hiring.  There is Mathis Brothers in Indio and Mathis Sleep Center in Cathedral City and Palm Desert.  Realistically, there are two locations because according to Google and Yelp, the Palm Desert location is permanently closed.

&nbsp;

Looking at the markup for the filters box pictured above we have a form with a lot of nested divs.  The divs for the filter types (Degree Type, Position Type, etc.) have dynamically generated ids.  This worried me because I thought it would make manipulating the form through javascript more difficult.  It turns out that even though those container divs have dynamic ids, the div elements containing the input tags have static ids that I am able to target.

&nbsp;

    <input class="filterCheckbox smallMarginRight" id="filters[locid][1865]" value="1865" type="checkbox" aria-label="Mathis Brothers - Indio, California - Indio, CA, 92201" name="filters[locid][1865]">

&nbsp;

After grabbing the ids for the different store locations, manipulating the form is a breeze.  The following is the code for the bookmarklet broken into multiple lines for readability.

&nbsp;

{{<gist jobsinthedesert 5dbfec52f5eeac99e9e0a8a9e2c277f7 "mathis_brothers_bookmarklet.js">}}

&nbsp;

Input elements of type 'checkbox' have a 'checked' property that will either return true or false.  Setting the value to true will check the box on the page.  In this case the form is submitted with a submit button so submitting the form is straightforward as it can be targeted with an id.  Minifying the code, we end up with this bookmarklet.

&nbsp;

{{<gist jobsinthedesert 5dbfec52f5eeac99e9e0a8a9e2c277f7 "mathis_brothers_bookmarklet-min.js">}}



<a href="javascript:(function(){document.getElementById('filters[locid][1865]').checked=true;document.getElementById('filters[locid][1867]').checked=true;document.getElementById('filters[locid][1868]').checked=true;document.getElementById('filter-form').submit();})();">Mathis Brothers Furniture Careers Bookmarklet</a>
