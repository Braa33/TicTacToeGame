
import tkinter as tk
from tkinter import messagebox

class TicTacToe:
    def __init__(self):
        self.current_player = "X"
        self.board = [[" " for _ in range(3)] for _ in range(3)]
        self.root = tk.Tk()
        self.root.title("Tic Tac Toe")
        self.create_board()
        self.root.mainloop()

    def create_board(self):
        for i in range(3):
            for j in range(3):
                button = tk.Button(self.root, text=" ", font=("Arial", 50), bg="#EEE", command=lambda row=i, col=j: self.play(row, col))
                button.grid(row=i, column=j, sticky="nsew")
                self.board[i][j] = button

    def play(self, row, col):
        button = self.board[row][col]
        if button["text"] == " ":
            button["text"] = self.current_player
            button["bg"] = "#DDD"
            self.check_winner()
            self.current_player = "O" if self.current_player == "X" else "X"
        else:
            messagebox.showerror("Error", "That cell is already taken!")

    def check_winner(self):
        for i in range(3):
            if self.board[i][0]["text"] == self.board[i][1]["text"] == self.board[i][2]["text"] != " ":
                self.declare_winner(self.board[i][0]["text"])
            if self.board[0][i]["text"] == self.board[1][i]["text"] == self.board[2][i]["text"] != " ":
                self.declare_winner(self.board[0][i]["text"])
        if self.board[0][0]["text"] == self.board[1][1]["text"] == self.board[2][2]["text"] != " ":
            self.declare_winner(self.board[0][0]["text"])
        if self.board[0][2]["text"] == self.board[1][1]["text"] == self.board[2][0]["text"] != " ":
            self.declare_winner(self.board[0][2]["text"])
        if all(button["text"] != " " for row in self.board for button in row):
            self.declare_tie()

    def declare_winner(self, winner):
        for i in range(3):
            for j in range(3):
                self.board[i][j]["state"] = "disabled"
        choice = messagebox.askquestion("Winner", f"{winner} wins! Do you want to play again?")
        if choice == "yes":
            self.reset_board()
        else:
            self.root.destroy()

    def declare_tie(self):
        for i in range(3):
            for j in range(3):
                self.board[i][j]["state"] = "disabled"
        choice = messagebox.askquestion("Tie", "It's a tie! Do you want to play again?")
        if choice == "yes":
            self.reset_board()
        else:
            self.root.destroy()

    def reset_board(self):
        for i in range(3):
            for j in range(3):
                self.board[i][j]["text"] = " "
                self.board[i][j]["bg"] = "#EEE"
                self.board[i][j]["state"] = "normal"
        self.current_player = "X"

if __name__ == "__main__":
    TicTacToe()
