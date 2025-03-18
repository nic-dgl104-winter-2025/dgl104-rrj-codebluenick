[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MMj2nZMu)
# Rsearch and Reflection Journal
Research and Reflection Journal for DGL 104 course

## Week 8 (Week of Feb 25th)

This week was a mix of getting back to some core development principles and starting to look outward toward how users actually experience the things we build.

I started by accepting the GitHub classroom invite and getting my repository up and running. After that, I spent time reviewing the mid-semester materials, which revisited important coding habits like writing good documentation, debugging properly, refactoring code, and testing thoroughly. It was a solid reminder that no matter how much we build, the basics still matter.

One of the highlights this week was the lecture on user stories and functional requirements. It really helped me see development in a new way. Instead of just thinking about code, I was encouraged to step into the shoes of users and think about what they actually need. It’s a small shift, but it made me realize that even simple apps solve real problems.

For the required activity, I had to research a new programming language. I chose Lua – something I had heard about before but never really explored. Turns out, it’s quite popular in game development (Roblox, for example) and is also used in embedded systems. I found some useful resources, like the official [Lua.org](https://www.lua.org/) site for documentation, [LuaRocks](https://luarocks.org/) for managing Lua packages, and [LuaJIT](https://luajit.org/), which helps make Lua faster. It’s a pretty lightweight language, and I can see why it’s valued for games and embedded systems.

### Simple Lua Example

```lua
-- Lua example: printing and basic function
print("Exploring Lua for the first time!")

function greet(name)
    print("Hello, " .. name .. "!")
end

greet("World")
greet("Lua Learner")
```
### LuaRocks Example (Package Management)

**LuaRocks** is a package manager for Lua. It helps manage libraries and dependencies easily. Here's an example of how to install and use the popular `luasocket` library.

### Installation:
```bash
# In terminal:
luarocks install luasocket
```

### Example usage in Lua:

> In this example, we install luasocket using LuaRocks and then use it to make a basic HTTP request in Lua.

```lua
-- Using LuaSocket to make a simple HTTP request
local http = require("socket.http")

local body, code = http.request("http://example.com")
if code == 200 then
    print("Response body:")
    print(body)
else
    print("Failed with code: " .. code)
end
```

## LuaJIT Example (Just-in-Time Compiler)

**LuaJIT** is a JIT compiler that runs Lua code faster by optimizing it at runtime.

### Running a Lua script with LuaJIT:
```bash
luajit myscript.lua
```
**Script example:**

```lua
-- LuaJIT will optimize this loop
local sum = 0
for i = 1, 1e6 do
    sum = sum + i
end
print("Sum is: " .. sum)
```

### Simple Game Development Example (Movement Simulation)

### Example in Lua:
```lua
-- Basic movement simulation in Lua (game style)
local player = { x = 0, y = 0 }

function movePlayer(dx, dy)
    player.x = player.x + dx
    player.y = player.y + dy
    print("Player position: (" .. player.x .. ", " .. player.y .. ")")
end

-- Simulate moving right and up
movePlayer(1, 0) -- right
movePlayer(0, 1) -- up
movePlayer(1, 1) -- diagonally
```


We also got to write user stories based on WhatsApp. I came up with:
- *"As a user, I can quickly send a text message from my contact list."*
- *"As a user, I can add new contacts directly from the message screen."*

Thinking through the acceptance criteria made me realize how much thought goes into simple actions like adding a contact – it’s easy to overlook how much UX design is at play behind the scenes.

Another key decision I made this week was choosing Javascript for my Application Development Project. After two semesters working with it and using it in some personal projects, I feel comfortable but also curious to dive deeper. I’m hoping to explore more advanced Javascript features and strengthen my web app development skills.

Lastly, I took some time on GitHub to star projects and topics related to Javascript and web app dev in general. It was cool to see how many open-source tools are out there, and it gave me a few ideas for how I might approach the project.

### Reflection
Overall, this week felt like a nice bridge between technical basics and user-centered thinking. The conversations on Slack were a bonus too – reading what others shared about languages like Haskell and Processing expanded my view a bit. It’s easy to get locked into the tools you know, but this week reminded me that there’s always more out there to learn.

### Bibliography:
- [Lua Official Website](https://www.lua.org/)
- [LuaRocks](https://luarocks.org/)
- [LuaJIT](https://luajit.org/)



---

## Week 9 (Week of March 4th)

This week was all about diving into **design patterns**, and it really clicked with me how important these patterns are in writing clean, maintainable code. Ashley introduced the topic in the video lecture, and Dibya contributed some useful insights. 

Design patterns were explained as reusable solutions to common coding problems. I liked the analogy of thinking about them like recipes – not set in stone, but flexible depending on the situation. It’s cool how they act as a shared language for developers, making it easier for teams to understand and maintain each other’s code.

The video examples helped too, showing patterns in both Java and Kotlin, which was perfect since I'm familiar with both languages. I also checked out additional resources like Refactoring Guru to see how these patterns work across different languages. It’s interesting to notice how the same pattern might look slightly different depending on the language family.

### Activities I Completed:

- I started researching design patterns more deeply and picked four that stood out to me for further study:
  1. **Singleton Pattern** – Ensures only one instance of a class exists (e.g., managing global app state).
  2. **Observer Pattern** – A great pattern for things like event handling or notifications (e.g., UI updates).
  3. **Factory Pattern** – Simplifies object creation when dealing with complex logic (e.g., creating different types of UI components).
  4. **Decorator Pattern** – Adds functionality to objects without changing their structure (e.g., adding scrolling to a window).

### 1. Singleton Pattern
**Purpose:** Ensures only one instance of a class exists.

```javascript
class Singleton {
    constructor() {
        if (Singleton.instance) {
            return Singleton.instance;
        }
        Singleton.instance = this;
    }

    log() {
        console.log("Singleton instance in action!");
    }
}

const singleton1 = new Singleton();
singleton1.log();

const singleton2 = new Singleton();
console.log(singleton1 === singleton2); // true
```
Use case: Managing global app state.

### 2. Observer Pattern

**Purpose:** A pattern useful for event handling or notifications.

```javascript
class Subject {
    constructor() {
        this.observers = [];
    }

    subscribe(observer) {
        this.observers.push(observer);
    }

    notify(data) {
        this.observers.forEach(observer => observer.update(data));
    }
}

class Observer {
    update(data) {
        console.log("Observer received data:", data);
    }
}

const subject = new Subject();
const observer1 = new Observer();
subject.subscribe(observer1);
subject.notify("New Event");
```

- I also read through the **Application Development Coding Project** assignment carefully. The rubric gave me a clearer picture of what’s expected, so now I feel a bit more grounded as I move forward.

- Next up, I checked out the new **Research and Reflection Journal guide** on GitHub. It’s helpful – I now have a clearer idea of how to approach writing my journal entries, especially around connecting research to my project work.

- I spent some time on GitHub reading **“How to Contribute to Open Source”** from the Open Source Guides. It broke down the process in a way that made it seem much more approachable. What stood out to me most was section 2, where it talks about different types of contributions – like fixing bugs, improving documentation, or suggesting new features. Personally, I think I’d enjoy contributing through documentation or tackling beginner-friendly issues as a way to ease into open source.

  Section 4 on “Finding a project” was super useful too. I browsed GitHub Explore and some Open Source Friday links and found a few interesting repositories I might want to follow up on later.

### Reflections:
Looking at everything this week, I’m feeling more confident in my choice to stick with Javascript for the project. It fits well with what we’re building.

The next step for me is to help my group set a rough project timeline so we can stay on track. The challenge now is balancing research, coding, and contributing to open source, but I’m looking forward to it!

---

### Links I Found Helpful:
- [Refactoring Guru](https://refactoring.guru/design-patterns)
- [GitHub Open Source Guide](https://opensource.guide/how-to-contribute/)
