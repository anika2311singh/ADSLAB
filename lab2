#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

struct Node{
    int data;
    struct Node *npx;
};

struct Node *head=NULL;
struct Node* XOR(struct Node *add1, struct Node *add2){
    struct Node *res;
    res=(struct Node*)((uintptr_t)(add1)^(uintptr_t)(add2));
    return res;
}


void insert(int data){
    struct Node *newNode=(struct Node*)malloc(sizeof(struct Node));
    newNode->data=data;

    newNode->npx=XOR(head,NULL);
    if(head==NULL){
        head=newNode;
    }
    else{
        struct Node *next=XOR(head->npx,NULL);
        head->npx=XOR(newNode,next);

        head=newNode;
    }
}

int delete(){

    if(head==NULL){
        printf("Empty List!!");
        return -1;
    }

    struct Node *curr=head;
    struct Node *next=NULL;
    struct Node *prev=NULL;
    struct Node *prev2=NULL;
    while(XOR(curr->npx,prev) != NULL){
        next=XOR(curr->npx,prev);
        prev=curr;
        curr=next;
    }
    int res=curr->data;
    prev=XOR(curr->npx,NULL);
    prev2=XOR(prev->npx,curr);
    prev->npx=XOR(prev2,NULL);
    free(curr);
    return res;
}


void print(){
    struct Node *curr=head;
    struct Node *next=NULL;
    struct Node *prev=NULL;


    while(curr != NULL){
        printf("%d ",curr->data);

        next=XOR(curr->npx,prev);
        prev=curr;

        curr=next;
    }
}



int main()
{

    while(1){
        int ch;
        printf("Enter 1 to insert:\n");
        printf("Enter 2 to delete:\n");
        printf("Enter 3 to Display\n");
        printf("Enter 4 to Exit\n");
        scanf("%d",&ch);
        switch(ch){
            case 1:{
                int data;
                printf("\nEnter the data to be inserted :");
                scanf("%d",&data);
                insert(data);
                break;
            }

            case 2:
                printf("Deleted Value %d\n",delete());
                break;
            case 3:
                printf("Data in the list are \n");
                print();
                break;
            case 4:
                exit(0);
            default:
                printf("Error!!! Enter the correct value");
                break;
        }

    }
}
