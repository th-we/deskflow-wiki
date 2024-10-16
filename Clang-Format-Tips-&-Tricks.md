> [!WARNING]
> WIP: This work-in-progress article is not yet finished.

Inspired by: KDE's doc, [Clang-format automatic code formatting](https://community.kde.org/Policies/Frameworks_Coding_Style#Clang-format_automatic_code_formatting)

For developers who are new to Clang-Format, there can be a temptation to fight against it. However, it's much more productive to go with it and accept it's idiosyncracies because the benefits of using it far outweigh the costs.

Pros:
- You don't need to worry about the code style either when developing or during code review, which reduces the cognitive load.

Cons:
- It may do things in ways you don't expect, such as breaking lines in places that could make code less readble.

# Line breaks

Use a comment at the end of the line to force a line break

Some developers may not find this so readable because the string is on the same line as the vars:
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
