# in_class_01_v3

## My Concept Notes Q3 to Q5

### Q3 Controllers and Lifecycle

In my app, `__TabsNonScrollableDemoState` owns a `late TabController _tabController`. In `initState()`, I create it with `initialIndex: 0`, `length: 4`, and `vsync: this`. The controller is connected to my `TabBar` and `TabBarView`, so it controls which of the four tabs is selected and provides the animation when I switch tabs. I also added a listener that uses `setState()` to save the selected index in `tabIndex`, and `restoreState()` uses that value to return to the same tab later.

Even though my app also has a `DefaultTabController`, my code directly uses `_tabController`, so it must be cleaned up. In `dispose()`, I call `_tabController.dispose()` and `tabIndex.dispose()`. Without those lines, the controller, its listener, and its animation ticker could stay in memory after the screen is removed. Over time, this could waste memory, drain battery, slow the app, or cause active-ticker warnings. A code reviewer would flag it because every controller created in `initState()` should be released in `dispose()`.

### Q4 Declarative UI

Flutter uses declarative UI, which means I describe what the screen should look like for its current state instead of manually changing individual screen elements. In my app, the `build()` method returns the widget tree: a `Scaffold`, an `AppBar`, a `TabBar`, a `TabBarView`, and the four tab pages. When the selected tab changes, my `_tabController` listener calls `setState()` and updates `tabIndex.value`. Calling `setState()` tells Flutter that state changed, so Flutter runs `build()` again and efficiently updates the UI.

An imperative approach would require me to find elements manually and change them step by step. For example, in JavaScript I might use `document.getElementById()`, change text, change colors, and hide or show elements myself. That can become difficult in a large app because changes can be scattered across many event handlers. Flutter's declarative approach is easier for a team to maintain because the widget tree is a clear description of the current screen, and developers can reason from the current state to the expected UI.

### Q5 Team Collaboration

The hardest part of the shared GitHub workflow was keeping the remote branch on GitHub and the local branch on my computer straight. My partner and I set up a shared repository, and I created `branchGR` on GitHub. After cloning the repository locally, I had to use `git switch --track origin/branchGR` so that my local work was connected to the correct remote branch. That made it clearer that creating a branch on GitHub alone does not automatically put me on that branch locally.

On my first day at a software job, I would avoid this friction by reading the team's repository instructions first, confirming my Git name and email, pulling the newest `main` branch, and creating or switching to my assigned branch before editing anything. I would also communicate clearly with my teammate about who is responsible for each task, push small commits regularly, and request a review before merging. This would reduce duplicate work and make pull requests easier to understand.