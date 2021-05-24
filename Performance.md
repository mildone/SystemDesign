# Design For Performance
below summaries aspects from design, implementation, Testing, Tuning phrases. 
## Difference in cloud and on-Primise
some notice when dealing with cloud design(e.g. Micro service) and monolithic "fix" process 
* capability (CPU and RAM) 
* on-primise
* key
```
scalability is key when designing cloud servcies(shared nothing or share data hanlding pattern)
it doesn't need to be strong in terms units(e.g. performance in peak scenario)
```
## Design Principles
* Become data-driven
* avoid anti-patterns
* performance load testing to set limit
* monitoring and optimize(logging to get root cause)
* scale-cube(XYZ)
## Performance Design Patterns
* cache-aside
* choreography(avoid SPOC)
* CQRS(read and write seperation)
* hirizontal scalling
* index bable
* Priority Queue
* queue-based load leveling
* sharding
* static content hosting(SDN)
* event sourcing
## Performance Design Anti-Patterns
Together with design patterns, this is worth to consider when doing system first place.
* busy components(e.g. Database, offering too-much on a single data store)
* busy FE(moving resource-intensive tasks to BE)
* chatty IO(small request, aggregation)
* extraneous fetching(asking too much when requesting so)
* improper instantiation(repeately createing and destroying objects than singleton)
* no caching for hot-spot data
* retry storm
* synchronous IO
* monolithic presistence(using same data store for different use. e.g. MOF to N*A table years ago)
## Rule: Check list
### Application design
* scalling: stateless
* scalling: auto-detection
* scalling: load balance dynamic
* scalling: service registry
* PaaS features: HPA
* seperation of concern and SRP 
* Avoid client affinity(e.g. only route to certain instance)
* off-load CPU-intensive and I/O intensive task as backend tasks
* shared nothing architect
### Data Management
* understand Data
* data partition
* reduce chatty interation/request
* use queue to level(load of high velocity data write)
* protect your datastore(by mimimizing load and volume)
* set cache control
* handle data growth and retention
* optimize DTO using effective format
###implementation general Rule
* review anti-pattern
* use async call
* avoid locking resource 
* minimize time that connections and resource are in use
* minimize IO request or in batch
* create resource dependency during deployment or application start up 
* less finger-print framework in use
* avoid serve side maintain state
## Performance Target
it's dream to have super powerful unit, it only make sense to discuss performance with indicator and context
* Load Model (under which it works)
* indicators to measure 
** throughout
** response time
** availability
** business operations requirements
## Performance Tuning
## Performance Testing



