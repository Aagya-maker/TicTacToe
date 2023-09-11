class TicTacToe:
    def __init__(self):
        self.board = [" "]*9
        self.player = "X"

    def move(self, pos):
        if self.board[pos] == " ":
            self.board[pos] = self.player
            self.player = "O" if self.player == "X" else "X"

    def winner(self):
        b, p = self.board, self.player
        if any(all(b[i] == p for i in line) for line in [(0, 1, 2), (3, 4, 5), (6, 7, 8), (0, 3, 6), (1, 4, 7), (2, 5, 8), (0, 4, 8), (2, 4, 6)]):
            return p
        return "Draw" if " " not in b else None

    def play(self):
        while not self.winner():
            print("\n".join([" | ".join(self.board[i:i+3]) for i in range(0, 9, 3)]))
            p = int(input(f"Player {self.player}, enter your move (0-8): "))
            if 0 <= p <= 8: self.move(p)
            else: print("Invalid move. Please try again.")
        print(f"Player {self.winner()} wins!" if self.winner() != "Draw" else "It's a draw!")

if __name__ == "__main__":
    TicTacToe().play()
