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

*
## Rule: Check list
## Performance Target
## Performance Tuning
## Performance Testing



