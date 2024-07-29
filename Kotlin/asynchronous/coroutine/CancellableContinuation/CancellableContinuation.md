# CancellableContinuation
## State
| State	| isActive | isCompleted	| isCancelled |
| ----- | -------- | -----------  | ----------- |
| Active (initial state) |	true	| false	| false |
| Resumed (final completed state)	| false	| true	| false |
| Canceled (final completed state) |	false	| true	| true |

```
    +-----------+   resume    +---------+
    |  Active   | ----------> | Resumed |
    +-----------+             +---------+
          |
          | cancel
          V
    +-----------+
    | Cancelled |
    +-----------+
```

## Ref
https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-cancellable-continuation/
