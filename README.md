import tkinter as tk
import random

# Initialize main window
root = tk.Tk()
root.title("Rock Paper Scissors")
root.geometry("400x400")
root.resizable(False, False)

# Game variables
player_score = 0
computer_score = 0
choices = ["Rock", "Paper", "Scissors"]

# Functions
def play(player_choice):
    global player_score, computer_score

    computer_choice = random.choice(choices)
    result = ""

    if player_choice == computer_choice:
        result = "It's a Tie!"
    elif (
        (player_choice == "Rock" and computer_choice == "Scissors") or
        (player_choice == "Paper" and computer_choice == "Rock") or
        (player_choice == "Scissors" and computer_choice == "Paper")
    ):
        result = "You Win!"
        player_score += 1
    else:
        result = "Computer Wins!"
        computer_score += 1

    # Update labels
    player_choice_label.config(text=f"Your Choice: {player_choice}")
    computer_choice_label.config(text=f"Computer's Choice: {computer_choice}")
    result_label.config(text=f"Result: {result}")
    score_label.config(text=f"Score - You: {player_score} | Computer: {computer_score}")

# Widgets
tk.Label(root, text="Rock Paper Scissors", font=("Arial", 18, "bold")).pack(pady=20)

# Choice buttons
button_frame = tk.Frame(root)
button_frame.pack()

for choice in choices:
    tk.Button(button_frame, text=choice, font=("Arial", 14), width=10,
              command=lambda c=choice: play(c)).pack(side="left", padx=10)

# Labels for results
player_choice_label = tk.Label(root, text="Your Choice: ", font=("Arial", 12))
player_choice_label.pack(pady=10)

computer_choice_label = tk.Label(root, text="Computer's Choice: ", font=("Arial", 12))
computer_choice_label.pack(pady=10)

result_label = tk.Label(root, text="Result: ", font=("Arial", 14, "bold"))
result_label.pack(pady=10)

score_label = tk.Label(root, text="Score - You: 0 | Computer: 0", font=("Arial", 12))
score_label.pack(pady=10)

# Run the GUI loop
root.mainloop()
