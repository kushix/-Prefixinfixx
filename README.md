# -Prefixinfixx
#include<stdio.h>
#include<stdlib.h>
#define max 5
void insertrear(int queue[max],int x,int *rear,int *front)
{
    (*rear)=((*rear)+1)%max;
    queue[*rear]=x;
}
void insertfront(int queue[max],int x,int *rear,int *front)
{
    (*front)=((*front)-1+max)%max;
    queue[*front]=x;
}
int deletefront(int queue[max],int *front,int *rear)
{
    int x;
    if(((*rear)+1)%max==*front)
    {
        printf("no elements");
        return NULL;
    }
    x=queue[*front];
    (*front)=((*front)+1)%max;
    return x;
}
int deleterear(int queue[max],int *front,int *rear)
{
    int x;
    if(((*rear)+1)%max==*front)
    {
        printf("no elements");
        return NULL;
    }
    x=queue[*rear];
    (*rear)=((*rear)-1+max)%max;
    return x;
}
void print(int queue[max],int front,int rear)
{
    if(((rear)+1)%max==front)
    {
        printf("\nQueue is empty!!");
        exit(0);
    }
    int i;
    i=front;
    while(i!=rear)
    {
        printf("\n%d",queue[i]);
        i=(i+1)%max;
    }
    printf("\n%d\n",queue[rear]);
}
int main()
{
    int ch,queue[max],x,rear=-1,front=0;
    printf("enter 1:insert front\n2:insert rear\n3:delete front\n4:delete rear\n5:print\n6:exit\n");
    while(1)
    {
        printf("enter choice\n");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1:
            {
                printf("enter element");
                scanf("%d",&x);
                insertfront(queue,x,&rear,&front);
                break;
            }
            case 2:
            {
                printf("enter element");
                scanf("%d",&x);
                insertrear(queue,x,&rear,&front);
                break;
            }
            case 3:
            {
                x=deletefront(queue,&front,&rear);
                printf("deleted element:%d\n",x);
                break;
            }
            case 4:
            {
                x=deleterear(queue,&front,&rear);
                printf("deleted element:%d\n",x);
                break;
            }
            case 5:
            {
                print(queue,front,rear);
                break;
            }
            default:exit(0);
                
        }
    }
    return 0;
}
