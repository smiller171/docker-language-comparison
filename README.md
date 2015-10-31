# docker-language-comparison
A Simple "Hello World" app built in Java, Python, and Go for performance testing.  
## Methodology
###Environment
* Go app will be compiled with no external dependancies. I expect the Go app to run the fastest due to this ability
* Python app will be run in Alpine Linux with Python installed
* Java app will be run in Alpine Linux with Java installed

### What will be tested
* Time to run including the time it takes to download the image.
* Time to run once image is already cached
