# My Responsive Blog #
Udacity [Responsive Images](https://www.udacity.com/course/ud882) Course Work

Note: This is *not* the **Build a Portfolio Site** project.  Click [here](https://github.com/icsantos/FEND-build-a-portfolio) to see that repository.

## Goals ##

Download the [project](http://udacity.github.io/responsive-images/downloads/RI-Project-Part-1-Start.zip)

* Make the images fit in their containers in the viewport.
* Restrain the width of the blog.
* Drop the page weight.

Upon meeting the goals, a code will appear in the Udacity Feedback. Paste the code in to the Udacity classroom to complete the quiz!

[More on the Udacity Front-End Grading Engine](https://github.com/udacity/frontend-grading-engine)

## Problems with the Page ##

* The text is readable, but the images overflow the viewport.
* Page weight is massive: the images have been saved as JPEGs at low quality, but they're still too big.
* The headings, body text and images are not styled, making the post hard to read and dull to look at.

## General Advice ##

Check the page with the Chrome Dev Tools:

* Open the tools, open the Network tab, reload the page and look at the number of requests, total transfer size and time to load.
* Change to device emulation mode by clicking the phone icon in the Dev Tools (at the top left next to the magnifying glass icon). Try the various throttling options to emulate a GPRS mobile phone cell connection -- now look at the Network tab. The page takes several minutes to complete loading. (Remember that studies by Amazon, Google and others show an increased drop off in revenue with delays of less than 0.1 seconds!) Even with a good DSL connection, load time is still over 10 seconds.
* Try out emulation on different devices, portrait and landscape (click the icon next to the dimensions). What problems do you notice with each image? Which ones look worse?

Check the page from Page Speed Insights -- lots more problems!

## Set up `localhost` ##

The page has to be loaded via localhost.  This is how to set it up:

* Turn on IIS:

  - Control Panel|Programs|Turn Windows features on or off

  - The Windows Features box will appear. It may take a while for it to load.

  - Scroll down and find Internet Information Services and ensure the box is clicked. Underneath that is Internet Information Services Hostable Web Core. Click that box as well.

* Open the Internet Information Services (IIS) Manager and configure IIS

  - Click the Start button and type IIS in the search bar.

  - Click on Internet Information Services (IIS) Manager to open.

  - In the left Connections pane click the little arrowhead to open the tree and right click on the Sites folder.

  - Click Add Web Site.

  - Give the site a name, and add the path to the folder where your website is located.

  - Go to the IP address and click the drop down. Find and write down the IP address (e.g. 192.168.0.92).

  - Pick a port. I don't recommend using port 80 but any other should do. I used 100.

  - Click ok.

* Set read permissions on the website folder

  - Right-click on the folder your website is kept on and click on properties.

  - Go to the security tab and scroll through Group or user names and look for *IUSR* and *IIS_IUSRS*.

  - If they are there, be sure that "read & execute" and "read" are checked. If they are there and not checked click on one of them and then click edit. Check the boxes for "read & execute" and "read". Click apply then click ok.

  - If they are not there then click edit and then Add. This brings up the Select Users or Groups box.

  - Click the Advanced Button and then the Find Now button. Scroll down until you find IIS_IUSRS. Click on it and press OK 2 times. Click apply.

  - Repeat for IUSR

* To bring up the webpage on local host

  - Open Chrome and type in the IP address and port like this:

    `192.168.0.142:100` (or whatever your port number is)
    
    or like this:
    
    `localhost:100`
    

## Part 1 of the Makeover ##

Used Grunt and ImageMagick to shrink resolutions and compress images such that the size of the page drops below 1.5MB, while making sure the images remain sharp.

* Installed ImageMagick

* Installed npm

* Installed grunt-cli

* Installed grunt

   `npm install`

* Configured IIS
  - add MIME Type webp (image/webp)
  - add MIME Type woff (application/x-woff)

* Added `<figure>` and `<figcaption>` tags around the `<img>` tags

* Added `<section>` container

* Added CSS setting `max-width: 100%;` for images

* Open command prompt
 
  ```
  CD "D:\Documents\Educational\Udacity\ud882 Responsive Images\Project"
  npm install grunt-responsive-images --save-dev
  ```

## Part 2 of the Makeover ##

* Replaced the smiley png
  - http://unicode-table.com/en/sets/
  - Copy and paste the emoji (not the HTML code)

* Used social media icons
  - https://css-tricks.com/html-for-icon-font-usage/
  - https://icomoon.io/app

## Part 3 of the Makeover ##

* Used `<picture>` tag to specify alternative sources for image files.

* Used `srcset` to enable the browser to choose the most appropriate image to request, depending on viewport size and DPR.

* Added a `sizes` attribute to the image with a media query and a viewport size.
 
`srcset` and `sizes` together tell the browser the natural width of the image, and how wide the image will be displayed relative to viewport width. Knowing the display width of the image and the widths of the image files available to it, the browser has the information it needs to download the image with the right resolution for its needs that is as small as possible. And it can make this choice early in the page load while the HTML is still being parsed.
