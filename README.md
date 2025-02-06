#include <iostream>
#include <vector>
#include <string>

class ProductDatabase {
private:
    std::vector<std::string> qrCodes;

public:
    void registerProduct(const std::string& qrCode) {
        qrCodes.push_back(qrCode);
        std::cout << "\n✅ Product Registered: " << qrCode << "\n";
    }

    bool verifyProduct(const std::string& qrCode) {
        for (const auto& code : qrCodes) {
            if (code == qrCode) {
                std::cout << "\n✅ Verified: Genuine Product\n";
                return true;
            }
        }
        std::cout << "\n❌ Fake Product Detected!\n";
        return false;
    }
};

int main() {
    ProductDatabase database;
    int choice;
    std::string qrCode;

    while (true) {
        std::cout << "\n1. Register Product\n2. Verify Product\n3. Exit\nChoose an option: ";
        std::cin >> choice;
        std::cin.ignore();

        if (choice == 1) {
            std::cout << "Enter QR Code: ";
            std::getline(std::cin, qrCode);
            database.registerProduct(qrCode);
        } 
        else if (choice == 2) {
            std::cout << "Enter QR Code to Verify: ";
            std::getline(std::cin, qrCode);
            database.verifyProduct(qrCode);
        } 
        else if (choice == 3) {
            std::cout << "\nExiting...\n";
            break;
        } 
        else {
            std::cout << "\nInvalid choice. Try again.\n";
        }
    }
    return 0;
}
