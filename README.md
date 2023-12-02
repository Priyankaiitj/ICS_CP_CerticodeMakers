we developed a vaccination registration system using C programming language. This system allows users to input and manage personal and vaccination-related details for individuals.

To achieve this, we structured the program around two key elements: the PersonalInfo and VaccinationInfo structures. These structures effectively capture and organize personal information (like name, ID, gender, contact details, etc.) and vaccination specifics (such as vaccine name, dosage, location, date, etc.).

For user interaction, we designed a menu-driven interface within the main function. This interface offers a smooth flow allowing users to input personal details, vaccination information, and subsequently generate a receipt combining both sets of information.

To ensure each individual receives a unique identification, we implemented a system to generate a distinct receipt number for every entry using a global counter (globalReceiptCounter). This number is then assigned to each person's registration details.

The code runs in a loop until the user chooses to exit (option
4). Upon selecting options 1 and 2, the program prompts the user to input the relevant information, which can then be printed as a receipt using option 3.

Overall, this code represents an efficient and user-friendly solution for registering and managing vaccination-related data.

