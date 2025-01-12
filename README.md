the code:

from tkinter import *
import random
import clipboard

#funclist
def passgener():
    passlenght = passwordlenghtchooser.get()
    i = ""
    for z in range(1,passlenght+1):
        i += str(random.choice(setofthings))
    text.set(i)
    lenght.set(f"Password lenght:   {passlenght}")

def newpassgener():
    passlenght = passwordlenghtchooser.get()
    i = ""
    for z in range(1,passlenght+1):
        i += str(random.choice(setofthings))
    text.set(i)
def copying():
    clipboard.copy(text.get())

#############################################################
i = ""
setofthings = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!#$%&'()*+,-./:;<=>?@]^_`{|}~"""

root = Tk()

root.title("Password Generator")
root.resizable(False,False)
icon = PhotoImage(file="61457.png")
root.iconphoto(True,icon)




text = StringVar()
lenght = StringVar()

lenght.set(f"Password lenght:   1")
text.set(random.choice(setofthings))


###########################################################################
passwordlenghtchooser = Scale(root, showvalue=0,from_=1,to=35,orient=HORIZONTAL,length=300,command= lambda _: passgener())
passwordgeneration = Label(root, textvariable=text,font=("Arial Baltic",12,"bold"))
passlenghtinformer = Label(root, textvariable=lenght)
btngenerator = Button(root, text="Regenerate",command= lambda: newpassgener(),bd=3)
copytoclipboard = Button(root, text="Copy",bd=3,command=lambda:copying())

###########################################################################
passwordgeneration.grid(column=0,row=0,columnspan=3,stick="nsew")
passwordlenghtchooser.grid(column=1,row=1,stick="nsew")
passlenghtinformer.grid(column=0,row=1,stick="nsew")
btngenerator.grid(column=3,row=1,sticky="nsew")
copytoclipboard.grid(column=4,row=1,stick="nsew")

root.mainloop()
