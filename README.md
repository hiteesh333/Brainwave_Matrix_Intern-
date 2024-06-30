# Brainwave_Matrix_Intern-
#include <iostream>
#include <string>
#include <unordered_map>

using namespace std;



class ATM {
private:
    unordered_map<string, pair<int, double>> accounts;
    
    
public:
    string language;
    ATM() {
        // Adding some dummy accounts
        accounts["John Doe"] = {1234, 5000.00};
        accounts["Jane Smith"] = {4321, 3000.00};
        accounts["Alice Brown"] = {5678, 1500.00};
        accounts["Bob White"] = {8765, 7000.00};
    }

    void setLanguage(int langChoice) {
        if (langChoice == 1) {
            language = "English";
        } else if (langChoice == 2) {
            language = "Hindi";
        } else if (langChoice == 3) {
            language = "Telugu";
        } else {
            language = "English";
        }
    }

    void showWelcomeMessage() {
        if (language == "English") {
            cout << "Welcome to the ATM!" << endl;
        } else if (language == "Hindi") {
            cout << "एटीएम में आपका स्वागत है!" << endl;
        } else if (language == "Telugu") {
            cout << "ఏటిఎం కి స్వాగతం!" << endl;
        }
    }

    void showMenu() {
        if (language == "English") {
            cout << "\nMain Menu:" << endl;
            cout << "1. Check Balance" << endl;
            cout << "2. Deposit" << endl;
            cout << "3. Withdraw Cash" << endl;
            cout << "4. Transfer Funds" << endl;
            cout << "5. Change PIN" << endl;
            cout << "6. Exit" << endl;
            cout << "Enter your choice (1-6): ";
        } else if (language == "Hindi") {
            cout << "\nमुख्य मेनू:" << endl;
            cout << "1. शेष राशि जांचें" << endl;
            cout << "2. जमा करें" << endl;
            cout << "3. नकद निकालें" << endl;
            cout << "4. धनराशि स्थानांतरित करें" << endl;
            cout << "5. पिन बदलें" << endl;
            cout << "6. बाहर जाएं" << endl;
            cout << "अपना चयन दर्ज करें (1-6): ";
        } else if (language == "Telugu") {
            cout << "\nప్రధాన మెను:" << endl;
            cout << "1. బ్యాలెన్స్ తనిఖీ చేయండి" << endl;
            cout << "2. డిపాజిట్ చేయండి" << endl;
            cout << "3. నగదు తీసుకోండి" << endl;
            cout << "4. నిధులు బదిలీ చేయండి" << endl;
            cout << "5. పిన్ మార్చండి" << endl;
            cout << "6. ఎగ్జిట్ చేయండి" << endl;
            cout << "మీ ఎంపికను నమోదు చేయండి (1-6): ";
        }
    }

    bool authenticate(const string& name, int pin) {
        if (accounts.find(name) != accounts.end() && accounts[name].first == pin) {
            return true;
        }
        return false;
    }

    void showBalance(const string& name) {
        if (language == "English") {
            cout << "Your balance is: $" << accounts[name].second << endl;
        } else if (language == "Hindi") {
            cout << "आपकी शेष राशि है: $" << accounts[name].second << endl;
        } else if (language == "Telugu") {
            cout << "మీ బ్యాలెన్స్: $" << accounts[name].second << endl;
        }
    }

    void deposit(const string& name, double amount) {
        if (amount > 0) {
            accounts[name].second += amount;
            if (language == "English") {
                cout << "Deposit successful. New balance: $" << accounts[name].second << endl;
            } else if (language == "Hindi") {
                cout << "जमा सफल। नई शेष राशि: $" << accounts[name].second << endl;
            } else if (language == "Telugu") {
                cout << "డిపాజిట్ విజయవంతం. కొత్త బ్యాలెన్స్: $" << accounts[name].second << endl;
            }
        } else {
            if (language == "English") {
                cout << "Invalid deposit amount." << endl;
            } else if (language == "Hindi") {
                cout << "अमान्य जमा राशि।" << endl;
            } else if (language == "Telugu") {
                cout << "చెల్లని డిపాజిట్ మొత్తం." << endl;
            }
        }
    }

    void withdraw(const string& name, double amount) {
        if (amount <= accounts[name].second && amount > 0) {
            accounts[name].second -= amount;
            if (language == "English") {
                cout << "Withdrawal successful. New balance: $" << accounts[name].second << endl;
            } else if (language == "Hindi") {
                cout << "निकासी सफल। नई शेष राशि: $" << accounts[name].second << endl;
            } else if (language == "Telugu") {
                cout << "విత్‌డ్రాయల్ విజయవంతం. కొత్త బ్యాలెన్స్: $" << accounts[name].second << endl;
            }
        } else {
            if (language == "English") {
                cout << "Insufficient funds or invalid amount." << endl;
            } else if (language == "Hindi") {
                cout << "अपर्याप्त धन या अमान्य राशि।" << endl;
            } else if (language == "Telugu") {
                cout << "తగినంత నిధులు లేవు లేదా చెల్లని మొత్తం." << endl;
            }
        }
    }

    void transfer(const string& from, const string& to, double amount) {
        if (accounts.find(to) != accounts.end()) {
            if (amount <= accounts[from].second && amount > 0) {
                accounts[from].second -= amount;
                accounts[to].second += amount;
                if (language == "English") {
                    cout << "Transfer successful. New balance of " << from << ": $" << accounts[from].second << endl;
                } else if (language == "Hindi") {
                    cout << "स्थानांतरण सफल। " << from << " की नई शेष राशि: $" << accounts[from].second << endl;
                } else if (language == "Telugu") {
                    cout << "బదిలీ విజయవంతం. " << from << " యొక్క కొత్త బ్యాలెన్స్: $" << accounts[from].second << endl;
                }
            } else {
                if (language == "English") {
                    cout << "Insufficient funds or invalid amount." << endl;
                } else if (language == "Hindi") {
                    cout << "अपर्याप्त धन या अमान्य राशि।" << endl;
                } else if (language == "Telugu") {
                    cout << "తగినంత నిధులు లేవు లేదా చెల్లని మొత్తం." << endl;
                }
            }
        } else {
            if (language == "English") {
                cout << "Recipient account does not exist." << endl;
            } else if (language == "Hindi") {
                cout << "प्राप्तकर्ता खाता मौजूद नहीं है।" << endl;
            } else if (language == "Telugu") {
                cout << "అందరికీ ఖాతా లేదు." << endl;
            }
        }
    }

    void changePin(const string& name, int oldPin, int newPin) {
        if (accounts[name].first == oldPin) {
            accounts[name].first = newPin;
            if (language == "English") {
                cout << "PIN change successful." << endl;
            } else if (language == "Hindi") {
                cout << "पिन परिवर्तन सफल।" << endl;
            } else if (language == "Telugu") {
                cout << "పిన్ మార్పు విజయవంతం." << endl;
            }
        } else {
            if (language == "English") {
                cout << "Old PIN is incorrect." << endl;
            } else if (language == "Hindi") {
                cout << "पुराना पिन गलत है।" << endl;
            } else if (language == "Telugu") {
                cout << "పాత పిన్ తప్పు." << endl;
            }
        }
    }
};

int main() {
    ATM atm;

    int langChoice;
    cout << "Please select your language / कृपया अपनी भाषा चुनें / దయచేసి మీ భాషను ఎంచుకోండి:" << endl;
    cout << "1. English" << endl;
    cout << "2. Hindi" << endl;
    cout << "3. Telugu" << endl;
    cout << "Enter your choice (1-3): ";
    cin >> langChoice;
    atm.setLanguage(langChoice);
    cin.ignore(); // Clear the input buffer

    atm.showWelcomeMessage();

    string name;
    int pin;

    if (atm.language == "English") {
        cout << "Enter your username: ";
    } else if (atm.language == "Hindi") {
        cout << "अपना उपयोगकर्ता नाम दर्ज करें: ";
    } else if (atm.language == "Telugu") {
        cout << "మీ వినియోగదారు పేరును నమోదు చేయండి: ";
    }
    getline(cin, name);

    if (atm.language == "English") {
        cout << "Enter your PIN: ";
    } else if (atm.language == "Hindi") {
        cout << "अपना पिन दर्ज करें: ";
    } else if (atm.language == "Telugu") {
        cout << "మీ పిన్ నమోదు చేయండి: ";
    }
    cin >> pin;

    if (atm.authenticate(name, pin)) {
        bool exit = false;
        while (!exit) {
            atm.showMenu();
            int choice;
            cin >> choice;

            switch (choice) {
                case 1:
                    atm.showBalance(name);
                    break;
                case 2: {
                    double amount;
                    if (atm.language == "English") {
                        cout << "Enter the amount to deposit: ";
                    } else if (atm.language == "Hindi") {
                        cout << "जमा करने के लिए राशि दर्ज करें: ";
                    } else if (atm.language == "Telugu") {
                        cout << "డిపాజిట్ చేయవలసిన మొత్తం నమోదు చేయండి: ";
                    }
                    cin >> amount;
                    atm.deposit(name, amount);
                    break;
                }
                case 3: {
                    double amount;
                    if (atm.language == "English") {
                        cout << "Enter the amount to withdraw: ";
                    } else if (atm.language == "Hindi") {
                        cout << "निकालने की राशि दर्ज करें: ";
                    } else if (atm.language == "Telugu") {
                        cout << "తీసుకోవలసిన మొత్తాన్ని నమోదు చేయండి: ";
                    }
                    cin >> amount;
                    atm.withdraw(name, amount);
                    break;
                }
                case 4: {
                    string to;
                    double amount;
                    if (atm.language == "English") {
                        cout << "Enter the recipient's username: ";
                    } else if (atm.language == "Hindi") {
                        cout << "प्राप्तकर्ता का उपयोगकर्ता नाम दर्ज करें: ";
                    } else if (atm.language == "Telugu") {
                        cout << "అందరి వినియోగదారు పేరును నమోదు చేయండి: ";
                    }
                    cin.ignore();  // To ignore the newline character left by cin
                    getline(cin, to);
                    if (atm.language == "English") {
                        cout << "Enter the amount to transfer: ";
                    } else if (atm.language == "Hindi") {
                        cout << "स्थानांतरण करने की राशि दर्ज करें: ";
                    } else if (atm.language == "Telugu") {
                        cout << "బదిలీ చేయవలసిన మొత్తాన్ని నమోదు చేయండి: ";
                    }
                    cin >> amount;
                    atm.transfer(name, to, amount);
                    break;
                }
                case 5: {
                    int oldPin, newPin;
                    if (atm.language == "English") {
                        cout << "Enter your current PIN: ";
                    } else if (atm.language == "Hindi") {
                        cout << "अपना वर्तमान पिन दर्ज करें: ";
                    } else if (atm.language == "Telugu") {
                        cout << "మీ ప్రస్తుత పిన్ నమోదు చేయండి: ";
                    }
                    cin >> oldPin;
                    if (atm.language == "English") {
                        cout << "Enter your new PIN: ";
                    } else if (atm.language == "Hindi") {
                        cout << "अपना नया पिन दर्ज करें: ";
                    } else if (atm.language == "Telugu") {
                        cout << "మీ కొత్త పిన్ నమోదు చేయండి: ";
                    }
                    cin >> newPin;
                    atm.changePin(name, oldPin, newPin);
                    break;
                }
                case 6:
                    if (atm.language == "English") {
                        cout << "Thank you for using the ATM. Goodbye!" << endl;
                    } else if (atm.language == "Hindi") {
                        cout << "एटीएम का उपयोग करने के लिए धन्यवाद। अलविदा!" << endl;
                    } else if (atm.language == "Telugu") {
                        cout << "ఏటిఎం ఉపయోగించినందుకు ధన్యవాదాలు. వీడ్కోలు!" << endl;
                    }
                    exit = true;
                    break;
                default:
                    if (atm.language == "English") {
                        cout << "Invalid choice. Please try again." << endl;
                    } else if (atm.language == "Hindi") {
                        cout << "अमान्य विकल्प। कृपया पुन: प्रयास करें।" << endl;
                    } else if (atm.language == "Telugu") {
                        cout << "చెల్లని ఎంపిక. దయచేసి మళ్లీ ప్రయత్నించండి." << endl;
                    }
            }
        }
    } else {
        if (atm.language == "English") {
            cout << "Authentication failed. Please try again." << endl;
        } else if (atm.language == "Hindi") {
            cout << "प्रमाणीकरण विफल। कृपया पुन: प्रयास करें।" << endl;
        } else if (atm.language == "Telugu") {
            cout << "ప్రామాణీకరణ విఫలమైంది. దయచేసి మళ్లీ ప్రయత్నించండి." << endl;
        }
    }

    return 0;
}
