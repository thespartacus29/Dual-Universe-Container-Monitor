# Container Monitor

This script allows you to monitor the contents of up to 28 containers and display Name, Qty and Status on a screen.

## :page_with_curl: Elements Required

- 4 Programming Boards
- 3 Databanks
- 1 Manual Switch
- 1 Relay
- 1 M Screen

## :page_facing_up: Parameters Documentation

<details>
 
| Parameter | Description | Default value | Type |
| ------------- | ------------- | ------------- | ------------- |
| showSafetyStock | Displays safety stock along with Qty i.e 100/200 instead of 100 | true | Boolean |
| containerEnabled | Uncheck for Slots with container name you don't want to use. There is one flag per container | true | Boolean |
| DBenabled | Uncheck if not using all the boards/Databanks. One per DB | true | Boolean |
| criticalColor | Use to change the default red color for the CRITICAL Status | "red" | String |
| lowColor | Use to change the default yellow color for the LOW Status | "yellow" | String |
| goodColor | Use to change the default green color for the GOOD Status | "gree" | String |
| containerLabel | Name that will display on screen for the container. One per container | "Default Label" | String |
| containerDensity | The Unit Mass for the item being monitored inside the container | 0 | Number |
| containerSafetyStock | This is the optimal numer of units you want in the container, what you consider 100% | 0 | Number |
  
</details>

## :pushpin: Features

<details>
  <summary>Display Qty or Qty/SafetyStock </summary>
  
  ![monitorsafetystockon](Resources/SafetyStockOn.png)
  ![monitorsafetystockoff](Resources/SafetyStockOff.png)
  
</details>
<details>
  <summary>Change default status colors</summary>
  
  Use [this](https://www.quackit.com/css/color/charts/css_color_names_chart.cfm) to help you pick colors if needed
</details>

## :gear: Setup
To add each script to a Programming board: 
  1. Copy the script to your clipboard 
  2. Right-click on the Programming Board > Advanced > Copy Lua configuration from Clipboard
  3. Go into Build Mode(B) and use the Link Element Tool to link the board to each of of the elements ( screen, databanks, containers etc )

:boom:NOTE: Linking the right slot to the correct element is a MUST. This is where most people run into issues. I suggest linking one element at the time and going into the LUA script (hover over the programming board and press Ctrl+L or right-click on the programming board > Advanced > Edit LUA script ) to see which slot gets linked. If you link the elements out of order you will be displaying the wrong quantities and most likely getting script errros as the code will try to execute on the wrong elements.

### Primary Board
1. Add script to the board
2. Open the Lua Editor (hover over the programming board and press Ctrl+L or right-click on the programming board > Advanced > Edit LUA script ) and look at the order of the slots. 
3. Link the elements (Databanks, screen, switch, containers) in the correct order 
4. Link switch to Relay
5. Link Relay to screen and each Secondary Board. This will ensure when you turn on/off the primary board all other elements get turn on/off as well.
6. Edit the LUA Parameters ( Right-click on the Programming Board > Advanced > Edit LUA parameters)
 - title: Enter a title for the top of the screen. DO NOT remove the double quotes
 - container1Label: Enter the name of the item inside container1. DO NOT remove the double quotes
 - container1Density: Enter a number that represents the Unit Mass for the item inside container1. 
 <details> 
 
 ![unitmass](Resources/Unit Mass.png)</details>
 
 - container1SafetyStock: Enter 

### Secondary Boards
1. Add script to the board
2. Open the Lua Editor (hover over the programming board and press Ctrl+L or right-click on the programming board > Advanced > Edit LUA script ) and look at the order of the slots. 
3. Link the elements (Databanks, containers) in the correct order 

Finally turn off/on the Primary board to ensure everything is running fresh. Enjoy :)
