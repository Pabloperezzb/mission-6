# mission-6
// Pablo Perez-Bedmar Merello

#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand((unsigned)time(0));

    cout << "Welcome to the Most Dangerous Game!" << endl;

    // Generate a random space for the silver coin
    int silverCoinSpace = rand() % 12 + 1;
    cout << "The interrogator has placed the silver coin on space " << silverCoinSpace << "." << endl;

    int goldCoinSpace;

    // Ask the player to place the gold coin
    do {
        cout << "Enter the space where you want to place your gold coin (1-12): ";
        cin >> goldCoinSpace;
    } while (goldCoinSpace < 1 || goldCoinSpace > 12 || goldCoinSpace == silverCoinSpace);

    int tokenPosition = 0;

    while (true) {
        // Roll a fair six-sided die
        int dieRoll = rand() % 6 + 1;

        // Move the token
        tokenPosition += dieRoll;

        // Check if the token has gone past space 12
        if (tokenPosition > 12) {
            tokenPosition = 0;
        }

        // Display the result of the die roll and the new location of the token
        cout << "You rolled a " << dieRoll << ", the token is now on space " << tokenPosition << "." << endl;

        // Check if the token has landed on a coin
        if (tokenPosition == silverCoinSpace) {
            cout << "Game over! The interrogator's silver coin was found. You lose." << endl;
            break;
        } else if (tokenPosition == goldCoinSpace) {
            cout << "Congratulations! You found your gold coin. You win!" << endl;
            break;
        }
    }

    return 0;
}

