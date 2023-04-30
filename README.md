# Trackbar control

### Overview


Windows application "Photos"

![Photos resize dialog](https://github.com/mikeduglas/trackbar/blob/master/screenshots/Photos_Resize.jpg?raw=true)  

### Code
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
  
  ?lblQuality{PROP:Text} = printf('Quality: %i%% (%s)', SELF.curValue, sQuality)```

### Demo project
![Photos resize dialog](https://github.com/mikeduglas/trackbar/blob/master/screenshots/trackbar_demo.png?raw=true)  

### Requirements
- Clarion versions: C6.3 and higher.
- Template chains: ABC, Clarion.
- Multi dll apps supported.
- [winapi](https://github.com/mikeduglas/winapi)
- [gdiplus](https://github.com/mikeduglas/gdiplus)
- [printf](https://github.com/mikeduglas/printf)

### Contacts
- <mikeduglas@yandex.ru>
- <mikeduglas66@gmail.com>

### Price
100 USD