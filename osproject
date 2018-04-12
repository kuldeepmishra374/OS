#include<stdio.h>
#include<iostream>

struct process
{
	int arrivalTime;
	int burstTime;
	int priority;
	char processName[3];
	int averageTime;
	int status; // 0-waiting, 1-running
};

struct queue{
	struct process *p;
	struct queue *next;
}*readyQueue=NULL,*temp,*prev=NULL;

struct process* createProcess(int userProcess);
void Stimulate(struct process *p,int userProcess,int executionTime);
 main()
{
	int userProcess;
	int i;
	struct process *p;
	printf("Enter no of Process: ");
	scanf("%d",&userProcess);
	p=createProcess(userProcess);
Stimulate(p,userProcess,0);

	
}

//Function  to input the n process with its arrival time and burst time

struct process* createProcess(int userProcess)
{
	struct process *p;
	int i;
	p=new process[userProcess];
	for(i=0;i<userProcess;i++)
	{
		printf("Process name :\t");
		scanf("%s",(p+i)->processName);
		printf("Arrivl time :");
		scanf("%d",&(p+i)->arrivalTime);
		printf("Burst time :");
		scanf("%d",&(p+i)->burstTime);
		(p+i)->priority=0;
		(p+i)->averageTime=0;
		(p+i)->status=0;
	}
	return p;
}

//Simulation function



void Stimulate(struct process *pr,int userProcess,int executionTime)
{
	
	struct process *runingProcess;
	struct queue *ready;
	int flagCheck=1,flag=0;
	
	int i;
		while(flagCheck)
		{
			flag=0;
			readyQueue=NULL;
		
			for(i=0;i<userProcess;i++)
			{	
				
				if(((pr+i)->arrivalTime-executionTime)<=0 && (pr+i)->burstTime>0)
				{
					ready=new queue;
					ready->p = (pr+i);
					ready->next=NULL;
					
					if(readyQueue==NULL)
					{
						readyQueue=ready;
							
					}
					else
					{	
						
						temp=readyQueue;
						while(temp->next!=NULL )
						{
							if(ready->p->priority == temp->p->priority)
							{
								if(temp->p->status==1)
								{
									break;
								}
								else
								{
									prev=temp;
									temp=temp->next;
								}
							
								
							 }
							else if( ready->p->priority < temp->p->priority )
							{
							prev=temp;
							temp=temp->next;
							}
							else
							{
								break;
							}
						}
						if(prev==NULL )
						{
							if(( ready->p->priority==temp->p->priority ))
							{
								if(temp->p->status==1)
								{
									
									ready->next=readyQueue;
									readyQueue=ready;
								}else
								{
									temp->next=ready;
								}
							}else if(ready->p->priority<temp->p->priority)
							{
								temp->next=ready;
							}
							else if(ready->p->priority>temp->p->priority)
							{
									ready->next=readyQueue;
									readyQueue=ready;
								
							}
						
						} else 
						if(temp->next==NULL)
						{
							if( ready->p->priority <= temp->p->priority )
							temp->next=ready;
						}
						else
						{
							ready->next=temp;
							prev->next=ready;
						}
						
					}
				}}
					
				
					temp=readyQueue;
								            runingProcess=readyQueue->p;
											readyQueue->p->burstTime-=1;
											readyQueue->p->status=1;
											readyQueue->p->priority+=1;
											temp=readyQueue;
											while(temp!=NULL)
											{	
												if(temp->p == runingProcess)   //changing here
												{
													
												}
												else
												{
													temp->p->priority+=2;
													temp->p->status=0;
													temp->p->averageTime+=1;
												}
												temp=temp->next;
											}
											
						for(i=0;i<userProcess;i++)
						{
							if((pr+i)->burstTime!=0)
							{
								flag=1;
								break;
							}
						}
						if(flag==1)
						{
							executionTime++;
						}
						else
						{
						 	flagCheck=0;
						}
				    	temp=readyQueue;
				            printf("\n ProcessName \t Arrival Time \t Burst Time \t Average Waiting time \t Priority \t Status");
							for(i=0;i<userProcess;i++)
								{
								    printf("\n\t%s\t\t%d\t\t%d\t\t%d\t\t\t%d\t\t%d",(pr+i)->processName,(pr+i)->arrivalTime,(pr+i)->arrivalTime,(pr+i)->averageTime,(pr+i)->priority,(pr+i)->status);
								}
	               					
				}
}
