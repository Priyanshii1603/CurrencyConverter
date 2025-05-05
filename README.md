import java.util.Scanner;

class CurrencyConversion {

    // Initial Conversion rates (USD to other currencies)
    
     double usdToEur = 0.95;
     
     double usdToGbp = 0.80;
     
     double usdToInr = 86.34;
     
     double usdToJpy = 154.24;
     
     double usdToAud = 1.59;
     
     double usdToCad = 1.44;
     
     double usdToNzd = 1.76;
     
     double usdToKrw = 1433.5;

    // Initial Conversion rates (INR to other currencies)
     double inrToEur = 0.011;
     double inrToGbp = 0.0093;
     double inrToUsd = 0.012;
     double inrToJpy = 1.78;
     double inrToAud = 0.018;
     double inrToCad = 0.0165;
     double inrToNzd = 0.020;
     double inrToKrw = 16.65;

    // Array to store conversion history
     String[] conversionHistory = new String[100];
     int historyIndex = 0;

    // Convert USD to another currency
    double convertUsdToCurrency(int option, double amount) {
        switch (option) {
            case 1: return amount * usdToEur;
            case 2: return amount * usdToGbp;
            case 3: return amount * usdToInr;
            case 4: return amount * usdToJpy;
            case 5: return amount * usdToAud;
            case 6: return amount * usdToCad;
            case 7: return amount * usdToNzd;
            case 8: return amount * usdToKrw;
            default: return -1;
        }
    }

    // Convert INR to another currency
    double convertInrToCurrency(int option, double amount) {
        switch (option) {
            case 9: return amount * inrToEur;
            case 10: return amount * inrToGbp;
            case 11: return amount * inrToUsd;
            case 12: return amount * inrToJpy;
            case 13: return amount * inrToAud;
            case 14: return amount * inrToCad;
            case 15: return amount * inrToNzd;
            case 16: return amount * inrToKrw;
            default: return -1;
        }
    }

    // Get the currency name based on conversion
    String getCurrencyName(int option) {
        switch (option) {
            case 1: case 9: return "EUR";
            case 2: case 10: return "GBP";
            case 3: return "INR";
            case 11: return "USD";
            case 4: case 12: return "JPY";
            case 5: case 13: return "AUD";
            case 6: case 14: return "CAD";
            case 7: case 15: return "NZD";
            case 8: case 16: return "KRW";
            default: return "Invalid currency";
        }
    }

    // Method to store conversion history
    void storeConversionHistory(String entry) {
        if (historyIndex < conversionHistory.length) {
            conversionHistory[historyIndex++] = entry; // Store the history entry
        } else {
            System.out.println("History is full. Cannot store more conversions.");
        }
    }

    // Method to display conversion history
     void viewConversionHistory() {
        if (historyIndex == 0) {
            System.out.println("No conversions yet.");
        } else {
            System.out.println("\nConversion History:");
            // Loop through the stored conversion history and print each entry
            for (int i = 0; i < historyIndex; i++) {
                System.out.println((i + 1) + ". " + conversionHistory[i]);
            }
        }
    }

    // Method to update USD exchange rates
     void updateUsdExchangeRates() {
        Scanner sc = new Scanner(System.in);
        System.out.println("\nChoose which USD exchange rate you want to change:");
        System.out.println("1. USD to EUR");
        System.out.println("2. USD to GBP");
        System.out.println("3. USD to INR");
        System.out.println("4. USD to JPY");
        System.out.println("5. USD to AUD");
        System.out.println("6. USD to CAD");
        System.out.println("7. USD to NZD");
        System.out.println("8. USD to KRW");
        System.out.print("Select an option (1-8): ");
        
        int choice = sc.nextInt();

        System.out.print("Enter the new exchange rate: ");
        double newRate = sc.nextDouble();

        switch (choice) {
            case 1: usdToEur = newRate; break;
            case 2: usdToGbp = newRate; break;
            case 3: usdToInr = newRate; break;
            case 4: usdToJpy = newRate; break;
            case 5: usdToAud = newRate; break;
            case 6: usdToCad = newRate; break;
            case 7: usdToNzd = newRate; break;
            case 8: usdToKrw = newRate; break;
            default: System.out.println("Invalid choice."); return;
        }

        System.out.println("Exchange rate updated successfully!");
    }

    // Method to update INR exchange rates
    void updateInrExchangeRates() {
        Scanner sc = new Scanner(System.in);
        System.out.println("\nChoose which INR exchange rate you want to change:");
        System.out.println("1. INR to EUR");
        System.out.println("2. INR to GBP");
        System.out.println("3. INR to USD");
        System.out.println("4. INR to JPY");
        System.out.println("5. INR to AUD");
        System.out.println("6. INR to CAD");
        System.out.println("7. INR to NZD");
        System.out.println("8. INR to KRW");
        System.out.print("Select an option (1-8): ");
        
        int choice = sc.nextInt();
		if (choice>8 || choice <1){
			System.out.println("Invalid choice");
		}
		else{
        System.out.print("Enter the new exchange rate: ");
        double newRate = sc.nextDouble();

        switch (choice) {
            case 1: inrToEur = newRate; break;
            case 2: inrToGbp = newRate; break;
            case 3: inrToUsd = newRate; break;
            case 4: inrToJpy = newRate; break;
            case 5: inrToAud = newRate; break;
            case 6: inrToCad = newRate; break;
            case 7: inrToNzd = newRate; break;
            case 8: inrToKrw = newRate; break;
            default: System.out.println("Invalid choice."); return;
        }

        System.out.println("Exchange rate updated successfully!");
		}
    }
}

// Main class for currency converter
class CurrencyConverter {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        CurrencyConversion conversion = new CurrencyConversion(); // Create object of CurrencyConversion class

        while (true) {
            // Display the menu with options
            System.out.println("\nCurrency Converter Menu");
            System.out.println("***************************************");
            System.out.println("1. Convert USD to EUR");
            System.out.println("2. Convert USD to GBP");
            System.out.println("3. Convert USD to INR");
            System.out.println("4. Convert USD to JPY");
            System.out.println("5. Convert USD to AUD");
            System.out.println("6. Convert USD to CAD");
            System.out.println("7. Convert USD to NZD");
            System.out.println("8. Convert USD to KRW");
            System.out.println("9. Convert INR to EUR");
            System.out.println("10. Convert INR to GBP");
            System.out.println("11. Convert INR to USD");
            System.out.println("12. Convert INR to JPY");
            System.out.println("13. Convert INR to AUD");
            System.out.println("14. Convert INR to CAD");
            System.out.println("15. Convert INR to NZD");
            System.out.println("16. Convert INR to KRW");
            System.out.println("17. View Conversion History");
            System.out.println("18. Update USD Exchange Rates");
            System.out.println("19. Update INR Exchange Rates");
            System.out.println("20. Exit");
            System.out.println("-----------------------------------------");

            System.out.print("Choose an option (1-20): ");
            int choice = sc.nextInt();

            if (choice == 20) {
                System.out.println("Exiting the program. Thank you!!");
                break; // Exit the program
            }

            if (choice == 17) {
                conversion.viewConversionHistory(); // View conversion history
                continue;
            }

            if (choice == 18) {
                conversion.updateUsdExchangeRates(); // Update USD exchange rates
                continue;
            }

            if (choice == 19) {
                conversion.updateInrExchangeRates(); // Update INR exchange rates
                continue;
            }

            System.out.print("Enter the amount: ");
            double amount = sc.nextDouble();

            if (amount <= 0) {
                System.out.println("Please enter a positive amount.");
                continue;
            }

            // Perform conversion based on user choice
            double convertedAmount = 0;
            String targetCurrency = "";
			String sourceCurrency="";

            if (choice <= 8) {
                convertedAmount = conversion.convertUsdToCurrency(choice, amount);
                targetCurrency = conversion.getCurrencyName(choice);
				sourceCurrency = "USD";
            } else {
                convertedAmount = conversion.convertInrToCurrency(choice, amount);
                targetCurrency = conversion.getCurrencyName(choice);
				sourceCurrency = "INR";
            }

            // Display conversion result with proper formatting
           System.out.println("Converted " + amount + " " + sourceCurrency +" to "+ convertedAmount + " " + targetCurrency);

            // Store the conversion history
            String historyEntry = "Converted " + amount + " " + sourceCurrency + " to " + convertedAmount + " " + targetCurrency;
            conversion.storeConversionHistory(historyEntry);
        }
    }
}
