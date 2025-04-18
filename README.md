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

### 3. Factory Pattern

**Purpose:** Simplifies object creation logic.

```javascript
class Button {
    render() {
        console.log("Render a generic button");
    }
}

class IconButton extends Button {
    render() {
        console.log("Render a button with an icon");
    }
}

class ButtonFactory {
    static createButton(type) {
        if (type === "icon") {
            return new IconButton();
        } else {
            return new Button();
        }
    }
}

const btn1 = ButtonFactory.createButton("icon");
btn1.render();

const btn2 = ButtonFactory.createButton("simple");
btn2.render();
```
Use case: Creating different types of UI components.

### 4. Decorator Pattern

**Purpose:** Adds new functionality to an object without modifying its structure.

```javascript
function addScroll(feature) {
    feature.scroll = function() {
        console.log("Scrolling added to the feature");
    };
    return feature;
}

const windowFeature = {
    draw: function() {
        console.log("Drawing window");
    }
};

const decoratedWindow = addScroll(windowFeature);
decoratedWindow.draw();
decoratedWindow.scroll();
```
Use case: Adding extra behaviour like scrolling to a window.

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




---


## Week 10 (Week of March 11th)

This week we shifted focus toward architectural thinking with **MV\*** patterns, particularly **MVC** and **MVVM**. Ashley’s lecture and Dibya’s notes provided a great breakdown of how MV* patterns differ from the more traditional design patterns we studied last week. 

I found the distinction between design patterns and architectural patterns useful—where design patterns help solve smaller-scale problems, MV* patterns guide the overall structure of an entire app. The comparison helped me realize how these structures shape everything from logic to UI handling, especially when working with mobile and web apps.


### MV* Patterns: MVC vs MVVM

The lecture explained how **MVC (Model-View-Controller)** and **MVVM (Model-View-ViewModel)** differ, especially depending on the framework. I’ve had some exposure to both through coursework and side projects—like using **MVVM** with **Jetpack Compose** for Android, which I find much cleaner and more reactive compared to older **MVC** setups.

We also got several helpful video links to explain these concepts. Seeing the same architecture explained in different frameworks helped reinforce the big picture for me.

- [MVVM Explained Simply](https://www.youtube.com/watch?v=PkvOL-hWnGs)
- [MVC vs MVVM](https://www.youtube.com/watch?v=o1M5hFLjcXw)

---

### Code Examples in JavaScript

#### MVC Pattern (Model-View-Controller)

```javascript
// Model
class Model {
  constructor() {
    this.data = "Hello MVC";
  }

  getData() {
    return this.data;
  }
}

// View
class View {
  render(data) {
    console.log("View rendering:", data);
  }
}

// Controller
class Controller {
  constructor(model, view) {
    this.model = model;
    this.view = view;
  }

  updateView() {
    const data = this.model.getData();
    this.view.render(data);
  }
}

// Usage
const model = new Model();
const view = new View();
const controller = new Controller(model, view);
controller.updateView();
```

#### MVVM Pattern (Model-View-ViewModel using simple binding)

```javascript
Copy
Edit
// Model
class Model {
  constructor() {
    this.message = "Hello MVVM";
  }
}

// ViewModel
class ViewModel {
  constructor(model) {
    this.model = model;
    this.bindings = [];
  }

  bind(callback) {
    this.bindings.push(callback);
  }

  setMessage(newMessage) {
    this.model.message = newMessage;
    this.bindings.forEach(cb => cb(this.model.message));
  }

  getMessage() {
    return this.model.message;
  }
}

// View (binding simulated)
const model = new Model();
const viewModel = new ViewModel(model);

viewModel.bind((newMsg) => {
  console.log("View updated:", newMsg);
});

console.log("Initial:", viewModel.getMessage());
viewModel.setMessage("Updated via ViewModel");
```



---


## Week 11 (Week of March 18th)

This week’s focus was all about **Object-Oriented Programming (OOP)**. We revisited core concepts like encapsulation, abstraction, inheritance, and polymorphism—some of which I’ve worked with before, but this time we went deeper into **why** these concepts matter, not just how they work.

The first video was familiar, but the second brought new insights on how OOP helps manage complexity in larger projects. It made me realize that understanding OOP isn't just useful—it's kind of essential if you want your codebase to grow and still be maintainable.


### Applying OOP in Our Group Project

For our group project, we’re using **JavaScript**, which **fully supports OOP**, even if it's a bit more flexible (and less strict) than languages like Java or C++. I’m mainly applying OOP concepts in how we model app features, like users, messages, and UI components.

#### Example: OOP with JavaScript in Our STMS App
```javascript
// services/UserService.js
const User = require('../models/userModel');

class UserService {
    static async getAllUsers() {
        return await User.find({}, 'name email role');
    }

    static async bulkUpdateRoles(users) {
        for (const usr of users) {
            await User.findByIdAndUpdate(usr._id, { role: usr.role });
        }
    }
}

module.exports = UserService;
```
I have created a service class to encapsulate logic like fetching and updating users. We also plan to implement a User class that holds account info and related methods (like login, logout, update profile). This modular setup lets us build and test each feature in isolation.

## Concepts Revisited

### Encapsulation
Keeps internal data safe. We’ll use private properties and getter/setter methods where appropriate.

### Abstraction
We'll expose only what's necessary in each class. For instance, the `Message` class exposes `display()` but hides the formatting logic inside.

### Inheritance
We’re considering a base `Component` class that UI elements like buttons or forms can extend. This would reduce repetition and keep the code cleaner.

### Polymorphism
Still exploring where to apply it. We may use polymorphism when rendering different types of messages (text, image, video), each with its own `display()` method but accessed the same way.


## Why OOP Matters for Us

- **Reusability** – Shared behaviors like authentication or data formatting can be put in base classes.
- **Modularity** – We’re dividing our app into small OOP-driven modules so that we can work in parallel.
- **Scalability** – It’ll be easier to add new features, like notifications or chat groups, by extending existing classes.
- **Testing** – Each class can be tested in isolation before integration.


## Reflection & Challenges

### Is JavaScript OOP capable?
Yes, JavaScript is **fully OOP-capable** through class syntax (introduced in ES6). It also supports **functional** and **prototype-based** programming, making it **multi-paradigm**. This flexibility is helpful for blending styles where needed—though we’re focusing on OOP for clarity and structure.

### Biggest challenge this week?
Trying to map traditional OOP concepts like inheritance to JavaScript’s looser structure. In languages like Java, inheritance is more rigid and obvious. In JavaScript, we need to be more intentional about using class-based syntax to get similar results.


## Connecting with the Community

I browsed the community’s Discord (for the repo I’m contributing to). I didn’t post yet, but I read through the threads and got a feel for the culture. People are generally helpful and respectful. I might introduce myself next week as I move closer to finalizing my contribution.


## What’s Next?

- Continue refining OOP structure in our app.
- Finalize the `User` and `Component` class hierarchy.
- Finish external contribution task and prep for final week reflections.


## Resources That Helped

- [OOP Part 1](https://www.youtube.com/watch?v=hdVYcOgNKfc)
- [OOP Part 2](https://www.youtube.com/watch?v=jzP2sw3I1nc)
- [JavaScript OOP Refresher – MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Classes_in_JavaScript)
- [Wikipedia: Multi-Paradigm Programming Languages](https://en.wikipedia.org/wiki/Multi-paradigm_programming_language)


## OOP Summary Table

| Principle     | Purpose                                      | Project Application                              |
|---------------|----------------------------------------------|--------------------------------------------------|
| Encapsulation | Hides internal state                         | `Message` class restricts direct data access     |
| Abstraction   | Exposes only relevant details                | `display()` method for showing messages          |
| Inheritance   | Reuses base class properties & methods       | Potential `Component` class for UI elements      |
| Polymorphism  | Shared interface with varied implementation  | `display()` used by different message types      |



---


## Week 12 (Week of March 25th) 

This week’s focus was on **Functional Programming**, and it was a refreshing shift in thinking. I was curious to dive deeper into how functional programming principles can improve the quality of our code—even in projects that aren’t purely functional.

---

### Functional Programming – Key Takeaways

We didn’t focus on pure functional languages (like Haskell or Clojure), but instead on **functional-style tools** that are available in most modern languages. The core message was to embrace methods like `map()`, `filter()`, and `reduce()` for working with collections more efficiently and cleanly.

This really clicked with me. I’ve used these methods before in JavaScript and Kotlin, but I never thought of them as part of a larger programming paradigm. Now I understand they’re functional tools that help make code more **declarative**, **concise**, and **less error-prone** than traditional loops.



### JavaScript Functional Example: Filtering Tasks

Here’s a quick example we could use in our group project when filtering chat messages:

```javascript

```javascript
const filteredTasks = filter
  ? tasks.filter(task =>
      task.status === filter || task.priority === filter
    )
  : tasks;


```
This example shows how functional programming can simplify conditional logic. Instead of using if-else statements or loops, the filter() method is used to create a new array based on the selected status or priority. It’s clean, readable, and easy to extend.

## Group Project Progress

We're now in the final stretch of development. This week, we focused heavily on tying up core functionality and doing some light refactoring. We’re also working on making the UI more responsive and consistent. I am trying to implement the backend data fetch to the frontend as it is currently using mock data. 

I’ve also been documenting progress in our **Research and Reflection Journal**, especially where we’ve applied **OOP** or **functional programming** ideas. We’ve still got work to do, but everything is coming together well.


## Final Week Priorities

- Finalize the remaining code for our app.
- Getting all the data from the backend.
- Clean up repetitive loops and consider converting them to `map()`, `filter()`, or `reduce()`.
- Finish up our group journal entries and project documentation.
- Ask any last-minute questions in class and prep for submission.


## Helpful Resource

- [Functional Programming for Beginners](https://www.youtube.com/watch?v=_uXZ8HvHH7o)


## Reminder

**Community Code Project** is due on **Sunday, April 6th, 2025 at 11:59pm PST**. Time to lock in and finish strong!


I’m really glad this course introduced us to both **OOP** and **Functional Programming**. Seeing both sides made me appreciate how combining these styles leads to better, cleaner software. Looking forward to wrapping everything up next week!

