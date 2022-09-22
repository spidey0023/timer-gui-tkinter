from importlib.metadata import EntryPoint
import time
from tkinter import  *
from tkinter import messagebox

# interface
clockwindow=Tk()
clockwindow.geometry("600x600")
clockwindow.title("Countdown Timer")
clockwindow.configure(background='orange')

hourstring=StringVar()
minutestring=StringVar()
secondstring=StringVar()

#srtings to intial value
hourstring.set("00")
minutestring.set("00")
secondstring.set("00")

#userinput
hourtextbox= Entry(clockwindow, width=3 , font=("calibri",20,'') ,textvariable=hourstring)
minutetextbox= Entry(clockwindow, width=3 , font=("calibri",20,'') ,textvariable=minutestring)
secondtextbox= Entry(clockwindow, width=3 , font=("calibri",20,'') ,textvariable=secondstring) 

#centre textbox
hourtextbox.place(x=170,y=180 )
minutetextbox.place(x=220,y=180)
secondtextbox.place(x=270,y=180)

#timer
def runtimer():
    try:
        clocktime=int(hourstring.get())*3600 +int(minutestring.get())*60 +int(secondstring.get())
    except:
        print("Incorrect valus")

    while(clocktime>-1):
        minutes,seconds=divmod(clocktime,60)

        hours=0
        if(minutes>60):
            hours,minutes=divmod(minutes,60)
        
        hourstring.set("{:02d}".format(hours))
        minutestring.set("{:02d}".format(minutes))
        secondstring.set("{:02d}".format(seconds))

        #interface
        clockwindow.update()
        time.sleep(1)

        #expired timer
        if (clocktime==0):
            messagebox.showinfo("","your time has expired!!")
        
        clocktime -=1
    
settimebutton=Button(clockwindow,text='set Time',bd='5',command=runtimer)
settimebutton.place(relx=0.5,rely=0.5,anchor=CENTER)

#keep looping
clockwindow.mainloop()


        








         
