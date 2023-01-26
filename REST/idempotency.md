# Idempotency

For an operation (or service call) to be idempotent, clients can make that 
same call repeatedly while producing the same result. In other words, making 
multiple identical requests has the same effect as making a single request.
Note that while idempotent operations produce the same result on the server (no side effects),
the response itself may not be the same (e.g. a resource's state may change between requests).

The **PUT** and **DELETE** methods are defined to be idempotent. However, there is a caveat on **DELETE**. 
The problem with **DELETE**, which if successful would normally return a `200 (OK)` or `204 (No Content)`, 
will often return a `404 (Not Found)` on subsequent calls, unless the service is configured to "mark"
resources for deletion without actually deleting them. However, when the service actually deletes the 
resource, the next call will not find the resource to delete it and return a `404`. However, the state on
the server is the same after each **DELETE** call, but the response is different.

**GET**, **HEAD**, **OPTIONS** and **TRACE** methods are defined as safe, meaning they are only intended for retrieving data.
This makes them idempotent as well since multiple, identical requests will behave the same.

**POST** is neither safe nor idempotent. It is therefore recommended for non-idempotent resource requests. Making two identical **POST** 
requests will most-likely result in two resources containing the same information.

**PATCH** is neither safe nor idempotent. However, a **PATCH** request can be issued in such a way as to be idempotent, which also helps prevent 
bad outcomes from collisions between two **PATCH** requests on the same resource in a similar time frame.

Resources:
- https://www.restapitutorial.com/lessons/idempotency.html