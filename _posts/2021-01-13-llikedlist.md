---
layout: post
title: "c- single linked list"
date: 2021-01-13
excerpt: "연구 선행학습 1 : c언어를 이용한 single linked list 구현하기 "


comments: true
---
'''
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node * next;
};

//메모리를 할당하여 입력한 value값을 저장한 노드를 만든다.
struct Node * createNode(int value)
{
    struct Node * newNode;

    newNode = (struct Node *) malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;

    return newNode;
}
//다음노드에 새로 만든 노드를 연결한다
void insertNext(struct Node *curr, int value)
{

    struct Node * newNode;

    newNode = createNode(value);
    newNode->next = curr->next;
    curr->next = newNode;
}
//정렬을 위해 head에 curr포인터를 지정하고 반복문이 실행되면서 curr이 모든 노드를 한번씩 지정하도록 한다. 이 때 curr의 다음 data가 현재 지정하고 있는 값보다 크면
//다음 데이터를 p포인터로 지정하여 노드의 맨 앞으로 빼준다. 뺀 후에는 curr이 다시 맨앞의 노드를 지정하도록 하여 노드를 data 값이 작은 순 부터 정렬해준다.
void insertSort(struct Node *head)
{
    struct Node *curr,*p;

    p=NULL;
    curr=head;

    while(curr->next!=NULL){
        if(curr->data>curr->next->data){
            p=curr->next;
            curr->next=curr->next->next;

            p->next=head;
            head=p;
            curr=p;

        }
        else{
            curr=curr->next;
        }

    }

    printf("inserSort result:");
    printAll(head);



}
//curr이 맨 처음 노드를 지정한 후 반복문으로 모든 노드를 한번씩 지정하게 되면서 value값과 같은 data값을 가진 노드를 지정하게 되면 그 노드를 return해준다.
{
     struct Node * curr;
     curr = head;
     while (curr!= NULL) {
         if (curr->data == value)
         return curr;
         curr = curr->next;
     }
     return NULL;
}
//curr이 맨 처음 노드를 지정한 후 반복문으로 모든 노드를 한번씩 지정하게 되면서 삭제 할 노드의 전 노드에 curr이 위치하도록 하고, 포인터 p를 삭제할 노드로 지정해준다.
//이는 삭제할 노드의 전 노드와 다음 노드를 이어주기 위함이다.
void delnode(struct Node *head, int value)
{
    struct Node *curr, *p;
    p=NULL;
    curr=head;

    while(curr!=NULL){
        //삭제할 노드가 첫 노드라면 head의 값을 다음 노드로 지정해준다.
        if(head->data==value){
            p=head;
            head=head->next;
            free(p);
            printf("'%d'is deleted in this list.\n",value);

            break;
        }

        else if(curr->next->data==value){
            p=curr->next;
            curr->next=curr->next->next;
            free(p);
            printf("'%d'is deleted in this list.\n",value);
            break;
        }
        else{
            curr=curr->next;
        }
    }
    //만얃 value와 같은 값의 data를 가지고 있는 노드가 없을 때 아래와 같이 출력한다.
    if(curr=NULL){
        printf("!no value that you find in this list!\n");
    }
}
//head포인터를 이용해 반복문으로 모든 노드를 지정하면서 노드의 data값을 모두 출력하게 한다.
void printAll(struct Node * head)
{
     while(head != NULL) {
         printf("[%d]->", head->data);
         head = head->next;
     }
     printf("NULL\n");
}

int main()
{
     struct Node *head, *temp, *curr;


     head = NULL;
     curr=NULL;

     temp = createNode(3);
     head = temp;
     curr = temp;

     temp = createNode(5);
     curr->next = temp;
     curr = temp;

     temp = createNode(7);
     curr->next = temp;
     curr = temp;

     temp = searchNode(head, 5);
     insertNext(temp, 9);

     temp = createNode(2);
     curr->next = temp;
     curr = temp;

     temp = createNode(6);
     curr->next = temp;
     curr = temp;

     printAll(head);
     delnode(head,5);
     printAll(head);
     insertSort(head);


}
'''
