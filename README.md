# suntek-training-2019
1)
#include <stdio.h>
void main()
{
	int i,j,n,c=1,k;
	char a[20],temp;
  printf("enter a string:");
	scanf("%s",a);
	i=0;
	while(a[i]!='\0')
	 i++;
	n=i;
	for(i=0;i<n;i++)
	{
		for(j=i+1;j<n;j++)
		{
			if(a[i]>a[j])
			{
				temp=a[i];
				a[i]=a[j];
				a[j]=temp;
			}
		}
	}
	for(i=0;i<n;i++)
	{
		if(a[i]==a[i+1])
		{
			c++;
		}
		else
		{
			printf("%c - %d",a[i],c);
			printf("\n");
			c=1;
		}
	}
}
2)
#include<stdio.h>
void sort(char a[],int n)
{
	char t;
	for(int i=0;i<n;i++)
	{
		for(int j=i+1;j<n;j++)
		{
			if(a[i]>a[j])
			{
				t=a[i];
				a[i]=a[j];
				a[j]=t;
			}
		}
	}
}
int len(char a[])
{
	int i=0;
	while(a[i]!='\0')
	i++;
	return(i);
}
int cmp(char a[],char b[],int n)
{
	for(int i=0;i<n;i++)
	{
		if(a[i]!=b[i])
		return 0;
	}
	return 1;
}
void main()
{
	char a[20],b[20];
	int l1,l2;
	printf("enter two strings:");
	scanf("%s%s",a,b);
	l1=len(a);
	l2=len(b);
	if(l1==l2)
	{
		sort(a,l1);
		sort(b,l2);
		if(cmp(a,b,l1))
		printf("\ngiven strings are anagrams");
	}
	else
	printf("\ngiven strings are not anagrams");
	
}
3)
#include<stdio.h>
#include<ctype.h>
#include<string.h>
void rev(char b[],int n)
{
	int i,j;
	char t;
	for(i=0,j=n-1;i<n/2;i++,j--)
	{
		t=b[i];
		b[i]=b[j];
		b[j]=t;
	}
}
void revc(char a[],int n)
{
	int i,j=0;
	char b[10],t;
	for(i=0;i<n;i++)
	{
		if(tolower(a[i])=='a'||tolower(a[i])=='e'||tolower(a[i])=='i'||tolower(a[i])=='o'||tolower(a[i])=='u')
			continue;
		else
		{
			b[j]=a[i];
			j++;
			a[i]='.';
		}
	}
	rev(b,j);	
	j=0;
	for(i=0;i<n;i++)
	{
		if(a[i]=='.')
		{
		 a[i]=b[j];
		 j++;
		}
	}
}

void main()
{
	char a[20];
	int i=0;
	printf("enter a string:");
	scanf("%s",a);
	revc(a,strlen(a));
	printf("consonants reversed string is:%s",a);
}
4)
#include<stdio.h>
int GCD(int a,int b)
{
	if(a==b)
		return b;
	if(a>b)
		return(a-b,b);
	return(a,b-a);
}
void main()
{
	int a,b,gcd,min,i;
	printf("enter two numbers:");
	scanf("%d%d",&a,&b);
	min=a<b?a:b;
	for(i=1;i<=min;i++)
	{
		if(a%i==0&&b%i==0)
			gcd=i;
	}
	printf("gcd using iteration:%d\n",gcd);
	gcd=GCD(a,b);
	printf("gcd using recursion:%d\n",gcd);
}
5)
#include<stdio.h>
#include<stdlib.h>
struct Node
{
	int data;
	struct Node *next;
};
struct Node* create(struct Node *h)
{
	struct Node *h1=h;
	struct Node* node=(struct Node*)malloc(sizeof(struct Node));
	scanf("%d",&node->data);
	node->next=NULL;
	while(h->next!=NULL)
	{
		h=h->next;
	}
	h->next=node;
	return(h1);
}
int lastn(struct Node *h,int n)
{
	if(n==0)
	{
	  printf("error");
	  exit(0);
	}
	while(n-1>0)
	{
		h=h->next;
		n--;
	}
	return(h->data);
}
void main()
{
	int n,l,i;
	struct Node* head=(struct Node*)malloc(sizeof(struct Node));
	struct Node *temp=head;
	printf("enter number of nodes:");
	scanf("%d",&n);
	printf("enter data into the nodes:");
	scanf("%d",&head->data);
	head->next=NULL;
	for(i=1;i<=n-1;i++)
	{ 	
		head=create(head);
	}
	printf("enter node position from the last:");
	scanf("%d",&l);
	printf("data at %d node from last is %d\n",l,lastn(head,n-l+1));
}
