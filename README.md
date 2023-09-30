# TicTakToe-

def print_board(board):
    for row in board:
        print(" | ".join(row))
        print("-" * 9)

def check_winner(board, player):
    for row in board:
        if all(cell == player for cell in row):
            return True

    for col in range(3):
        if all(board[row][col] == player for row in range(3)):
            return True

    if all(board[i][i] == player for i in range(3)) or all(board[i][2 - i] == player for i in range(3)):
        return True

    return False

def is_board_full(board):
    return all(cell != " " for row in board for cell in row)

def main():
    board = [[" " for _ in range(3)] for _ in range(3)]
    player = "X"
    winner = None

    while True:
        print_board(board)

        if winner:
            print(f"Player {winner} wins!")
            break
        elif is_board_full(board):
            print("It's a tie!")
            break

        row = int(input(f"Player {player}, enter row (0, 1, or 2): "))
        col = int(input(f"Player {player}, enter column (0, 1, or 2): "))

        if board[row][col] == " ":
            board[row][col] = player
            if check_winner(board, player):
                winner = player
            player = "X" if player == "O" else "O"
        else:
            print("That cell is already occupied. Try again.")

if __name__ == "__main__":
    main()


