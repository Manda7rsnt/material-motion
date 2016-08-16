# TransitionDriver

**Scheduler**: Store a single `Scheduler` instance while the transition is active.

Example pseudo-code:

    TransitionController {
      private var scheduler: Scheduler
    }

**Replication controller**: Store a single `ReplicationController` instance while the transition is active.

Example pseudo-code:

    TransitionController {
      private var replicationController: ReplicationController
    }

**Transition director**: Store a single `TransitionDirector` instance while the transition is active.

Example pseudo-code:

    TransitionController {
      private var director: TransitionDirector
    }


