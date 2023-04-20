from tkinter import *
from tkinter import filedialog

root = Tk()
root.geometry("1000x600")
root.title("notepad")
root.config(bg="lightblue")
root.resizable(False,False)

def saveFile():
    openFile = filedialog.asksaveasfile(mode = "w", defaultextension= ".txt")
    if openFile is None:
        return
    text = str(entry.get(1.0,END))
    openFile.write(text)
    openFile.close()

def openFile():
    file = filedialog.askopenfile(mode="r", filetypes=[('text files','*.txt')])
    if file is not None:
        content = file.read()
    entry.insert(INSERT,content)

saveBtn = Button(root, width="20", height="2", bg="#fff", text="Save File", command=saveFile).place(x = 300, y = 5)
openBtn = Button(root, width="20", height="2", bg="#fff", text="Open File", command=openFile).place(x = 600, y = 5)

entry = Text(root, height="33", width="122", wrap=WORD)
entry.place(x=10, y=60)

root.mainloop()