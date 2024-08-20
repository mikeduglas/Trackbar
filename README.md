# TrackBar control

### Overview
Modern Windows applications use cute TrackBar control, below is a screenshot from "Photos" application:

![Photos resize dialog](https://github.com/mikeduglas/trackbar/blob/master/screenshots/Photos_Resize.jpg?raw=true)  

I decided to mimic this control in Clarion.

![Screenshot1](https://github.com/mikeduglas/trackbar/blob/master/screenshots/trackbar_demo1.jpg?raw=true)  
![Screenshot2](https://github.com/mikeduglas/trackbar/blob/master/screenshots/trackbar_demo2.jpg?raw=true)  

### Features
- The control supports both horizontal and vertical orientations, each orientation supports top/left, center and bottom/right alignments.
- Mouse wheel is supported.
- keyboard is supported (arrow keys, home key, end key).
- TAB control order is supported.
- 2 types of step values are supported: a step and a small step. When SHIFT key is pressed, arrow keys and mouse wheel change the value by a small step.
- Immediate mode: when true (by default), OnNewSelection event is fired whenever a user changes the value.

### Demo app
You can see how new TrackBar control works running demo\Trackbar_demo.exe.  
The code is quite primitive:

```
  PROGRAM
  INCLUDE('trackbar.inc'), ONCE
  MAP
    INCLUDE('printf.inc'), ONCE
  END

Window                        WINDOW('Trackbar demo'),AT(,,260,100),CENTER,GRAY,SYSTEM,FONT('Segoe UI',9)
                                REGION,AT(16,26,186,32),USE(?rgnQuality)
                                PROMPT('Prompt1'),AT(16,14),USE(?lblQuality)
                                BUTTON('Close'),AT(197,76,47),USE(?btnClose),STD(STD:Close)
                              END

tbQuality                     CLASS(TTrackBar)
OnNewSelection                  PROCEDURE(LONG pValue), DERIVED, PROTECTED
                              END
  CODE
  OPEN(Window)
  
  tbQuality.Init(?rgnQuality)
  tbQuality.SetRange(10, 100, 5, 1)  !- step: 5; small step: 1
  tbQuality.SetValue(50)
  tbQuality.SetAlignment(TrackbarAlignmentCenter)

  ACCEPT
  END
  
tbQuality.OnNewSelection      PROCEDURE(LONG pValue)
sQuality                        STRING(6), AUTO
  CODE
  IF pValue < 50
    sQuality = 'Low'
  ELSIF pValue < 80
    sQuality = 'Medium'
  ELSE
    sQuality = 'High'
  END
  ?lblQuality{PROP:Text} = printf('Quality: %i%% (%s)', pValue, sQuality)
```

### Requirements
- Clarion versions: C6.3 and higher.
- Template chains: ABC, Clarion.
- Multi dll apps supported.

### Contacts
- <mikeduglas@yandex.ru>
- <mikeduglas66@gmail.com>

### Price
- 120 USD via ClarionShop 
