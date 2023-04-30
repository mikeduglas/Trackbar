# TrackBar control

### Overview
Modern Windows applications use cute TrackBar control, below is a screenshot from "Photos" application:

![Photos resize dialog](https://github.com/mikeduglas/trackbar/blob/master/screenshots/Photos_Resize.jpg?raw=true)  

I decided to mimic this control in Clarion:

### Demo
You can see how new TrackBar control works running demo\Trackbar_demo.exe.

![Photos resize dialog](https://github.com/mikeduglas/trackbar/blob/master/screenshots/trackbar_demo.png?raw=true)  

The code is quite primitive:

```
  PROGRAM
  INCLUDE('trackbar.inc'), ONCE
  MAP
    INCLUDE('printf.inc'), ONCE
  END

Window                        WINDOW('Trackbar demo'),AT(,,260,100),CENTER,GRAY,SYSTEM,FONT('Segoe UI',9)
                                REGION,AT(16,26,186,22),USE(?rgnQuality)
                                PROMPT('Prompt1'),AT(16,14),USE(?lblQuality)
                                BUTTON('Close'),AT(197,76,47),USE(?btnClose),STD(STD:Close)
                              END

tbQuality                     CLASS(TTrackBar)
OnNewSelection                  PROCEDURE(), DERIVED, PROTECTED
                              END
  CODE
  OPEN(Window)
  
  tbQuality.Init(?rgnQuality)
  tbQuality.SetRange(10, 100)
  tbQuality.SetValue(50)
  
  ACCEPT
  END
  
tbQuality.OnNewSelection      PROCEDURE()
sQuality                        STRING(6), AUTO
  CODE
  IF SELF.curValue < 50
    sQuality = 'Low'
  ELSIF SELF.curValue < 80
    sQuality = 'Medium'
  ELSE
    sQuality = 'High'
  END
  ?lblQuality{PROP:Text} = printf('Quality: %i%% (%s)', SELF.curValue, sQuality)
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
- 106 USD via https://solar-staff.com)
