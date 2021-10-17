// Programmer: Farahsanwar
// Class:  Section: 
// Purpose: This program calculates the monthly phone bill and how much would be saved if another plan was chosen.
#include <iostream> // for cin and cout to be used
#include <iomanip> // for formatting decimals
#include <string> // for string
using namespace std;
int main() // to check for hours
{ 
    const float PACKAGE_A_CHARGES = 9.95,
        PACKAGE_B_CHARGES = 14.95,
        PACKAGE_C_CHARGES = 19.95,

        PACKAGE_A_ADDITIONAL_CHARGES = 2.00,
        PACKAGE_B_ADDITIONAL_CHARGES = 1.00,

        PACKAGE_A_HOURS = 10,
        PACKAGE_B_HOURS = 20,

        _30_DAYS = 30,
        _31_DAYS = 31,
        _28_DAYS = 28,

        NUM_HOURS_IN_28_DAYS = 672,
        NUM_HOURS_IN_30_DAYS = 720,
        NUM_HOURS_IN_31_DAYS = 744;

    char menu_choice;
    int month; 
//A menu of choices that the user can pick from
    cout << "\nPackage A: For $9.95 per month 10 "
        << "hours are provided.\n"
        << "--Additional hours are $1.00 per hour."
        << endl
        << "Package B: For $14.95 per month 20 "
        << "hours are provided.\n"
        << "--Additional hours are $2.00 per hour."
        << endl
        << "Package C: For $19.95 per month unlimited\n"
        << "hours provided.\n"
        << endl;

    cout << "Choose package: ";
    cin >> menu_choice; // input package chosen
    cout << endl;

    switch (menu_choice)
    {
        int counter;
        float total_charges_A,
            total_charges_B,
            total_charges_C;

    case 'a':
    case 'A':
    case 'B':
    case 'b':
    case 'c':
    case 'C':
        cout << "Choose a month (use numbers)\n"
            << " E.g. 12 = December, 3 = March:" 
            << endl;
        cin >> month; // input month

        switch (month)
        {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
            counter = _31_DAYS;
            break;
        case 4:
        case 6:
        case 9:
        case 11:
            counter = _30_DAYS;
            break;
        case 2:
            counter = _28_DAYS;
            break; 

        default:
            cout << "Invalid month. Rerun program.\n"
                << "Try again."
                << endl;
            break;
        }

        if (counter >= _28_DAYS && counter <= _31_DAYS)
        {
            int hours_used;

            cout << "How many hours used? ";
            cin >> hours_used; // input hours
            cout << endl;

            if (hours_used < 0)
            {
                cout << "We're sorry. Hours must be "
                    << "greater than 0.\n"
                    << "Rerun the program and try "
                    << "again."
                    << endl;
            }
            else
            {
                if (counter == _31_DAYS &&
                    hours_used > NUM_HOURS_IN_31_DAYS)
                {
                    cout << "We're sorry. Hours must "
                        << "be "
                        << NUM_HOURS_IN_31_DAYS
                        << " or less.\nRerun the "
                        << "program and try"
                        << " again."
                        << endl;
                }
                else if (counter == _30_DAYS &&
                    hours_used > NUM_HOURS_IN_30_DAYS)
                {
                    cout << "We're sorry. Hours must "
                        << "be "
                        << NUM_HOURS_IN_30_DAYS
                        << " or less.\nRerun the "
                        << "program and try"
                        << " again."
                        << endl;
                }
                else if (counter == _28_DAYS &&
                    hours_used > NUM_HOURS_IN_28_DAYS)
                {
                    cout << "We're sorry. Hours must "
                        << "be "
                        << NUM_HOURS_IN_28_DAYS
                        << " or less.\nRerun the "
                        << "program and try"
                        << " again."
                        << endl;
                }
                else
                {
                    cout << setprecision(2) << fixed;

                    total_charges_A = hours_used > PACKAGE_A_HOURS 
                        ? PACKAGE_A_CHARGES + ((hours_used - PACKAGE_A_HOURS) * PACKAGE_A_ADDITIONAL_CHARGES) // Calculate cost of monthly bill and additional hours.
                        : PACKAGE_A_CHARGES;

                    total_charges_B = hours_used > PACKAGE_B_HOURS
                        ? PACKAGE_B_CHARGES + ((hours_used - PACKAGE_B_HOURS) * PACKAGE_B_ADDITIONAL_CHARGES) // Calculate cost of monthly bill and additional hours.
                        : PACKAGE_B_CHARGES;

                    total_charges_C = PACKAGE_C_CHARGES;

                    if (menu_choice == 'a' ||
                        menu_choice == 'A')
                    {
                        cout << "Package A monthly" 
                            << " charges: $"
                            << total_charges_A
                            << endl
                            << endl;
                        if (total_charges_A >
                            total_charges_B)
                        {
                            cout << "You could have "
                                << "saved $"
                                << total_charges_A - total_charges_B   // Calculate Package B total savings
                                << " with Package B."
                                << endl
                                << "You could have "
                                << "saved $"
                                << total_charges_A - total_charges_C
                                << " with Package C."
                                << endl;
                        }
                    }
                    else if (menu_choice == 'b' ||
                        menu_choice == 'B')
                    {
                        cout << "Package B monthly "
                            << "charges: $"
                            << total_charges_B
                            << endl;
                        if (total_charges_B >
                            total_charges_C)
                        {
                            cout << "You could have "
                                << "saved $"
                                << total_charges_B - total_charges_C // Calculate Package C total savings
                                << " with Package C."
                                << endl;
                        }
                    }
                    else if (menu_choice == 'c' ||
                        menu_choice == 'C')
                    {
                        cout << "Package C monthly "
                            << "charges: $"
                            << total_charges_C
                            << endl;
                    }
                }
            }
        }
        break;

    default:
        cout << "We're sorry. Menu choice must be A, \n" // Error in package choice
            << "B, or C.\n"
            << "Rerun the program and try again."
            << endl;
        break;
    }
    cout << endl;

    return 0;  
}

                      
                      
