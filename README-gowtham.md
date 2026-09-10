# Gowtham Revanur Personal Reflection

GitHub username: Grevanur

## What surprised me most

What surprised me most was how the widget tree and controller keep the tabs connected without me manually changing every part of the screen. My `TabBar` and `TabBarView` both use `_tabController`, so selecting a tab updates the visible page and the tab indicator together. I originally thought I would need to directly change text or show and hide widgets myself. Instead, Flutter rebuilds the UI from the current state. Seeing the `Scaffold`, `AppBar`, `TabBar`, `TabBarView`, and four tab pages nested together made the widget tree feel much more real.

## Concept that took the longest to understand

Controllers and lifecycle took the longest to click for me. It became clearer when I saw that `_tabController` is created once in `initState()` instead of inside `build()`. The `build()` method can run many times, but the controller should stay available while the tab screen exists. Then `dispose()` is the matching cleanup step when the screen is removed. Understanding that the controller has a listener and an animation ticker helped me see why forgetting `_tabController.dispose()` could waste resources and create problems in a larger app.

## GitHub workflow reflection

The GitHub workflow that felt least familiar was the difference between a branch on GitHub and a branch on my computer. I created `branchGR` on GitHub, but cloning the repository first placed me on `main`. I used `git branch -a` to see the remote branches, then used `git switch --track origin/branchGR` to connect my local work to the correct branch. I worked through it one command at a time by checking `git status`, adding my changes, committing them, and pushing the branch. This made the branch workflow feel less confusing.

## What I would do differently next time

If I rebuilt this activity tomorrow, I would set up the shared repository, team roles, and branches before writing any answers. I would also sketch the widget tree first and use one source of truth, such as `tabs.length`, for the number of tabs. While building the app, I would test each tab right after changing it and check the widget nesting carefully before changing sizes or layout. For GitHub, I would make smaller commits more often and open the Pull Request earlier so my teammate could review the work sooner.