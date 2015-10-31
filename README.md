# docker-language-comparison
A Simple "Hello World" app built in Java, Python, and Go for Docker performance testing.  
## Methodology
###Environment
* Go app will be compiled with no external dependancies and built "FROM scratch"
* Python app will be run in Alpine Linux with Python installed
* Java app will be run in Alpine Linux with Java installed

### What will be tested
* Time to run including the time it takes to download the image.
* Time to run once image is already cached

### Expectations
* I expect the Go app to run the fastest because of the ability to run as a standalone executable
* I expect Java to be slowest because of the JVM overhead

## Results
As expected, Go was fastest to run when you had to download the entire image, as it is less than 1Mb  
Surprisingly, Go was not the fastest to execute when the image had already been downloaded, that title went to Java. This is especially surprising since I had expected additional overhead caused by the JVM starting up.  
Python and Go were approximately equal in execution time, each taking about a half a second, with an outlyer Python execution taking less than 0.4 seconds. This was the fastest execution time from the set, but I don't have an explanation for why it took so much less time than the other runs.  
Java took just over 0.4 seconds to execute consistently.


When you include download time, Go took about 2 seconds, Python about 8 seconds, and Java abou t 9 seconds. This aligns well with the size differences in the images


Overall, I think the takeaway here is that while the overall size of the image and your various layers matters, the language choice shouldn't be influenced by execution time in Docker. Try to keep your application small, and pre-cache at least a base image with all of your dependencies and you should get good performance

### go
#### Including download time
* real	0m2.283s
* real	0m1.986s
* real	0m2.085s

#### Pre-cached image
* real	0m0.509s
* real	0m0.527s
* real	0m0.507s

### python
#### Including download time
* real	0m7.727s
* real	0m8.047s
* real	0m7.700s

#### Pre-cached image
* real	0m0.537s
* real	0m0.382s
* real	0m0.510s

### java
#### Including download time
* real	0m9.302s
* real	0m8.864s
* real	0m8.914s

#### Pre-cached image
* real	0m0.432s
* real	0m0.429s
* real	0m0.410s
