#This is am example which will so you how to create a GUI in with the healp of tkinter
###Everin travels****
from tkinter import *
import tkinter.messagebox as tmsg
root = Tk()
#Enintial
root.geometry("1300x570")
root.title("By  Naman kashyap")
#Mainmenu , submenu and function
def help():
    print("I will help you")
    tmsg.showinfo("Help", " Try to contact 'Naman kashyap '")
def rate():
    print("Rate us")
    value = tmsg.askquestion("Was your experience Good?", "You used this gui.. Was your experience Good?")
    if value == "yes":
        msg = "Great. Rate us on appstore please"
    else:
        msg = "Tell us what went wrong. We will call you soon"
    tmsg.showinfo("Experience", msg)
mainmenu = Menu(root)
submenu1 = Menu(mainmenu, tearoff=0)
submenu1.add_command(label = "Help", command=help)
submenu1.add_command(label = "Rate us", command=rate)
mainmenu.add_cascade(label="Help", menu=submenu1)
submenu2 = Menu(mainmenu, tearoff=0)
submenu2.add_command(label = "Exit", command=quit)
mainmenu.add_cascade(label="Exit", menu=submenu2)
root.config(menu=mainmenu)
#Heading
Label(root, text="Everin Travels", font="comicsansms 13 bold", pady=15).grid(row=0, column=3)
#Text and its packing
Label(root, text="Name").grid(row=1, column=2)
Label(root, text="Phone").grid(row=2, column=2)
Label(root, text="Gender").grid(row=3, column=2)
Label(root, text="Emergency Contact").grid(row=4, column=2)
Label(root, text="Payment Mode").grid(row=5, column=2)
# Tkinter variable for storing entries
namevalue = StringVar()
phonevalue = StringVar()
gendervalue = StringVar()
emergencyvalue = StringVar()
paymentmodevalue = StringVar()
foodservicevalue = IntVar()
#Entries and their packing for our form
nameentry = Entry(root, textvariable=namevalue).grid(row=1, column=3)
phoneentry = Entry(root, textvariable=phonevalue).grid(row=2, column=3)
genderentry = Entry(root, textvariable=gendervalue).grid(row=3, column=3)
emergencyentry = Entry(root, textvariable=emergencyvalue).grid(row=4, column=3)
paymentmodeentry = Entry(root, textvariable=paymentmodevalue).grid(row=5, column=3)
#Checkbox & Packing it
Checkbutton(text="Want to prebook your meals?", variable = foodservicevalue).grid(row=6, column=3)
#Button & packing it and assigning it a command
def data_saving():
    with open("records.txt", "a") as f:
        f.write(f"{namevalue.get(), phonevalue.get(), gendervalue.get(), emergencyvalue.get(), paymentmodevalue.get(), foodservicevalue.get()}\n ")
Button(text="Submit", command=data_saving).grid(row=11, column=3)
root.mainloop()
