Project Report: Game Billing and Subscription System

1. Project Overview
The Game Billing and Subscription System is a C++ console-based application developed to manage game-related billing, subscriptions, and discounts for users at a gaming center. The system allows users to select games, calculate bills based on hours played, and manage subscriptions. It also includes functionalities for applying discounts, maintaining user records, and analyzing sales data.

2. Objectives

Provide an efficient and user-friendly billing system for gaming centers.
Enable users to subscribe to a monthly service with added benefits.
Maintain accurate user records for billing and subscription management.
Implement functionalities like sorting records, applying discounts, and tracking subscribed users.
3. Key Features

Game Selection and Billing:
Users can select games from a predefined list and specify the hours they wish to play. The system calculates the total cost based on the hourly rates of the games.

Subscription Management:
Users can subscribe to a monthly service for an additional charge, which is added to their total bill.

Discount Application:
Discounts can be applied to user records, with the system recalculating the total bill and storing discounted records separately.

Record Management:
The system allows adding, deleting, and updating user records. Records can also be displayed in sorted order based on the total bill.

Sales Analysis:
The system calculates the average sales across all users and identifies the maximum discounted price among discounted records.

4. Technologies Used

Programming Language: C++
Libraries: Standard Template Library (STL) for data structures such as vectors and algorithms for sorting and searching.
5. Functional Modules

Add Entry: Collects user information, game selection, play hours, and subscription details.
Display Records: Displays all user records with their total bills.
Sorted Records: Sorts and displays user records in ascending order of total bills.
Update and Delete Records: Enables updating a user’s bill and deleting user records by name.
Apply Discounts: Allows applying discounts to specific user bills and maintains discounted records.
Subscribed Users: Displays all users subscribed to the monthly service.
Sales Insights: Calculates and displays average sales and the highest discounted price.
6. Implementation Details
The system uses a vector-based data structure to store user records, which allows dynamic resizing and efficient operations such as sorting and searching. A menu-driven approach ensures an intuitive user experience, with each functionality mapped to a menu option.

7. Limitations

Currently supports only console-based interaction.
No persistent storage; data is lost when the program terminates.
Input validation could be further enhanced for better error handling.
8. Future Enhancements

Integrate a database for persistent storage of records.
Develop a graphical user interface (GUI) for improved usability.
Add support for generating detailed billing receipts for users.
Enhance security features to protect user data.
9. Conclusion
The Game Billing and Subscription System is a practical solution for managing billing, subscriptions, and discounts in a gaming center. Its modular structure, user-friendly interface, and efficient record management make it a valuable tool. With future enhancements, the system can be expanded to support more advanced features and broader use cases.
