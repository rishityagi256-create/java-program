#include <stdio.h>
#include <stdlib.h>
#define MAX 5
int queue[MAX];
int front =-1,rear =-1;
void addjob()
{
    int job;
    if (rear ==MAX -1)
    {
        printf("Queue overflow! printer queue is full.\n");
        return;
    }
    printf("Enter print job number:");
    scanf("%d", &job);
    if (front ==-1)
    front = 0;
    rear++;
    queue[rear] = job;
    printf("print job added successfully.\n");
}
    void processjob()
    {
        if (front ==-1 || front > rear)
        {
            printf("queue underflow! no print jobs to process.\n");
            return;
        }
        printf("processing print job: %d\n", queue[front]);
        front++;
    if (front> rear)
    front = rear -1;
}
void displaycount()
{
    if (front == -1)

    printf("Number of waiting print jobs: 0\n", rear - front +1);
}
int main()
{
    int choice;
    while (1)
    {
        printf("\n--- PRINTER QUEUE ---\n");
        printf("1. Add a print job\n");
        printf("2. Process a print job\n");
        printf("3. Display number of waiting jobs\n");
        printf("4. Demonstrate overflow and underflow\n");
        printf("5. Exit\n");
        printf("Enter your choice");
        scanf("%d", &choice);
        switch (choice)
        {
            case 1:
            addjob();
            break;
            case 2:
            processjob();
            break;
            case 3:
            displaycount();
            break;
            case 4:
            printf("Queue capacity:%d\n",MAX);
            if (rear == MAX -1)
            printf("Overflow condition: Queue is full.\n");
            else
            printf("Overflow occurs when the queue is full.\n");
            if (front == -1)
            printf("Underflow conndition: Queue is empty.\n");
            else
            printf("Underflow occurs when deleting from an empty queue.\n");
            break;
            case 5:
            printf("Exiting Printer Queue Program.\n");
            exit(0);
            default:
            printf("invalid choice! Try again.\n");
        }
    }
    return 0;
}
