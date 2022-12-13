(The permissions of an app are stored as  `Slice bool 32`)
1. [[#Fork]]
2. [[#ExternChan]]


### Fork
Fork takes in two functions. They are named newThread, and continuation.$$Fork: (NewThread, \space Continuation) \rightarrow Management$$

### ExternChan
A way to make channels of shared mutable memory with processes outside of the system. These functions *must* update us when they're starting and finishing writing to memory


Given:
$$MutInfo \space T = (Nat, \space T)$$
$$Data = Slice \space Bool \space N$$
$$RequestModify = MutInfo \space (Nat, \space Bit) \rightarrow Bool$$
$$FinishModify = Alert$$
We have that:
$$Channel \space N = (Data, \space RequestModify, \space FinishModify)$$
$$Callback \space T = Unit \rightarrow T$$
(it calls you back with a T once it has one ready. This is used with T=Unit to delay calculations until something important happens.)
$$Alert = Callback \space Unit$$
Type:
$$ExternChan: ((Nat, \space RequestModify, \space FinishModify) \rightarrow (Maybe \space Channel)$$
Where:

MutInfo is just the index that was modified, and what it was before modification



ExternChan's arguments (n, alert1, alert2) are as follows:
- n is a Nat representing the ID of a process (that ID is in the context of the host's processes, not ours) that we want to communicate with.
- RequestModify is a $MutInfo \space (Nat, \space Bit) \rightarrow Bool$. This is the function we want to run before they modify the shared buffer (we are given an index into the buffer that was modified, and the original value). We can return false if we do not want to allow modification to that section of the buffer, which notifies them such, and prevents it from happening.
- FinishModify is an $Alert$ which notifies us when the external channel is done modifying (we can modfiy after that should we choose).