# creadit-card-validator
Author - shreyas Gujarathi
#include <iostream>
#include <string>
using namespace std;

// Function to check if a given card number is valid using the Luhn algorithm
bool isValidCard(const string& cardNumber) {
    int sum = 0;
    bool alternate = false;

    // Traverse the card number from right to left
    for (int i = cardNumber.length() - 1; i >= 0; i--) {
        int digit = cardNumber[i] - '0'; // Convert character to integer

        if (alternate) {
            digit *= 2; // Double every second digit
            if (digit > 9) {
                digit -= 9; // Subtract 9 if the result is greater than 9
            }
        }
        sum += digit;
        alternate = !alternate; // Alternate the flag
    }

    // If the total sum is a multiple of 10, the card number is valid
    return (sum % 10 == 0);
}

int main() {
    string cardNumber;
    cout << "Enter the credit card number: ";
    cin >> cardNumber;

    // Validate the card number
    if (isValidCard(cardNumber)) {
        cout << "The credit card number is valid." << endl;
    } else {
        cout << "The credit card number is invalid." << endl;
    }

    return 0;
}
