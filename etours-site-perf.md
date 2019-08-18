# Etours webiste performance

Tool to test PageSpeed is [PageSpeed Insight by Google](https://developers.google.com/speed/pagespeed/insights/)

* Etours REACT-STATIC Homepage PageSpeed Insight
  * First Contentful Paint - 6.4s
  * Speed Index - 18.4s
  * Time to interactive - 24.5s
  * First Meaningful Paint - 6.4s
  * First CPU Idle - 12.4s
  * Max Potential First Input Delay 510ms
  
* Etours REACT-STATIC TourPackage PageSpeed Insight
  * First Contentful Paint - 2.1s
  * Speed Index - 3.0s
  * Time to interactive - 6.1s
  * First Meaningful Paint - 2.1s
  * First CPU Idle - 6.3s
  * Max Potential First Input Delay 400ms  

* Etours Django Homepage PageSpeed Insight
  * First Contentful Paint - 1.9s
  * Speed Index - 2.1s
  * Time to interactive - 4.1s
  * First Meaningful Paint - 3.2s
  * First CPU Idle - 3.2s
  * Max Potential First Input Delay 190ms
  
* Etours Django TourPackage page PageSpeed Insight
  * First Contentful Paint - 1.9s
  * Speed Index - 2.3s
  * Time to interactive - 4.1s
  * First Meaningful Paint - 3.8s
  * First CPU Idle - 4.1s
  * Max Potential First Input Delay 230ms  
  
* Findings
  * Serverside rendered Home page performs better
  * Serverside rendered TourPackage pafe performs better
  * Serverside rendered pages is more performant in all metrics
