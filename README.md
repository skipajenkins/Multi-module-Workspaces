
---

# 🐹 Go Multi-Module Workspaces

This repository demonstrates how to use Go Workspaces (go.work) to manage and develop multiple Go modules together in a single workspace.

It shows how to:

* Create multiple Go modules

* Link them together locally using go.work

* Import and use functions from another module

* Work with external modules alongside local modules

* Build scalable multi-project Go layouts

---

## 🎯 Learning Objectives

By working through this project, you will learn how to:

* Understand Go module-based project structures

* Use go.work for multi-module development

* Import packages across local modules

* Combine remote dependencies + local modules

* Build clean, scalable Go project layouts
  
---

### 📁 Project Structure
workspace/
├── example/
│   └── hello/
│       ├── go.mod
│       ├── hello.go
│       └── reverse/
│           ├── reverse.go
│           ├── reverse_test.go
│           └── int.go
│
├── hello/
│   ├── go.mod
│   ├── go.sum
│   └── hello.go
│
├── go.work
├── go.mod
├── go.sum
├── LICENSE
├── PATENTS
└── README.md

---

### 🧠 What Is a Go Workspace?

A Go Workspace (go.work) allows multiple Go modules to be developed together without publishing them.

It enables:

* Local development across multiple projects

* Clean dependency resolution

* Easy cross-module imports

* No need for replace directives in each module

---

## ⚙️ Setup Instructions
### Step 1: Install Go

Check if Go is installed:
```bash
go version
```

If not installed, download from:
```bash
👉 https://go.dev/dl/
```
---
### Step 2: Clone the Repository
```bash
git clone https://github.com/skipajenkins/Multi-module-Workspaces.git
cd Multi-module-Workspaces
```
---
###Step 3: Initialize Workspace

The project already includes a go.work file:
```bash
go 1.25.6

use (
    ./example/hello
    ./hello
)
```
This tells Go:

Treat both modules as part of one workspace.
---
###Step 4: Run the Application
```bash
cd hello
go run .
```
---
###🧪 Example Output
```bash
olleH 109642
```

This output demonstrates:

* Reversing a string

* Reversing an integer

* Using functions imported from another module

---

## 📜 Code Overview
main.go
```bash
package main

import (
	"fmt"
	"golang.org/x/example/hello/reverse"
)

func main() {
	fmt.Println(reverse.String("Hello"), reverse.Int(24601))
}
```

This program:

* Imports the reverse package

*Calls:

  *reverse.String() → reverses strings

  *reverse.Int() → reverses integers

reverse/int.go
package reverse
```bash
import "strconv"

// Int returns the decimal reversal of the integer i.
func Int(i int) int {
	i, _ = strconv.Atoi(String(strconv.Itoa(i)))
	return i
}
```

This demonstrates:

* String ↔ integer conversion

* Function composition

* Package modularization

---

## 📚 Key Concepts

| Concept | Explanation |
|----------|--------------|
| Go Modules | Project-level dependency management using `go.mod` |
| Workspaces | Combine multiple modules via `go.work` |
| Local Imports | Import local modules cleanly |
| External Modules | Use third-party packages normally |
| Modular Design | Split logic across focused packages |
| Dependency Resolution | Unified build across all workspace modules |


---

## 🧩 Why Use Go Workspaces?

Without workspaces, managing multiple local modules becomes painful:

* Requires many replace directives

* Hard to maintain

* Difficult to scale

With go.work:

✅ Cleaner imports
✅ Faster builds
✅ Easier collaboration
✅ Professional project structure

---

## 🛠️ How This Workspace Works
go.work → links modules
     ↓
example/hello → provides logic
     ↓
hello → consumes logic


This allows:
```
import "golang.org/x/example/hello/reverse"
```

to work locally without publishing the module.

---

## 🧾 Summary

This repository demonstrates:

* Multi-module Go workspace setup

* Local dependency resolution

* Modular Go architecture

* Real-world project layout

* Best practices for scalable Go projects

---


🦫 Built With

* Go

* Go Modules

* Go Workspaces

---

📄 License

This project is open-source and available under the MIT License.

----
