# student-record-system
#include <iostream>
using namespace std;

class Student {
public:
    int rollNo;
    string name;
    float marks;
};

int main() {

    Student students[100];
    int totalStudents = 0;
    int choice;

    do {
        cout << "\n===== STUDENT RECORD SYSTEM =====";
        cout << "\n1. Add Student";
        cout << "\n2. View All Students";
        cout << "\n3. Search Student";
        cout << "\n4. Update Student";
        cout << "\n5. Delete Student";
        cout << "\n6. Exit";
        cout << "\nEnter your choice: ";
        cin >> choice;

        
        if(choice == 1) {

            cout << "\nEnter Roll Number: ";
            cin >> students[totalStudents].rollNo;

            cin.ignore();

            cout << "Enter Name: ";
            getline(cin, students[totalStudents].name);

            cout << "Enter Marks: ";
            cin >> students[totalStudents].marks;

            totalStudents++;

            cout << "\nStudent Added Successfully!\n";
        }

        
        else if(choice == 2) {

            if(totalStudents == 0) {
                cout << "\nNo Records Found!\n";
            }
            else {
                cout << "\n===== STUDENT RECORDS =====\n";

                for(int i = 0; i < totalStudents; i++) {

                    cout << "\nStudent " << i + 1;
                    cout << "\nRoll Number : " << students[i].rollNo;
                    cout << "\nName        : " << students[i].name;
                    cout << "\nMarks       : " << students[i].marks;
                    cout << "\n---------------------------";
                }
            }
        }

       
        else if(choice == 3) {

            int searchRoll;
            bool found = false;

            cout << "\nEnter Roll Number to Search: ";
            cin >> searchRoll;

            for(int i = 0; i < totalStudents; i++) {

                if(students[i].rollNo == searchRoll) {

                    cout << "\nStudent Found!";
                    cout << "\nRoll Number : " << students[i].rollNo;
                    cout << "\nName        : " << students[i].name;
                    cout << "\nMarks       : " << students[i].marks;

                    found = true;
                    break;
                }
            }

            if(!found) {
                cout << "\nStudent Not Found!\n";
            }
        }

       
        else if(choice == 4) {

            int updateRoll;
            bool found = false;

            cout << "\nEnter Roll Number to Update: ";
            cin >> updateRoll;

            for(int i = 0; i < totalStudents; i++) {

                if(students[i].rollNo == updateRoll) {

                    cin.ignore();

                    cout << "Enter New Name: ";
                    getline(cin, students[i].name);

                    cout << "Enter New Marks: ";
                    cin >> students[i].marks;

                    cout << "\nRecord Updated Successfully!\n";

                    found = true;
                    break;
                }
            }

            if(!found) {
                cout << "\nStudent Not Found!\n";
            }
        }

        
        else if(choice == 5) {

            int deleteRoll;
            bool found = false;

            cout << "\nEnter Roll Number to Delete: ";
            cin >> deleteRoll;

            for(int i = 0; i < totalStudents; i++) {

                if(students[i].rollNo == deleteRoll) {

                    for(int j = i; j < totalStudents - 1; j++) {
                        students[j] = students[j + 1];
                    }

                    totalStudents--;

                    cout << "\nRecord Deleted Successfully!\n";

                    found = true;
                    break;
                }
            }

            if(!found) {
                cout << "\nStudent Not Found!\n";
            }
        }

        // EXIT
        else if(choice == 6) {
            cout << "\nThank You!\n";
        }

        else {
            cout << "\nInvalid Choice!\n";
        }

    } while(choice != 6);

    return 0;
}

