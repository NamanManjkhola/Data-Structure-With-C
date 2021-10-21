```c
/******************************************************************************
Stack Implementation using Array
operations->
1. push
2. pop
3. peek
4. display
*******************************************************************************/
#include <stdio.h>
#include <stdlib.h>

typedef struct Stack{
    int top;
    unsigned int max;
    int *array;
} Stack;

Stack*createStack(unsigned int capacity){
    Stack *ptr;
    ptr = (Stack*)malloc(sizeof(Stack));
    ptr->max = capacity;
    ptr->top = -1;
    ptr->array = (int*)malloc(sizeof(int)*capacity);

    return ptr;
};

void push(Stack*s,int element){
    if(s->top == s->max-1){
        printf("Stack is full");
        exit(1);
    }
    
    s->array[++s->top] = element;
    printf("\nElement successfully pushed!");
}

int pop(Stack*s){
    if(s->top == -1){
        printf("Stack is empty");
        exit(1);
    }
    
    return s->array[s->top--];
}

int peek(Stack*s){
    if(s->top == -1){
        printf("Stack is empty");
        exit(1);
    }
    return s->array[s->top];
}

void display(Stack*s){
    if(s->top == -1){
        printf("Stack is empty");
        exit(1);
    }
    
    int t = s->top;
    while(t>=0){
        printf("%d ",s->array[t]);
        t--;
    }
}

int main()
{
    unsigned int m;
    printf("Enter the maximum size of stack ");
    scanf("%u", &m);
    Stack * s1 = createStack(m);
    
    push(s1,10);
    push(s1,20);
    push(s1,30);
    peek(s1);
    display(s1);
    
    printf("\nElement popped is %d\n",pop(s1));
    peek(s1);
    display(s1);

    return 0;
}

```
