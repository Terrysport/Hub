#cs---------------------------------------------------

AutoIt Version :v3.3.14.2

Author: TerryLin

Script Function:

Template AutoIt script.

For Dior Test Case #HDD/SSD - Stress PassMark BurnIn Test

#ce----------------------------------------------------

; Script Start - Add you code below here

#RequireAdmin;Run with Admin for below script.

If MsgBox(1,"warning","Please close all of application and wait memont")=1 Then
send("#r")
BlockInput(1);Block mouse/keyboard input
send("diskpart{enter}")
WinWaitActive("C:\Windows\system32\diskpart.exe","diskpart",2)
send("list volume{enter}")
send("select volume 1{enter}");if the primary HDD is 1,select vo1ume
send("shrink desired=20000{enter}");test case is 200GB NFTS,but demo only 20GB
sleep(5000)
send("creat partition primary{enter}")
send("format fs=ntfs label=Test_1 quick{enter}")
sleep(5000)
send("assign letter=e:{enter}");if it has same HDD name ,it must be change name,e.g:f,g,h....
sleep(3000)
BlockInput(0);open mouse/keyboard input
send("!{tab}")
BlockInput(1);Block mouse/keyboard input
WinWaitActive("C:\Windows\system32\diskpart.exe","diskpart",2)
send("shrink desired=5000{enter}");test case is 20GB ,but demo only 5GB
sleep(5000)
send("creat partition primary{enter}")
send("format fs=FAT32 label=Test_2 quick{enter}")
sleep(5000)
send("assign letter=f:{enter}");if it has same HDD name ,it must be change name,e.g:f,g,h....
sleep(2000)
Send("#{PRINTSCREEN}")
sleep(2000)
BlockInput(0)
send("!{tab}")
sleep(2000)
send("list volume{enter}")
EndIf

sleep(1000)
If MsgBox(1,"warning","Please close all of application and waitting memont")=1 Then
Run("bitpro.exe");install burning test tool
WinWaitActive("Setup - BurnInTest")
Send("!n")
WinWaitActive("Setup - BurnInTest")
Send("!a")
WinWaitActive("Setup - BurnInTest")
Send("!n")
WinWaitActive("Setup - BurnInTest")
Send("!n")
WinWaitActive("Setup - BurnInTest")
Send("!n")
WinWaitActive("Setup - BurnInTest","Type the name of a program" , 1)
Send("!i")
WinWaitActive("Exit Setup","Type the name of a program" , 1)
Send("n")
WinWaitActive("Setup - BurnInTest","Type the name of a program" , 1)
Send("n")
WinWaitActive("Click Finish to exit Setup.","Type the name of a program" , 3)
Send("!f")


WinWaitActive("BurnInTest by PassMark Software", "Type the name of a program" , 8)
Send("{Tab}")
Send("{Tab}")
Send("{Tab}")
Send("{Tab}")
send("PEGATRON Corporation")
Send("{enter}")
Send("{#}ANDSCJIBJX7FYBZ996T9XFAXUSAATJP9XCST9CUZNVD3CAH53FJYGVT88FV5XWKZF972UBWKQB5DR9X8XEF8EE857PZPP4TX5JIMC5MG6GMIUBTCHP699EN8")
Send("{Tab}")
Send("{enter}")
WinWaitActive("Thanks","Type the name of a program" , 1)
Send("{enter}")


WinWaitActive("BurnInTest V7.1 Pro", "Type the name of a program" ,5 )
Send("{alt}")
Send("c")
Send("t")
WinWaitActive("Test selection and duty cycles", "Type the name of a program" , 3)
Send("5")
WinWaitActive("Test selection and duty cycles", "Type the name of a program" , 3)
Controlclick("Test selection and duty cycles","Optical Drive(s)","[CLASS:Button; INSTANCE:3]")
WinWaitActive("Test selection and duty cycles", "Type the name of a program" , 2)
Controlclick("Test selection and duty cycles","Video","[CLASS:Button; INSTANCE:13]")
Send("{enter}")

WinWaitActive("BurnInTest V7.1 Pro", "Type the name of a program" , 3)
Send("{alt}")
Send("t")
Send("s")

WinWaitActive("Getting ready to run Burn in tests", "Type the name of a program" , 3)
Send("{enter}")

Sleep(360000)
WinWaitActive("BurnInTest test result", "Type the name of a program" , 3)
Send("#{PRINTSCREEN}")
WinWaitActive("BurnInTest test result", "Type the name of a program" , 1)
Send("{Enter}")

WinWaitActive("BurnInTest V7.1 Pro", "Type the name of a program" ,5 )
Send("{alt}")
Send("c")
Send("t")
WinWaitActive("Test selection and duty cycles", "Type the name of a program" , 3)
Send("720")
WinWaitActive("Test selection and duty cycles", "Type the name of a program" , 1)
Send("{Enter}")
WinWaitActive("BurnInTest V7.1 Pro", "Type the name of a program" , 3)
Send("{alt}")
Send("t")
Send("s")
WinWaitActive("Getting ready to run Burn in tests", "Type the name of a program" , 3)
Send("{enter}")
Sleep(43300000);waitting for burning test done
WinWaitActive("BurnInTest test result", "Type the name of a program" , 3)
Send("#{PRINTSCREEN}");screencapure
WinWaitActive("BurnInTest test result", "Type the name of a program" , 1)
Send("{Enter}")
EndIf
