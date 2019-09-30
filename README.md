# CS 291A Proj 0: Static Page

## Questions
1. On average, how many requests can ab complete in 10 seconds with various power of two concurrency levels between 1 and 256?
	-	| Concurrency Level | Requests Completed (10s)	|
		| ----------------- | ------------------------- |
		| 1     			| 65	 					|
		| 2    				| 142      					|
		| 4					| 263      					|
		| 8					| 451      					|
		| 16				| 663      					|
		| 32				| 855      					|
		| 64				| 883      					|
		| 128				| 883      					|
		| 256				| 855      					|
2. Why are there diminishing returns at higher concurrency levels?
	- This is because once more and more requests hit the server hosting the site at once, the server is unable to process all the requests at the same time. Some requests may get queued while other requests get completed first. We can tell with the apache benchmark tool because as the concurrency levels increase, so does the time it takes to complete each request. Essentially, higher concurrency levels means we are overloading the server with too many requests. Therefore, 1. the server may either queue the incoming requests and process them later or 2. the requests could timeout.
3. What’s the difference when requesting HTTP and HTTPS?
	- HTTP and HTTPS are both used for the browser to be able to establish a (TCP) connection and send / receive data packets. The difference is that packets sent over HTTP are not encrypted, since TCP does not provide that feature. HTTPS uses on SSL certificate (public key on server) to encrypt data getting sent back and forth.  On the client side of things, the data is decrypted using a private key that is generated and agreed upon between the client and server.
4. How can github respond so quickly?
	- One thing that keeps response times relatively low is that GitHub Pages only hosts and renders static content. Because it is only designed for such content, my guess is that GitHub is able to optimize for that by maybe compressing the static files being served.
5. What is your site’s “Time to Interactive” according to PageSpeed Insights?
	- 1.0 sec
