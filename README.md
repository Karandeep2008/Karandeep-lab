# Karandeep-lab
Some python codes 
import tkinter as tk

class VisitorForm:
    def __init__(self, master):
        self.master = master
        master.title("WELCOME VISITORS")
        master.configure(background="#ADD8E6")  # light blue background

        # Heading
        self.heading_label = tk.Label(master, text="WELCOME VISITORS", font=("Arial", 24, "bold"), fg="black", bg="#ADD8E6")
        self.heading_label.pack(pady=20)

        # Name input
        self.name_label = tk.Label(master, text="Enter your name:", font=("Arial", 16), fg="black", bg="#ADD8E6")
        self.name_label.pack()
        self.name_entry = tk.Entry(master, font=("Arial", 16), width=30)
        self.name_entry.pack()

        # Purpose of visit input
        self.purpose_label = tk.Label(master, text="Enter your purpose of visit:", font=("Arial", 16), fg="black", bg="#ADD8E6")
        self.purpose_label.pack()
        self.purpose_entry = tk.Entry(master, font=("Arial", 16), width=30)
        self.purpose_entry.pack()

        # Exhibitions selection
        self.exhibitions_label = tk.Label(master, text="Select exhibitions to visit:", font=("Arial", 16), fg="black", bg="#ADD8E6")
        self.exhibitions_label.pack()
        self.exhibitions_frame = tk.Frame(master, bg="#ADD8E6")
        self.exhibitions_frame.pack()
        self.volcano_var = tk.IntVar()
        self.water_filter_var = tk.IntVar()
        self.rocket_var = tk.IntVar()
        self.magic_mirror_var = tk.IntVar()
        self.exhibitions = [
            ("Volcano", self.volcano_var),
            ("Water Filter", self.water_filter_var),
            ("Rocket", self.rocket_var),
            ("Magic Mirror", self.magic_mirror_var),
        ]
        for text, var in self.exhibitions:
            tk.Checkbutton(self.exhibitions_frame, text=text, variable=var, font=("Arial", 14), fg="black", bg="#ADD8E6").pack(side=tk.LEFT)

        # Submit button
        self.submit_button = tk.Button(master, text="Submit", font=("Arial", 16), fg="black", bg="#FFC080", command=self.submit_form)
        self.submit_button.pack(pady=20)

    def submit_form(self):
        name = self.name_entry.get()
        purpose = self.purpose_entry.get()
        exhibitions = [text for text, var in self.exhibitions if var.get()]
        print(f"Name: {name}, Purpose: {purpose}, Exhibitions: {', '.join(exhibitions)}")

root = tk.Tk()
my_form = VisitorForm(root)
root.mainloop()
