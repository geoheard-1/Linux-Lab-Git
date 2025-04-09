#include <iostream>
 #include <string>
 
 using namespace std;
 
 
 string encrypt(string message, int key) {
     string encrypted = "";
 
     for (char ch : message) {
         if (isalpha(ch)) {
             char base = isupper(ch) ? 'A' : 'a';
             encrypted += (ch - base + key) % 26 + base;
         } else {
             encrypted += ch; 
         }
     }
 
     return encrypted;
 }
 
 
 string decrypt(string message, int key) {
     return encrypt(message, 26 - key); 
 }
 
 int main() {
     string message;
     int key;
 
     cout << "Enter a message to encrypt: ";
     getline(cin, message);
 
     cout << "Enter a key (1-25): ";
     cin >> key;
 
     // Input validation
     if (key < 1 || key > 25) {
         cout << "Invalid key. Must be between 1 and 25." << endl;
         return 1;
     }
 
     string encrypted = encrypt(message, key);
     string decrypted = decrypt(encrypted, key);
 
     cout << "\nEncrypted message: " << encrypted << endl;
     cout << "Decrypted message: " << decrypted << endl;
 
     return 0;
     
