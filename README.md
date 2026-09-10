
Q1.  Widget Tree
 
MaterialAPP
--- Tab controller
---tabnonscroll
--Scaffold
-top Bar
-App Bar
tabs 1-4
tab view
-Tab 1
    Text + Alert
-Tab 2
    textbox + Image
-Tab 3
    Elevated Button + Snackbar
-Tab 4
    list components
--BottomAppBar
 
If you wanted to add a 5th tab you would need to go through and change the length of the tab controller and the final tab context to create and add the 5th tab into the app. The tab controller is in control of the tabs and it being viewed. so if this specific node isn't changed, the 5th node would not be updated as present when in the demo view of the app.


Q2. The tab clicker widget could be identified as a stateless widget because it doesn't do anything but display which tab is selected. Once its uploaded, it doesn’t need to be changed. No information is needed to be kept or remembered to display that information. In the case that this is switched to stateful, it would not be able to run without errors as flutter expects a state to be able to manage or change with the widget at any given point. If anything, it would become super unnecessary.
 
  The main tab 1 is stateful as it must keep its information to be able to update or change later on. It includes many states that hold information regarding the widget to be able to update it. If the widget doesn't have the states, it will not be able to be updated or changed. will receive errors trying to do this as no states are being called.
