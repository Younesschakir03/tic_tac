import tkinter as tk
from tkinter import messagebox

class TicTacToe:
    def __init__(self, master):
        self.master = master
        self.master.title('Tic Tac Toe')
        self.master.geometry('402x450')
        self.master.configure(bg='#f0f0f0')
        
        # Create button grid
        self.buttons = [[None for _ in range(3)] for _ in range(3)]
        for i in range(3):
            for j in range(3):
                button = tk.Button(self.master, text=' ', font=('Arial', 30), width=5, height=2,
                                   command=lambda i=i, j=j: self.take_turn(i, j))
                button.grid(row=i, column=j, padx=5, pady=5)
                self.buttons[i][j] = button
        
        # Create game state variables
        self.turn = 'X'
        self.board = [[' ' for _ in range(3)] for _ in range(3)]
        self.game_over = False
        
        # Create restart button
        restart_button = tk.Button(self.master, text='Start Over', font=('Arial', 14), command=self.restart_game)
        restart_button.grid(row=3, column=0, columnspan=3, pady=10)
        
    def take_turn(self, i, j):
        if not self.game_over and self.buttons[i][j]['text'] == ' ':
            self.buttons[i][j]['text'] = self.turn
            self.board[i][j] = self.turn
            
            # Check for win condition
            if self.check_win():
                self.highlight_winning_cells()
                messagebox.showinfo('Winner!', f'{self.turn} wins!')
                self.game_over = True
            # Check for tie condition
            elif self.check_tie():
                messagebox.showinfo('Tie!', 'The game is tied!')
                self.game_over = True
            # Switch turns
            else:
                self.turn = 'O' if self.turn == 'X' else 'X'
    
    def check_win(self):
        # Check rows
        for row in self.board:
            if row[0] == row[1] == row[2] != ' ':
                return True
        # Check columns
        for j in range(3):
            if self.board[0][j] == self.board[1][j] == self.board[2][j] != ' ':
                return True
        # Check diagonals
        if self.board[0][0] == self.board[1][1] == self.board[2][2] != ' ':
            return True
        if self.board[0][2] == self.board[1][1] == self.board[2][0] != ' ':
            return True
        return False
    
    def check_tie(self):
        for row in self.board:
            for cell in row:
                if cell == ' ':
                    return False
        return True
    
    def highlight_winning_cells(self):
        # Highlight winning row
        for i in range(3):
            if self.board[i][0] == self.board[i][1] == self.board[i][2] != ' ':
                for j in range(3):
                    self.buttons[i][j].configure(bg='#ffee58')
                return
        
        # Highlight winning column
        for j in range(3):
            if self.board[0][j] == self.board[1][j] == self.board[2][j] != ' ':
                for i in range(3):
                    self.buttons[i][j].configure(bg='#ffee58')
                return
        
        # Highlight winning diagonal
        if self.board[0][0] == self.board[1][1] == self.board[2][2] != ' ':
            for i in range(3):
                self.buttons[i][i].configure(bg='#ffee58')
            return
        
        # Highlight winning diagonal
        if self.board[0][2] == self.board[1][1] == self.board[2][0] != ' ':
            for i in range(3):
                self.buttons[i][2-i].configure(bg='#ffee58')
            return
    
    def restart_game(self):
        # Reset game state variables
        self.turn = 'X'
        self.board = [[' ' for _ in range(3)] for _ in range(3)]
        self.game_over = False
        
        # Reset button text and color
        for i in range(3):
            for j in range(3):
                self.buttons[i][j]['text'] =' '
                self.buttons[i][j].configure(bg='white')
                
# Create main window
root = tk.Tk()

# Create Tic Tac Toe game
game = TicTacToe(root)

# Run main loop
root.mainloop()
