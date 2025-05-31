# banking_system
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
    string name;
    int accountNumber;
    float balance;

    static constexpr float FDR_RATE = 0.07f;
    static constexpr float DPS_RATE = 0.05f;

public:
    BankAccount(string n = "", int acc = 0, float bal = 0.0f)
        : name(n), accountNumber(acc), balance(bal) {}

    void createAccount(string n, int acc, float initialDeposit) {
        name = n;
        accountNumber = acc;
        balance = initialDeposit;
        cout << "Account created for " << name << " with Account Number: " << accountNumber << endl;
    }

    void deposit(float amount) {
        balance += amount;
        cout << "Deposited " << amount << ". New Balance: " << balance << endl;
    }

    void withdraw(float amount) {
        if (amount > balance) {
            cout << "Insufficient balance!" << endl;
        } else {
            balance -= amount;
            cout << "Withdrew " << amount << ". New Balance: " << balance << endl;
        }
    }

    void fdr(float amount, int years) {
        float interest = amount * FDR_RATE * years;
        cout << "FDR Interest for " << years << " years: " << interest << endl;
    }

    void dps(float monthlyDeposit, int months) {
        float interest = monthlyDeposit * months * DPS_RATE;
        cout << "DPS Interest for " << months << " months: " << interest << endl;
    }

    void show() const {
        cout << "Name: " << name << ", Account No: " << accountNumber
             << ", Balance: " << balance << endl;
    }
};


int main() {
    BankAccount users[10];


    for (int i = 0; i < 10; ++i) {
        users[i].createAccount("User" + to_string(i + 1), 1000 + i, 1000.0f);
    }

    cout << "\n Performing Transactions \n";
    users[0].deposit(500);
    users[0].withdraw(300);
    users[0].fdr(1000, 3);
    users[0].dps(100, 12);

    cout << "\n User Info \n";
    users[0].show();

    return 0;
}


