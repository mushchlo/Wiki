## eval_jot
##### Type
	$(jot\_source: u64) \rightarrow u64$
##### Explanation
This takes in a [[Jot]] expression [[λs as numbers |encoded as an u64]] as its only parameter. It then fully expands it into SKI calculus, evaluates it, and returns an equivalent jot expression


### Make-Id

Type: $$Unit \rightarrow (Unique \space  Id,  Unit \rightarrow Unit)$$
  - Note that $Unit$ is the `void` or `()` of this type system, it just contains no information. It's an empty set.

The first value is pretty self explanatory, it's any Id the identifier allocation scheme the host OS uses. The only requirement is that it must not have been used before.

The second value returned is a callback that is used when the Id "falls out of scope". If a function that can be run in the `Comptime` universe, this callback can be resolved at compile time (register planning).


### Start-Process

Type: $$[Bit] \rightarrow Absurd$$
 - Note that Absurd has no constructible value. Because all functions must return an element of the set of their return type, this means the function *cannot return* (in the context of the process' life (cause, yknow, it'll be dead and all.)).
This function sets up all resources required for a process (loads required object files and optimizes if not already done, allocates requested resources, etc.).
