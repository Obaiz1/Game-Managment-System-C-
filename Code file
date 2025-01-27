#include <iostream>
#include <vector>
#include <algorithm>

struct Entry {
    std::string USER_NAME;
    float Total_bill;
};

std::vector<Entry> entry;
std::vector<Entry> discounted_records;
std::vector<std::string> subscribed_users;

std::vector<int> game_prices = {30, 25, 60, 40, 50, 10, 20, 150, 130};  // Prices for each game

std::vector<float> calculate_game_prices(std::vector<int>& hours) {
    std::vector<float> game_costs;
    for (size_t i = 0; i < hours.size(); ++i) {
        game_costs.push_back(static_cast<float>(hours[i] * game_prices[i]));
    }
    return game_costs;
}

void display_game_bar() {
    std::cout << "DISPLAY BAR" << std::endl;
    std::cout << "GAME AVAILABLE" << std::endl;
    std::cout << std::endl;
    std::cout << "AMONG US......Rs 40/hour" << std::endl;
    std::cout << "PUB G......Rs 120/hour" << std::endl;
    std::cout << "IGI 3......Rs 100/hour" << std::endl;
    std::cout << "TAKEN 3......Rs 80/hour" << std::endl;
    std::cout << "FREE_FIRE ......Rs 60/hour" << std::endl;
    std::cout << "CRICKET 2007......Rs 90/hour" << std::endl;
    std::cout << "ROAD_RASH......Rs 50/hour" << std::endl;
    std::cout << "LAST OF US......Rs 150/hour" << std::endl;
    std::cout << "TEKKEN 8......Rs 130/hour" << std::endl;
    std::cout << std::endl;
}

void record() {
    display_game_bar();

    Entry data;
    std::cout << "Enter your name: ";
    std::getline(std::cin, data.USER_NAME);

    std::vector<int> game_hours;

    for (const auto& game : {"TAKEN 3", "AMONG US", "GTA 5", "PUB G", "IGI 2", "HOUSE OF DEAD", "CRICKET 2007", "LAST OF US", "TEKKEN 8"}) {
        std::string play_game;
        std::cout << "Do you want to play " << game << "? (yes/no): ";
        std::getline(std::cin, play_game);

        if (play_game == "yes") {
            int hours;
            std::cout << "Enter how many hours you want to play " << game << ": ";
            std::cin >> hours;
            game_hours.push_back(hours);
        }
    }

    std::vector<float> game_costs = calculate_game_prices(game_hours);
    float Total_bill = 0;

    for (const auto& cost : game_costs) {
        Total_bill += cost;
    }

    std::cout << data.USER_NAME << ", your total bill is Rs. " << Total_bill << std::endl;

    std::string subscription_option;
    std::cout << "Do you want to subscribe for a monthly subscription? (yes/no): ";
    std::cin >> subscription_option;

    if (subscription_option == "yes") {
        float monthly_subscription_cost = 150;
        Total_bill += monthly_subscription_cost;
        subscribed_users.push_back(data.USER_NAME);
    }

    std::cout << data.USER_NAME << ", your total bill with subscription is Rs. " << Total_bill << std::endl;

    data.Total_bill = Total_bill;
    entry.push_back(data);
    std::cin.ignore();  // Consume the newline character left in the buffer
}

void display() {
    for (const auto& record : entry) {
        std::cout << "USER_NAME: " << record.USER_NAME << ", Total_bill: Rs. " << record.Total_bill << std::endl;
    }
}

void display_discounted_records() {
    std::cout << "Discounted Records:" << std::endl;
    for (const auto& record : discounted_records) {
        std::cout << "USER_NAME: " << record.USER_NAME << ", Total_bill: Rs. " << record.Total_bill << std::endl;
    }
}

void display_subscribed_users() {
    std::cout << "Subscribed Users:" << std::endl;
    for (const auto& user : subscribed_users) {
        std::cout << user << std::endl;
    }
}

void sorted_value() {
    std::sort(entry.begin(), entry.end(), [](const Entry& a, const Entry& b) {
        return a.Total_bill < b.Total_bill;
    });

    for (const auto& record : entry) {
        std::cout << "USER_NAME: " << record.USER_NAME << ", Total_bill: Rs. " << record.Total_bill << std::endl;
    }
}

void delete_search_value() {
    std::string name;
    std::cout << "Enter name to delete: ";
    std::getline(std::cin, name);

    entry.erase(std::remove_if(entry.begin(), entry.end(), [&name](const Entry& e) {
        return e.USER_NAME == name;
    }), entry.end());

    std::cout << "Entry for " << name << " deleted, if existed." << std::endl;
}

void update_entry() {
    std::string name;
    std::cout << "Enter name to update: ";
    std::getline(std::cin, name);

    for (auto& record : entry) {
        if (record.USER_NAME == name) {
            float new_bill;
            std::cout << "Enter the new total bill for " << name << ": ";
            std::cin >> new_bill;
            record.Total_bill = new_bill;
            std::cout << "Total bill for " << name << " updated to Rs. " << new_bill << "." << std::endl;
            break;
        }
    }
}

void apply_discount() {
    if (entry.empty()) {
        std::cout << "No entries to apply discount." << std::endl;
        return;
    }

    int entry_index;
    std::cout << "Select the entry number to apply discount (1 to " << entry.size() << "): ";
    std::cin >> entry_index;

    if (entry_index < 1 || entry_index > entry.size()) {
        std::cout << "Invalid entry number." << std::endl;
        return;
    }

    float discount_percentage;
    std::cout << "Enter the discount percentage: ";
    std::cin >> discount_percentage;

    Entry& user_entry = entry[entry_index - 1];
    float original_price = user_entry.Total_bill;
    float discount_amount = original_price * (discount_percentage / 100);
    float discounted_price = original_price - discount_amount;

    user_entry.Total_bill = discounted_price;
    std::cout << "Congratulations! " << user_entry.USER_NAME << ", you get a " << discount_percentage << "% discount." << std::endl;
    std::cout << "Original Price: Rs. " << original_price << std::endl;
    std::cout << "Discount Amount: Rs. " << discount_amount << std::endl;
    std::cout << "Discounted Price: Rs. " << discounted_price << std::endl;
    discounted_records.push_back(user_entry);
}

std::string get_maximum_discounted_price() {
    if (!discounted_records.empty()) {
        float max_discounted_price = std::max_element(discounted_records.begin(), discounted_records.end(),
            [](const Entry& a, const Entry& b) {
                return a.Total_bill < b.Total_bill;
            })->Total_bill;

        return "Maximum Discounted Price: Rs. " + std::to_string(max_discounted_price);
    }
    else {
        return "No discounted records available.";
    }
}

std::string calculate_average_sales() {
    if (!entry.empty()) {
        float average_sales = 0;
        for (const auto& record : entry) {
            average_sales += record.Total_bill;
        }
        average_sales /= entry.size();

        return "Average of Sales: Rs. " + std::to_string(average_sales);
    }
    else {
        return "No sales records available.";
    }
}

void display_menu() {
    std::cout << "WHICH OPTION YOU WANT TO CHOOSE" << std::endl;
    std::cout << "OPTION 1 IS ADD ENTRY" << std::endl;
    std::cout << "OPTION 2 IS SHOW ENTRY" << std::endl;
    std::cout << "OPTION 3 IS SHOW SORTED ENTRY" << std::endl;
    std::cout << "OPTION 4 IS DELETE VALUE" << std::endl;
    std::cout << "OPTION 5 IS UPDATE ENTRY" << std::endl;
    std::cout << "OPTION 6 IS APPLY DISCOUNT TO SELECTED ENTRY" << std::endl;
    std::cout << "OPTION 7 IS DISPLAY DISCOUNTED RECORDS" << std::endl;
    std::cout << "OPTION 8 IS DISPLAY SUBSCRIBED USERS" << std::endl;
    std::cout << "OPTION 9 IS DISPLAY MAXIMUM DISCOUNTED PRICE" << std::endl;
    std::cout << "OPTION 10 IS AVERAGE OF SALES" << std::endl;
    std::cout << "OPTION 11 IS QUIT SYSTEM" << std::endl;
    std::cout << std::endl;
}

void process_choice(int choice) {
    switch (choice) {
        case 1:
            record();
            std::cout << std::endl;
            break;
        case 2:
            display();
            std::cout << std::endl;
            break;
        case 3:
            sorted_value();
            std::cout << std::endl;
            break;
        case 4:
            delete_search_value();
            std::cout << std::endl;
            break;
        case 5:
            update_entry();
            std::cout << std::endl;
            break;
        case 6:
            apply_discount();
            std::cout << std::endl;
            break;
        case 7:
            display_discounted_records();
            std::cout << std::endl;
            break;
        case 8:
            display_subscribed_users();
            std::cout << std::endl;
            break;
        case 9:
            std::cout << get_maximum_discounted_price() << std::endl;
            std::cout << std::endl;
            break;
        case 10:
            std::cout << calculate_average_sales() << std::endl;
            std::cout << std::endl;
            break;
        case 11:
            std::exit(0);
        default:
            std::cout << "Invalid choice. Please enter a valid option." << std::endl;
    }
}

int main() {
    while (true) {
        display_menu();
        int choice;
        std::cout << "ENTER YOUR CHOICE: ";
        std::cin >> choice;
        std::cin.ignore();  // Consume the newline character left in the buffer
        process_choice(choice);
    }

    return 0;
}
