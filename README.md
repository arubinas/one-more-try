# one-more-try
Have four items
import tkinter as tk
from tkinter import Menu
from datetime import datetime
import random

# Function to display date and time in text box
def show_datetime():
    current_datetime = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    text_box.delete("1.0", tk.END)
    text_box.insert(tk.END, current_datetime)

# Function to write text box contents to "log.txt"
def write_to_file():
    content = text_box.get("1.0", tk.END).strip()
    if content:
        with open("log.txt", "a") as file:
            file.write(content + '\n')

# Function to change the background color to a random green hue
def change_bg_color():
    hue = random.randint(85, 150)  # Green hues range
    color = f'#{hue:02x}ff{hue:02x}'  # Converting hue to a hex color
    root.config(bg=color)
    menu.entryconfig(3, label=f"Change Background Color (#{hue:02x}ff{hue:02x})")
    with open("log.txt", "a") as file:
        file.write(f"Changed background color to #{hue:02x}ff{hue:02x}\n")

# Function to clear the text box
def clear_text_box():
    text_box.delete("1.0", tk.END)

# Function to exit the program
def exit_program():
    root.quit()

# Create the main window
root = tk.Tk()
root.title("User Interface Example")

# Create a menu
menu = Menu(root)
root.config(menu=menu)

# Add menu items
menu.add_command(label="Show Date and Time", command=show_datetime)
menu.add_command(label="Write to File", command=write_to_file)
menu.add_command(label="Change Background Color", command=change_bg_color)
menu.add_command(label="Clear Text Box", command=clear_text_box)
menu.add_command(label="Exit", command=exit_program)

# Create a text box
text_box = tk.Text(root, height=10, width=50)
text_box.pack(pady=20)

# Start the main loop
root.mainloop()
