# 0.5.0
1. [[OPR-22](https://github.com/blindingskies/Slots/pull/22)]: Supports displaying a `UIAlertController` as a `AlertOperation`.
2. [[OPR-26](https://github.com/blindingskies/Slots/pull/26)]: Adds a Block Condition. This allows an operation to only execute if a block evaluates true.
3. [[OPR-27](https://github.com/blindingskies/Slots/pull/27)]: Fixes a bug where the `produceOperation` function was not publicly accessible. Thanks - @MattKiazyk
4. [[OPR-28](https://github.com/blindingskies/Slots/pull/28)]: Supports a generic `Operation` subclass which wraps a `CKDatabaseOperation` setting the provided `CKDatabase`.
5. [[OPR-29](https://github.com/blindingskies/Slots/pull/29)]: Improves the `CloudCondition.Error` to include `.NotAuthenticated` for when the user is not signed into iCloud.

# 0.4.2 - Initial Release of Operations.
Base `Operation` and `OperationQueue` classes, with the following features.

The project has been developed using Xcode 7 and Swift 2.0, with  unit testing (~ 75% test coverage). It has now been back-ported to Swift 1.2 for version 1.0 of the framework. Version 2.0 will support Swift 2.0 features, including iOS 9 technologies such as Contacts framework etc.

1. Operation types:
1.1. `BlockOperation`: run a block inside an operation, taking advantage of Operation features.
1.2. `GroupOperation`: compose one more operations into a group.
1.3. `DelayOperation`: delay execution of operations on the queue.

2. Conditions
Conditions can be attached to `Operation`s, and optionally introduce new `NSOperation` instances to overcome the condition requirements. E.g. presenting a permission dialog. The following conditions are currently supported:
2.1. `MutuallyExclusive`: for exclusivity of a given kind, e.g. to prevent system alerts presenting at the same time.
2.2. `ReachabilityCondition`: only execute tasks when the device is online.
2.3. `CloudCondition`: authorised access to a CloudKit container. 

3. Observers
Observers can be attached to `Operation`s, and respond to events such as the operation starting, finishing etc. Currently observer types are:
3.1. `BackgroundObserver`: when the app enters the background, a background task will automatically be started, and ended when the operation ends.
3.2. `BlockObserver`: run arbitrary blocks when events occur on the observed operation.
3.3. `NetworkObserver`: updates the status of the network indicator.
3.4. `TimeoutObserver`: trigger functionality if the operation does not complete within a given time interval.

