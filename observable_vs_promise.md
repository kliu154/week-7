#### 1. Creation and subscription
Observables are not executed until a consumer subscribes. The `subscribe()` executes the defined behavior once, and it can be called again. Each subscription has its own computation. Resubscription causes recomputation of values.

Promises execute immediately, and just once. The computation of the result is initiated when the promise is created. There is no way to restart work. All `then` clauses (subscriptions) share the same computation.

#### 2. Chaining
Observables differentiate between transformation function such as a map and subscription. Only subscription activates the subscriber function to start computing the values.

Promises do not differentiate between the last `.then` clauses (equivalent to subscription) and intermediate `.then` clauses (equivalent to map).

#### 3. Cancellation
Observable subscriptions are cancellable. Unsubscribing removes the listener from receiving further values, and notifies the subscriber function to cancel work.

Promises are not cancellable.

#### 4. Error handling
Observable execution errors are delivered to the subscriber's error handler, and the subscriber automatically unsubscribes from the observable.

Promises push errors to the child promises.

<br><br>

Overall, the key differences between Observables and promises include:
- Observables are declarative; computation does not start until subscription. Promises execute immediately on creation. This makes observables useful for defining recipes that can be run whenever you need the result.

- Observables provide many values. Promises provide one. This makes observables useful for getting multiple values over time.

- Observables differentiate between chaining and subscription. Promises only have `.then()` clauses. This makes observables useful for creating complex transformation recipes to be used by other part of the system, without causing the work to be executed.

- Observables `subscribe()` is responsible for handling errors. Promises push errors to the child promises. This makes observables useful for centralized and predictable error handling.
