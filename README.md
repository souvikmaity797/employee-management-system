
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_EMPLOYEES 10

struct Employee {
    char name[50];
    int id;
    float salary;
    char jobTitle[50];
};

void addEmployee(struct Employee employees[], int *count);
void printEmployees(struct Employee employees[], int count);

int main() {
    struct Employee employees[MAX_EMPLOYEES];
    int count = 0;
    char choice;

    do {
        printf("Employee Management System\n");
        printf("--------------------------\n");
        printf("1. Add Employee\n");
        printf("2. Print Employees\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf(" %c", &choice);

        switch (choice) {
            case '1':
                addEmployee(employees, &count);
                break;
            case '2':
                printEmployees(employees, count);
                break;
            case '3':
                printf("Exiting program...\n");
                break;
            default:
                printf("Invalid choice!\n");
                break;
        }
    } while (choice != '3');

    return 0;
}

void addEmployee(struct Employee employees[], int *count) {
    if (*count >= MAX_EMPLOYEES) {
        printf("Cannot add more employees!\n");
        return;
    }

    struct Employee employee;
    printf("Enter employee name: ");
    scanf("%s", employee.name);
    printf("Enter employee ID: ");
    scanf("%d", &employee.id);
    printf("Enter employee salary: ");
    scanf("%f", &employee.salary);
    printf("Enter employee job title: ");
    scanf("%s", employee.jobTitle);

    employees[*count] = employee;
    (*count)++;

    printf("Employee added successfully!\n");
}

void printEmployees(struct Employee employees[], int count) {
    if (count == 0) {
        printf("No employees to display!\n");
        return;
    }

    printf("Employees:\n");
    for (int i = 0; i < count; i++) {
        struct Employee employee = employees[i];
        printf("Name: %s\n", employee.name);
        printf("ID: %d\n", employee.id);
        printf("Salary: %f\n", employee.salary);
        printf("Job Title: %s\n", employee.jobTitle);
        printf("--------------------------\n");
    }
}
