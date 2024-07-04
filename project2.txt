def get_secret_number():
    while True:
        secret_number = input("Player 1, enter the secret multi-digit number: ")
        if secret_number.isdigit():
            return secret_number
        else:
            print("Invalid input. Please enter a multi-digit number.")

def get_guess():
    while True:
        guess = input("Player 2, enter your guess: ")
        if guess.isdigit():
            return guess
        else:
            print("Invalid input. Please enter a multi-digit number.")

def provide_feedback(secret, guess):
    feedback = []
    for i in range(len(guess)):
        if guess[i] == secret[i]:
            feedback.append('Correct')
        elif guess[i] in secret:
            feedback.append('Wrong position')
        else:
            feedback.append('Wrong')
    return feedback

def mastermind_game():
    print("Welcome to Mastermind Game!")
    
    # Player 1 sets the secret number
    secret_number = get_secret_number()
    
    # Player 2 attempts to guess
    attempts = 0
    while True:
        attempts += 1
        guess = get_guess()
        if guess == secret_number:
            print(f"Player 2 guessed the number in {attempts} attempts!")
            break
        else:
            feedback = provide_feedback(secret_number, guess)
            print("Feedback: ", feedback)
    
    # Now Player 2 sets the secret number for Player 1
    print("Now Player 2 sets the secret number.")
    secret_number = get_secret_number()
    
    # Player 1 attempts to guess
    attempts_player1 = 0
    while True:
        attempts_player1 += 1
        guess = get_guess()
        if guess == secret_number:
            print(f"Player 1 guessed the number in {attempts_player1} attempts!")
            break
        else:
            feedback = provide_feedback(secret_number, guess)
            print("Feedback: ", feedback)
    
    # Determine the winner
    if attempts_player1 < attempts:
        print("Player 1 wins the game and is crowned Mastermind!")
    else:
        print("Player 2 wins the game and is crowned Mastermind!")

if __name__ == "__main__":
    mastermind_game()
