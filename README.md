#include<stdio.h>
#include<stdlib.h>
  
struct Node{
    int data;
    struct Node* next;
};

struct Node* createNode(int data){
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->data = NULL;
    return newNode;

}

struct Node* mergesortedlists(struct Node* list1,struct Node* list2){
    if(list1==NULL)
    return list2;
    if(list2==NULL)
    return list1;
    
    if(list1->data<list2->data){
        list1->next=mergesortedlists(list1->next,list2);
        return list1;
    }else{
        list2->next=mergesortedlists(list1,list2->next);
        return list2;
    }
        
    }
    void printlist(struct Node* head){
        while(head!=NULL){
            printf("%d-> ", head->data);
            head = head->next;
        }
        printf("NULL\n");
    }
int main() {
    struct Node* list1 = createNode(1);
    list1->next = createNode(3);
    list1->next->next = createNode(5);

    struct Node* list2 = createNode(2);
    list2->next = createNode(4);
    list2->next->next = createNode(6);
    

    printf("List 1: ");
    printlist(list1);


    printf("List 2: ");
    printlist(list2);


    struct Node* mergedlist = mergesortedlists(list1,list2);
    printf("Merged List: ");
    printlist(mergedlist);

    return 0;



}
