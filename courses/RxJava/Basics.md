#  RxJava
- can be though as **library** that give us easy way to use **observer pattern.**
- there are Java Observale but it is **complex**, **layered**. 
- is a Java implementation for **ReactiveX**.

### Component
 Observable | Observer(Subscribers)
 ---------- | ---------------------
 what you watch | watcher
 list of values/data | consumer for data


## Observable Categories 
- New event: (UI events).
- Change event: (change title after data update).
- Complete event: tasks of code (network calls).

## Subscriber methods
- `onSubscribe() `-> when subcribe to observable  
- `onNext() `-> when a new value is emited/publisged 
- `onError()` -> when error ocurr
- `onComplete()` -> when complete task 


# Observable Types 
- **Relay**
    - easiest piece of work.
    - **hot observable**: only get **most current values** or default
    - **never error out** or **complete** so it is **save for UI**. 
- **Subject**
    - little more complex.
    - can **receive onComplete/onError** so *not ideal* for UI.
    - **Die** after onComplete/onError.
    - **can observe** and also **be observed**.
    - **hot observable**:but it **receive number of events** depending of its type.
    - flavor of subjects:
        - **Behavior**:- **last event** or defaut (ex as kid remember last thing).
        - **Publish** :- start from **zero events** so use **only new events**(ex for academia no matter books published by prof only concern what new book to publish).
        - **Replay**:- hav n of previous events 
        `let subject = ReplaySubject<String>.create(bufferSize : 3)`

- **Observable**: used for **complex tasks** such as chaining network calls.


## Traits 
are one-off tasks that cann be wrapped in asingle observable, there are 
- **Single** that accept (onNext, onError).
- **Completablem** that accept (onComplete, onError).
- **Maybe** that accept (onNext/onComplete, onError).

when you see one-off call such as network call so it is a greate place to use Traits.







