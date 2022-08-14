# Caching
Caching is a mechanism to improve the performance of any type of application. Technically, caching is the process of storing and accessing data from a cache. But wait, [what is a cache?](https://auth0.com/blog/what-is-caching-and-how-it-works/) A cache is a software or hardware component aimed at storing data so that future requests for the same data can be served faster.

* The main reason why caching was born is that accessing data from persistent memories takes a considerable amount of time. Thus, whenever data is retrieved or processed, it should be stored in a more efficient memory. We call such a memory cache, which can be thought of as a high-speed data storage layer whose primary purpose is to reduce the need to access slower data storage layers. To be cost-effective and efficient, caches must be relatively small, especially if compared to traditional memories. This is why they are usually implemented by using fast access hardware such as RAM (Random-Access Memory) plus a software component.

* Thanks to caches, it is possible to implement a mechanism to efficiently reuse previously retrieved or computed data. Whenever a new request arrives, the requested data is searched first in a cache. A cache hit occurs when the requested data can be found in a cache. On the contrary, a cache miss occurs when it cannot. Obviously, reading the required data from caches is assumed to be faster than recomputing the result or reading it from the original data store. So, the more requests can be served from a cache, the faster the system will be.

![](https://images.ctfassets.net/23aumh6u8s0i/2fNadw2WJZjxWw4vlmEwtq/ec47b60f009e5dbae3ab41cf79e64b08/01_caching-sep.jpg)

## Why Caching is Important
Caching is extremely important because it allows developers to achieve performance improvements, sometimes considerably. As mentioned earlier, this is vital.

* In particular, neither users nor developers want applications to take a long time to process requests. As developers, we would like to deploy the most performing version of our applications. And as users, we are willing to wait only for a few seconds, and sometimes even milliseconds. The truth is that no one loves wasting their time looking at loading messages.

* Plus, the importance of offering high performance is so critical that caching has rapidly become an unavoidable concept in computer technology. This means that more and more services are using it, making it practically omnipresent. As a consequence, if we want to compete with the multitude of applications on the market, we are required to properly implement caching systems. Furthermore, explaining to users why our systems are slow can represent a problem.

Another important aspect of caching is that it allows us to avoid making new requests or reprocessing data every time. So that we can avoid overhead, like network overhead, and reduce CPU usage, especially if requests involve complex elaborations. This can prolong the life of our machines or servers. Plus, avoiding making new requests reduces the overall amount of requests needed, which may decrease the cost of your infrastructure. In fact, when dealing with Cloud platforms or public API providers, for example, it is common to bill for any network communication between their services. Great side effects, right?

![](https://images.ctfassets.net/23aumh6u8s0i/3VaLlGf6vmPCC4RllRsF6/0e085ab23dd40ce7b43ad7be633a0433/02_caching-sep.jpg)

## Challenges
Caching is by no means a simple practice, and there are inevitable challenges inherent in the subject. Let’s explore the most insidious ones.

### Coherence Problem

* Since whenever data is cached, a copy is created, there are now two copies of the same data. This means that they can diverge over time. In a few words, this is the coherence problem, which represents the most important and complex issue related to caching. There is not a particular solution that is preferred over another, and the best approach depends on the requirements. Identifying the best cache update or invalidation mechanism is one of the biggest challenges related to caching and perhaps one of the hardest challenges in computer science.

### Choosing Data to Be Cached

* Virtually any kind of data can be cached. This means that choosing what should reside in our cache and what to exclude is open to endless possibilities. Thus, it may become a very complex decision. As tackling this problem, there are some aspects to take into account. First, if we expect data to change often, we should not want to cache it for too long. Otherwise, we may offer users inaccurate data. On the other hand, this also depends on how much time we can tolerate stale data. Second, our cache should always be ready to store frequently required data taking a large amount of time to be generated or retrieved. Identifying this data is not an easy task, and you might risk filling our cache with useless data. Third, by caching large data, you may fill your cache very rapidly, or worse, using all available memory. If your RAM is shared between your application and your caching system, this can easily become a problem, which is why you should limit the amount of your RAM reserved for caching.

### Dealing with Cache-misses

* Cache misses represent the time-based cost of having a cache. In fact, cache misses introducing latencies that would not have been incurred in a system not using caching. So, to benefit from the speed boost deriving from having a cache, cache misses must be kept relatively lows. In particular, they should be low compared to cache hits. Reaching this result is not easy, and if not achieved, our caching system can turn into nothing more than overhead.

## Types of Caching
* Although caching is a general concept, there a few types that stand out from the rest. They represent key concepts for any developers interested in understanding the most common approaches to caching, and they cannot be omitted. Let’s see them all.

### In-memory Caching
* In this approach, cached data is stored directly in RAM, which is assumed to be faster than the typical storing system where the original data is located. The most common implementation of this type of caching is based on key-value databases. They can be seen as sets of key-value pairs. The key is represented by a unique value, while the value by the cached data.

* Essentially, this means that each piece of data is identified by a unique value. By specifying this value, the key-value database will return the associated value. Such a solution is fast, efficient, and easy to understand. This is why it is usually the preferred approach by developers that are trying to build a caching layer.
### Database Caching
* Each database usually comes with some level of caching. Specifically, an internal cache is generally used to avoid querying a database excessively. By caching the result of the last queries executed, the database can provide the data previously cached immediately. This way, for the period of time that the desired cached data is valid, the database can avoid executing queries. Although each database can implement this differently, the most popular approach is based on using a hash table storing key-value pairs. Just like seen before, the key is used to look up the value. Note that such type of cache is generally provided by default by ORM (Object Relational Mapping) technologies.

## Web Caching
This can be divided into two further subcategories:
### Web Client Caching
This type of cache is familiar to most Internet users, and it is stored on clients. Since it is usually part of browsers, it is also called Web Browser Caching. It works in a very intuitive way. The first time a browser loads a web page, it stores the page resources, such as text, images, stylesheets, scripts, and media files. The next time the same page is hit, the browser can look in the cache for resources that were previously cached and retrieve them from the user’s machine. This is generally way faster than download them from the network.

### Web Server Caching
This is a mechanism aimed at storing resources server-side for reuse. Specifically, such an approach is helpful when dealing with dynamically generated content, which takes time to be created. Conversely, it is not useful in the case of static content. Web server caching avoids servers from getting overloaded, reducing the work to be done, and improves the page delivery speed.

### CDN Caching
CDN stands for Content Delivery Network, and it is aimed at caching content, such as web pages, stylesheets, scripts, and media files, in proxy servers. It can be seen as a system of gateways between the user and the origin server, storing its resources. When the user requires a resource, a proxy server intercepts it and checks to see if it has a copy. If so, the resource is immediately delivered to the user; otherwise, the request is forwarded to the origin server. These proxy servers are placed in a vast number of locations worldwide, and user requests are dynamically routed to the nearest one. Thus, they are expected to be closer to end-users than origin servers, which implies a reduction in network latency. Plus, it also reduces the number of requests made to origin servers.

![](https://images.ctfassets.net/23aumh6u8s0i/2TmCisu0FJwFyZoffWt7vv/a8920c26226f8d723a8280c7752de8b6/04_caching-sep.jpg)
# Caching approaches
## Cache Updates
Caching replaces [slower operations](https://www.developer.com/design/performance-improvements-caching/#:~:text=Caching%20replaces%20slower%20operations%E2%80%94like,changes%20from%20time%20to%20time%3F)—like making calls to a SQL server to an instantiate an object—with faster operations like reading a serialized copy of the object from memory. This can dramatically improve the performance of reading the object.

* however, what happens when the object changes from time to time? Take, for instance, a common scenario where the user has a cart of products. It’s normal, and encouraged, for the user to change what’s in their shopping cart. However, if you’re displaying a quick summary of the items in a user’s cart on each page, it may not be something that you want to read from the database each time.

* That’s where managing cache updates comes in, you have to decide how to manage these updates and still have a cache. At the highest level you have two different strategies. The first set of strategies is a synchronized approach where it’s important to maintain synchronization of the object at all times. The second strategy is a lazy (or time) based updating strategy where having a completely up-to-date object is nice but not essential.

Say for instance that you had an update to a product’s description to include a new award the product has won — that may not be essential to know about immediately in the application.
## Synchronized Update
With a synchronized update, sometimes called coherent cache, you’re trying to make sure that updates are synchronized between all of the consumers of the cache. When you’re on a single server this is pretty easy. You have access to an in-memory cache and you just clear the value and update it with the new value. However, in a farm where you have multiple servers you have a substantially harder problem to solve. You must now use some sort of a coordination point (like a database, out of process memory store, etc.) and take the performance impact of that synchronization, or you must develop a coordination strategy for the cache.

* The problem with the synchronized approach is that synchronization reduces the performance of the cache, which is of course the whole reason why it exists. There are implementations of this strategy that require only a small of the synchronization data to be shared, and there are strategies that essentially move the cache into a serialized database not unlike persisted session state. In either strategy the impact of synchronization is not trivial.

* The synchronization strategy is good when there’s a relatively large amount of change in the cache. For instance, if you needed to know the last few products a user looked at, that’s going to change rapidly, then you may want not want to use a synchronized strategy for that data.

* Another approach to synchronized cache is to use a coordination approach. With this approach you believe that the number of updates will be small and because of that you require extra actions when the cache is updated, rather than requiring extra activities on every (or nearly every) read. In general the kinds of data that you want to cache have relatively low volatility (rate of change) so the coordination approach to keeping cache’s synchronized is often the best choice for synchronized cache. In this situation, when the object changes, and that change is persisted to whatever the back end store is, the object notifies the cache manager and the cache manager notifies all of the servers running the application.

* For instance, in a farm with three servers, the cache manager clears the cache on the currently running servers and then signals the other cache managers — say via a web service — that they should clear their cache for a specific object. The number of calls needed obviously increases the larger the farm but as a practical matter the frequency is relatively low.

The final approach to a synchronized cache is having it client managed via a cookie. This strategy is really only viable for user data/session cache when the cached data is small (so that it can be retransmitted without impact), volatile (so that another strategy won’t work well), and non-sensitive (so that the user having the information doesn’t have any potential security implications.) The example of the recently visited products is a great example of a cache that could be pushed down to the client. This solves the need for it to be managed in cache.
## Lazy Update
In some situations such as the product description changing to include a new award for the product the change needs to be visible to all of the members of the farm and in every session eventually but the applications usefulness doesn’t rely upon an absolute up to the minute cache to function correctly. In these situations there are two basic approaches that can be applied based on your scenario. First, you can allow the cache to expire after a certain passage of time.

* For instance, caching information about a product is useful but perhaps you decide that the product should only be cached for ten minutes. This decision is made because most of the time if the product isn’t accessed within the previous ten minutes it’s not needed any longer.

* Depending upon your scenario you can choose to apply a fixed window (e.g. every ten minutes the product object in memory is updated ) or a sliding window (e.g. only after ten minutes of inactivity is the product object in memory updated). Of course, we’re really talking about expiring the cache so in both scenarios it’s really just that the objects will be cleared from the cache at those intervals and when they are reloaded or regenerated could potentially be much longer, but the older data would only be returned while the object is in cache.

When you know specifically when the object data is going to change, say for instance during a batched update in the middle of the night, you can choose to update the entire cache, generally for a class of objects, at the same time. The effect of this is that you are able to maintain cache efficiency except for the onetime per day when you know that updates are happening.
## Read-Through
The final scenario that introduces a bit of awareness in your objects that caching is involved is to allow for a read-through strategy where the consumer of the cached objects can specifically request that the object be read from “source of truth” rather than relying upon the cache. This can be useful when there are specific scenarios where it’s critical to know the exact right answer. For instance, consider the importance of having the exact right value during a checkout on a commerce site.

Read-Through strategies don’t solve the issues around a cache getting stale. They just recognize that there are specific times when read operations are critical and other situations where they’re less critical. In recognizing this the length of time that a cache can be scale can be longer since critical operations will still use the correct data.
## Caching Options
Whether your caching needs are not volatile at all or are very volatile you have another decision to make about what level at which to cache data. There are techniques built into ASP.NET which allow you to cache the output of a control as well as caching individual objects like we’ve been discussing. With both of these options available the question is bound to come up about which of these techniques you should use or whether you should use both.

* The key benefit of output caching is that once the data is processed for output once it doesn’t have to be reprocessed. In other words, if you have some complex algorithm for building a set of data or a graph, then caching the output of that process would prevent reprocessing the same data over and over again. Caching the output is also good when you only need a small subset of the data to create the output and caching the objects themselves would require a larger cache.

* However, as a general rule the use of output caching produces a larger cache because you may have a few different visual representations of the same data. For instance, you might have a control which is a vertical sidebar representation of a cart, the actual cart display page, and a summary indicator for the number of items which appears on every page. These controls would likely require more memory if cached at the output level than would be required to cache the cart and rebuild them.

* Of course, for this kind of cache disk files can be used. SharePoint, for instance, uses this strategy for page output caching. This approach can be valuable particularly if most of what you’re generating is coming from a database and thus is relatively expensive to get to. Nearly all content in a SharePoint site comes from a database. Of course, if you decide on a strategy that utilizes the disks on the front in web servers you’ll want to make sure that the disk performance is acceptable. This generally means going for SAS (Serially Attached SCSI) instead of SATA disks to get better responsiveness.

The reality is that processing power is cheap and is rarely the bottleneck in the system. More frequently the coordination point — the database — is generally the bottleneck in any large system. Because of that reprocessing a bit to regenerate the user interface isn’t generally as big an issue as mitigating the impact on the back end database server.
## Cache Management
Once you’ve concluded whether you want to cache the output or the objects you’re still not done, you still have to consider what items you’re going to put into the cache and what priority you’re going to give them should the cache manager need to make decisions about which objects need to get thrown out of the cache to make room for new items.

* As a practical matter cache’s can’t be of infinite size. There’s a limited amount of memory in a server, there’s a limited amount of entries in a database before performance suffers, etc. Knowing that you have a fixed size cache to work with the question often comes up as to which objects should end up in cache, for how long, and which objects should be purged first if there are pressures to reduce the cache size.

* Selecting objects to cache is really a balance between four factors: volatility, frequency of access, cost to recreate, and size in cache. The ideal candidate for caching is one that never changes, has a really high frequency of use and cost to recreate and is very small. Of course, real objects don’t have all of these attributes. In the real world objects may be relatively volatile but don’t cost much to recreate.(These objects may not even need to be cached at all let alone cached with a high priority).

* Similarly, you may find that an invoice is hard to recreate but is relatively infrequently accessed and is fairly large in memory.

The greater the performance impact by caching the object the more important it is to keep in memory. In review, slowly changing (low volatility), highly accessed, hard to recreate, and small storage objects are the best to maintain in a cache. The more an object fits the characteristics the more important it is to keep in cache.

## Oflate the datatbase
stay away from the database as much as possible. That means don’t open connections to it and don’t start transactions unless you have to.

## What a difference a cache makes
caches can greatly offload the database especially for applications accessing the database in read-only mode. In-memory cache is better than an on-disk one, which is better than a remote or a relational database.

## Cache as coarse-grained objects as possible
caching coarse-grained objects “will save CPU and time required to interrogate n number of cache zones rather than a single cache zone. Furthermore, retrieving a full object graph saves time assembling the object graph.”

## Don’t store transient state permanently
avoid storing transient data, like login session data, in a database.

## Location
put things close to where they are supposed to be delivered. Instead of going through a load balancer, a web server, an application server and a database, it is faster and less consuming to go through the load balancer and the web server and retrieve some of the content from a [CDN](https://en.wikipedia.org/wiki/Content_delivery_network).
## Constrain concurrent access to limited resources
if more than one request accesses the same resource and performs the same calculation, it is better to proceed with the first and let the others wait until it finishes its job to just use the final results. Letting all the threads to access the resource will only slow down the process.
## Staged, asynchronous processing
Separating a process through asynchronicity into discrete, separate steps separated by queues and executed by a limited number of workers/threads in each step will quite often do wonders for both [scalability and performance](https://www.infoq.com/news/2009/05/8-Best-Practices-Scalability/).

## Minimize network chatter
try to make the application as remotely untalkative as possible because network communications are considerably slower than in-memory ones.
## references:-
* [auth0.com](https://auth0.com/blog/what-is-caching-and-how-it-works/)
* [developer.com](https://www.developer.com/design/performance-improvements-caching/#:~:text=Caching%20replaces%20slower%20operations%E2%80%94like,changes%20from%20time%20to%20time%3F)
* [infoq.com](https://www.infoq.com/news/2009/05/8-Best-Practices-Scalability/)














