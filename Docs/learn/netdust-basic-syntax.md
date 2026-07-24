# Basic Syntax

Now that your project is set up, let's write some actual netdust code. This guide covers the core building blocks: file structure, variables, rooms, and control flow.

---

## File Structure

Every `.nd` file must start with a `code start` marker:

```netdust
code start

bring : std.io

room main():
    call std.io.println("Hello, netdust!")
end;
```

Comments can be written with either `//` or `#`:

```netdust
// this is a comment
# this also works
```

---

## Variables

netdust supports three variable keywords: `var`, `num`, and `bool`.

```netdust
var name = "admin"
num count = 3
bool ready = true
```

---

## Rooms

A **room** is netdust's equivalent of a function. Every program needs a `main()` room as its entry point. A room block ends with `end;`.

```netdust
room greet(name):
    call std.io.println("Hi, " + name)
end;

room main():
    call greet("admin")
end;
```

---

## Bringing in Libraries

Use `bring :` to import a module before using it:

```netdust
bring : std.io

room main():
    call std.io.println("printed via std.io")
end;
```

---

## Conditionals

netdust uses `if`, `else if`, and `else:` for branching:

```netdust
room main():
    num score = 7

    if (score > 5):
        call io.println("passed")
    end;
    else if (score == 5):
        call io.println("borderline")
    end;
    else:
        call io.println("failed")
    end;
end;
```

---

## Next Steps

You now know the basics of netdust syntax. Head over to [Learning Resources](/Docs/learn/learning-resources.md) for more tutorials.
