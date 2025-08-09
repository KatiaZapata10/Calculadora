import tkinter as tk

from tkinter.ttk import Entry

def click(btn):
    if btn == "=":
        try:
            res = str(eval(entry.get())) 
            entry.delete(0, tk.END) 
            entry.insert(tk.END, res) 
        except:
            entry.delete(0, tk.END)
            entry.insert(tk.END, "Error")
    elif btn == "C":
        entry.delete(0, tk.END)
    else:    
        entry.insert(tk.END, btn)

root = tk.Tk()
root.title("Calculadora")

entry = Entry(root, width=20, font=(None, 20),justify="right")
entry.grid(row=0, column=0, columnspan=4)

buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    '0', '.', '=', '+',
    'C'
]
row, col = 1, 0
for b in buttons:
    if b in ('=', 'C'):
        bg_color = "blue" if b == 'C' else "pinck"
        fg_color = "black"
    else:
        bg_color ="grey"
        fg_color ="white"     
    tk.Button(root, text=b, width=5, height=2, font=(None, 16),
              command=lambda x=b: click(x)).grid(row=row, column=col)
    col += 1
    if col > 3:
        col = 0
        row += 1

root.mainloop()
