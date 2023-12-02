# ICS_CP_CerticodeMakers
#ICS Project
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_NAME_LEN 50
#define MAX_ID_LEN 20
#define MAX_GENDER_LEN 10
#define MAX_STATE_LEN 50
#define MAX_CITY_LEN 50
#define MAX_HOSPITAL_LEN 50
#define MAX_DATE_LEN 20
#define MAX_TIME_LEN 20
#define MAX_BLOOD_TYPE_LEN 5
#define MAX_CONTACT_NUM_LEN 15
#define MAX_VACCINE_NAME_LEN 50
#define MAX_AUTH_NAME_LEN 50
#define MAX_DOSAGE_LEN 10
#define MAX_NATIONALITY_LEN 20
#define MAX_PINCODE_LEN 10

struct PersonalInfo {
    char name[MAX_NAME_LEN];
    char idType[MAX_ID_LEN];
    char idNumber[MAX_ID_LEN];
    char gender[MAX_GENDER_LEN];
    char bloodType[MAX_BLOOD_TYPE_LEN];
    char contactNumber[MAX_CONTACT_NUM_LEN];
    char nationality[MAX_NATIONALITY_LEN];
    int receiptNumber;
};

struct VaccinationInfo {
    char vaccineName[MAX_VACCINE_NAME_LEN];
    char authorizationName[MAX_AUTH_NAME_LEN];
    char dosage[MAX_DOSAGE_LEN];
    char state[MAX_STATE_LEN];
    char city[MAX_CITY_LEN];
    char hospital[MAX_HOSPITAL_LEN];
    char date[MAX_DATE_LEN];
    char time[MAX_TIME_LEN];
    char pincode[MAX_PINCODE_LEN];
};

int globalReceiptCounter = 1000; // Global variable to generate unique receipt number

void clearInputBuffer() {
    int c;
    while ((c = getchar()) != '\n' && c != EOF) { }
}

void capturePersonalInfo(struct PersonalInfo *person) {
    printf("Enter Name: ");
    fgets(person->name, sizeof(person->name), stdin);
    person->name[strcspn(person->name, "\n")] = '\0';

    printf("Enter ID Type: ");
    fgets(person->idType, sizeof(person->idType), stdin);
    person->idType[strcspn(person->idType, "\n")] = '\0';

    printf("Enter ID Number: ");
    fgets(person->idNumber, sizeof(person->idNumber), stdin);
    person->idNumber[strcspn(person->idNumber, "\n")] = '\0';

    printf("Enter Gender: ");
    fgets(person->gender, sizeof(person->gender), stdin);
    person->gender[strcspn(person->gender, "\n")] = '\0';

    printf("Enter Blood Type: ");
    fgets(person->bloodType, sizeof(person->bloodType), stdin);
    person->bloodType[strcspn(person->bloodType, "\n")] = '\0';

    printf("Enter Contact Number: ");
    fgets(person->contactNumber, sizeof(person->contactNumber), stdin);
    person->contactNumber[strcspn(person->contactNumber, "\n")] = '\0';

    printf("Enter Nationality: ");
    fgets(person->nationality, sizeof(person->nationality), stdin);
    person->nationality[strcspn(person->nationality, "\n")] = '\0';
}

void captureVaccinationInfo(struct VaccinationInfo *vaccination) {
    printf("Enter Name of Vaccination: ");
    fgets(vaccination->vaccineName, sizeof(vaccination->vaccineName), stdin);
    vaccination->vaccineName[strcspn(vaccination->vaccineName, "\n")] = '\0';

    printf("Enter Authorization Name: ");
    fgets(vaccination->authorizationName, sizeof(vaccination->authorizationName), stdin);
    vaccination->authorizationName[strcspn(vaccination->authorizationName, "\n")] = '\0';

    printf("Enter Dosage (in ml): ");
    fgets(vaccination->dosage, sizeof(vaccination->dosage), stdin);
    vaccination->dosage[strcspn(vaccination->dosage, "\n")] = '\0';

    printf("Enter State: ");
    fgets(vaccination->state, sizeof(vaccination->state), stdin);
    vaccination->state[strcspn(vaccination->state, "\n")] = '\0';

    printf("Enter City: ");
    fgets(vaccination->city, sizeof(vaccination->city), stdin);
    vaccination->city[strcspn(vaccination->city, "\n")] = '\0';

    printf("Enter Hospital: ");
    fgets(vaccination->hospital, sizeof(vaccination->hospital), stdin);
    vaccination->hospital[strcspn(vaccination->hospital, "\n")] = '\0';

    printf("Enter Date: ");
    fgets(vaccination->date, sizeof(vaccination->date), stdin);
    vaccination->date[strcspn(vaccination->date, "\n")] = '\0';

    printf("Enter Time: ");
    fgets(vaccination->time, sizeof(vaccination->time), stdin);
    vaccination->time[strcspn(vaccination->time, "\n")] = '\0';

    printf("Enter Pincode: ");
    fgets(vaccination->pincode, sizeof(vaccination->pincode), stdin);
    vaccination->pincode[strcspn(vaccination->pincode, "\n")] = '\0';
}

void printVaccinationReceipt(struct PersonalInfo person, struct VaccinationInfo vaccination) {
    printf("\n--------------------------------------------------------\n");
    printf("| %-20s | %-30d |\n", "Receipt Number", person.receiptNumber);
    printf("| %-20s | %-30s |\n", "Name", person.name);
    printf("| %-20s | %-30s |\n", "ID Type", person.idType);
    printf("| %-20s | %-30s |\n", "ID Number", person.idNumber);
    printf("| %-20s | %-30s |\n", "Gender", person.gender);
    printf("| %-20s | %-30s |\n", "Blood Type", person.bloodType);
    printf("| %-20s | %-30s |\n", "Contact Number", person.contactNumber);
    printf("| %-20s | %-30s |\n", "Nationality", person.nationality);
    printf("|--------------------------------------------------------|\n");
    printf("| %-20s | %-30s |\n", "Vaccine Name", vaccination.vaccineName);
    printf("| %-20s | %-30s |\n", "Authorization Name", vaccination.authorizationName);
    printf("| %-20s | %-30s |\n", "Dosage (in ml)", vaccination.dosage);
    printf("| %-20s | %-30s |\n", "State", vaccination.state);
    printf("| %-20s | %-30s |\n", "City", vaccination.city);
    printf("| %-20s | %-30s |\n", "Hospital", vaccination.hospital);
    printf("| %-20s | %-30s |\n", "Date", vaccination.date);
    printf("| %-20s | %-30s |\n", "Time", vaccination.time);
    printf("| %-20s | %-30s |\n", "Pincode", vaccination.pincode);
    printf("--------------------------------------------------------\n");
}

int main() {
    int choice;
    struct PersonalInfo person;
    struct VaccinationInfo vaccination;

    do {
        printf("\nVaccination Registration Portal\n");
        printf("1. Capture Personal Information\n");
        printf("2. Enter Vaccination Information\n");
        printf("3. Print Vaccination Receipt\n");
        printf("4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        clearInputBuffer(); // Clear input buffer after scanf

        switch (choice) {
            case 1:
                capturePersonalInfo(&person);
                person.receiptNumber = globalReceiptCounter++; // Assign unique receipt number
                break;
            case 2:
                captureVaccinationInfo(&vaccination);
                break;
            case 3:
                if (person.receiptNumber == 0) {
                    printf("Please enter personal information first.\n");
                } else {
                    printVaccinationReceipt(person, vaccination);
                }
                break;
            case 4:
                printf("Exiting the program. Thank you!\n");
                exit(EXIT_SUCCESS);
            default:
                printf("Invalid choice! Please enter a valid option.\n");
        }
    } while (choice != 4);

    return 0;
}
