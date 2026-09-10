## Q1 Widget Tree

My Flutter app is built as a widget tree. At the top, `MyApp` returns a `MaterialApp`, which contains a `DefaultTabController` with a length of four. Inside it is `_TabsNonScrollableDemo`, which returns a `Scaffold`. The `Scaffold` contains an `AppBar`, a `TabBar`, a `TabBarView`, and a `BottomAppBar`.

The `TabBarView` contains four pages. Tab 1 uses a `Container`, `Center`, and `Column` with styled text and an `ElevatedButton` that opens an `AlertDialog`. Tab 2 contains a network image and a `TextField`. Tab 3 contains an `ElevatedButton` that displays a `SnackBar`. Tab 4 contains a `ListView` with `Card` and `ListTile` widgets. The `BottomAppBar` contains `Padding` and a `Text` widget.

If I needed to add a fifth tab, I would first update the `DefaultTabController` because it is the parent controller node that declares the number of tabs for its children. In my current code, I would also update `_tabController`, the `tabs` list, and the `TabBarView` children. A cleaner future improvement would be to use `tabs.length` so the number is defined in one place.

## Q2 Stateless versus Stateful

`MyApp` is a stateless widget because it only creates the general app structure: `MaterialApp`, `DefaultTabController`, and `_TabsNonScrollableDemo`. It does not store changing data itself. Making it stateful would not improve the app; it would only add unnecessary state and lifecycle code.

`_TabsNonScrollableDemo` is stateful because it owns `_tabController` and `tabIndex`, which change as the user switches between tabs. It also uses `initState()` to create the controller, `setState()` to update the selected tab index, and `dispose()` to clean up resources. If I changed this widget to stateless, the app could not manage the controller in the same way, listen for tab changes, restore the selected tab, or safely dispose of the controller. The selected-tab behavior would either break or require the state to be moved somewhere else.
