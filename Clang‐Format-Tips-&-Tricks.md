> [!WARNING]
> WIP: This work-in-progress article is not yet finished.

Inspired by: KDE's doc, [Clang-format automatic code formatting](https://community.kde.org/Policies/Frameworks_Coding_Style#Clang-format_automatic_code_formatting)

For developers who are new to Clang-Format, there can be a temptation to fight against it. However, it's much more productive to go with it and accept its quirks because the benefits of using it far outweigh the costs.

**Pros:**
- You don't need to worry about the code style either when developing or during code review, which reduces cognitive load.
- Ensures consistent formatting across the entire codebase, making it easier for teams to work together.
- Saves time by automating formatting tasks that would otherwise be done manually.
- Reduces debates over subjective style preferences in code reviews.
- Helps with code refactoring by keeping the formatting clean during changes.
- Can be easily integrated into CI/CD pipelines for automatic checks.

**Cons:**
- It may do things in ways you don't expect, such as breaking lines in places that could make code less readable.
- Developers may feel a loss of control over certain style preferences or nuances.
- Configuring it to match existing codebases with unique styles can be time-consuming.
- Some formatting decisions, such as alignment or bracket placement, can clash with personal or team preferences.

# Line breaks

Use a comment at the end of the line to force a line break

Some developers may struggle to mentally parse function args when they're not deliberately placed:
```
  LOG_DEBUG1(
      "say hello version %s %d.%d", protocolName.c_str(), helloBackMajor,
      helloBackMinor);
```

It may be a little easier for some developers to grok if they force a break with `//` at the end:
```
  LOG_DEBUG1(
      "say hello version %s %d.%d", //
      protocolName.c_str(), helloBackMajor, helloBackMinor);
```

# Overriding `#include` ordering

Split your includes up into groups to force ordering. This can be useful when there are accidental (or nasty) interdependencies between headers.

# Formatting enumerations

Add a trailing comma to tell Clang-Format that you want enums and initializer lists on separate lines.

Without:
```
enum HelloWorld { kFoo, kBar };
```

With trailing comma:
```
enum HelloWorld {
  kFoo,
  kBar,
};
```

# Last resort, turn it off

```
// clang-format off
Some fragile or from third parties imported code...
// clang-format on
```
