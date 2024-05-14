When one server is not enough, you need many servers. There is usually a load balancer deciding who to send information.

The two main problems with distributed systems are:
- **Receiving the same message more than once.** To solve it we can do idempotent messages. This means that no matter how many of the same message where sent, it will only execute once.
- **Messages are unordered.** To solve it you can do "eventual consistency". Assume that the failing message will eventually be true, since the state of the server is not yet what it needs to be because another event needs to be handled first. You add it to the queue again, and hopefully it will be possible this time.

## Sources
- https://www.youtube.com/watch?v=ADp7_3ygB2M
