# Tile-Flipper-Stake-
import random
def create_grid(size, diamond_count): grid = [[0 for _ in range(size)] for _ in range(size)] 
diamonds_placed = 0 while diamonds_placed < diamond_count: row = random.randint(0, size -
1) col = random.randint(0, size - 1) if grid[row][col] == 0: grid[row][col] = 1 diamonds_placed += 
1 return grid
def display_grid(grid, revealed): for i in range(len(grid)): for j in range(len(grid[i])): if 
revealed[i][j]: print(" " if grid[i][j] == 1 else " ", end=" ") else: print("■", end=" ") print()
def play_game(): size = int(input("Enter grid size (e.g., 5 for a 5x5 grid): ")) diamond_count = 
int(input("Enter the number of diamonds to hide: "))
grid = create_grid(size, diamond_count)
revealed = [[False for _ in range(size)] for _ in range(size)]
streak = 0
while True:
 display_grid(grid, revealed)
 try:
 row = int(input("Enter row (0-based index): "))
 col = int(input("Enter column (0-based index): "))
 
 if revealed[row][col]:
 print("Tile already flipped! Try again.")
 continue
 revealed[row][col] = True
 if grid[row][col] == 1:
 print("You found a diamond! ")
 streak += 1
 else:
 print("No diamond here! Game Over.")
 print(f"Your streak: {streak}")
 break
 except (ValueError, IndexError):
 print("Invalid input. Please enter valid row and column numbers.")
replay = input("Do you want to play again? (yes/no): ").strip().lower()
if replay == 'yes':
 play_game()
play_game()
