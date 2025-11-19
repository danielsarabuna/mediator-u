mediator-u

A lightweight, fast implementation of the Mediator pattern designed for Unity.
It enables decoupled communication between game systems via commands, queries, and events — keeping your architecture clean and modular.

✨ Features
- Command / Query / Event messaging model.
- Zero dependencies — works out of the box.
- Minimal boilerplate — simple interfaces and intuitive usage.
- Unity-friendly — fully compatible with IL2CPP and mobile builds.
- Flexible architecture — works well with MVVM, ECS, DDD, VContainer, MessagePipe, UniTask, and other patterns/tools.

---

🚀 Quick Start

1. Define a command

```csharp
public struct MovePlayerCommand : ICommand
{
    public Vector3 Position;
}
```

2. Create a handler

```csharp
public class MovePlayerHandler : ICommandHandler<MovePlayerCommand>
{
    public UniTask Handle(MovePlayerCommand command)
    {
        Player.Instance.MoveTo(command.Position);
        return UniTask.CompletedTask;
    }
}
```

3. Send the command

```csharp
await mediator.Send(new MovePlayerCommand
{
    Position = new Vector3(5, 0, 3)
});
```

---

📦 Installation

Add to Unity via Git URL:

https://github.com/danielsarabuna/mediator-u.git

Or download and import the package manually.

---

🧩 Architecture

Mediator-U supports three message types:

| Type | Purpose | Returns a result |
|------|---------|------------------|
| ICommand | Execute an action | ❌ |
| IQuery   | Request data       | ✔️ |
| IEvent   | Broadcast to multiple listeners | ❌ |

Each message is handled by a dedicated handler, resulting in clean, modular, and testable code.

---

🧪 Testing

- Works with any C# testing framework (NUnit, xUnit, etc.).
- Easy to mock due to simple interfaces.
- Does not require Unity Test Runner.

---

🛠 Compatibility

- Unity — 2020 or newer
- Backends — Mono, IL2CPP
- Platforms — Mobile, PC, WebGL

---

📜 License

MIT — free for commercial and open-source use.
