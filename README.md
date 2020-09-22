<div align="center">

## FCFS \(First Come First Serve\) CPU Scheduling


</div>

### Description

This Describes the principle of a queue processing technique or servicing conflicting demands by ordering process or also known as CPU scheduling. The program displays the list of process and their burst and waiting time and the total waiting and burst time.
 
### More Info
 
any integer from 1 to 20

CPU scheduling

the list of process and their burst and waiting time and the total waiting and burst time.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Blueorange Tekknologee](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/blueorange-tekknologee.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Data Structures](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/data-structures__3-8.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/blueorange-tekknologee-fcfs-first-come-first-serve-cpu-scheduling__3-12179/archive/master.zip)





### Source Code

```
#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
struct Process //structure for processes
{
 int burst;
 int time;
};
//--------functions------------------------
//a function that displays the processes and their burst time
int validate(int processInput)
{
	if(processInput == 0 || processInput>20)
		return 0;
	else
		return 1;
}
void heading()
{
	gotoxy(18,3);
	printf(" ---------------------------------------\n");
	gotoxy(18,4);
	printf("| FIRST COME FIRST SERVE CPU SCHEDULING |\n");
	gotoxy(18,5);
	printf(" ---------------------------------------\n");
	gotoxy(18,6);
	printf("| 1 - Use this program         |\n");
	gotoxy(18,7);
	printf("| 2 - CREDITS             |\n");
	gotoxy(18,8);
	printf("| 3 - Exit               |\n");
	gotoxy(18,9);
	printf(" ---------------------------------------\n");
	gotoxy(18,10);
  printf("Enter your choice(1-4):");
}
void displayProcess(Process p[], int processInput, int sum, float &awt)
{
int i,index=1,yAxis=12;
	gotoxy(18,12);
	printf("Processes\tBurst Time\tWaiting Time\n");
 for(i=0;i<processInput;i++)
 {
	gotoxy(18,yAxis+=1);
 printf("\tP%d\t%5d\t%15d\n", index, p[i].burst, p[i].time);
 index++;
 }
 gotoxy(18,yAxis+2);
 printf("Total Waiting Time = %d\n",sum);
 gotoxy(18,yAxis+3);
 printf("Average Waiting Time = %.2f",awt);
}
//a function that generates random burst for each processes
void randomBurst(Process p[], int processInput)
{
int i,burstTime;
	randomize();//call randomize function
 for(i=0;i<processInput;i++)
 {
	burstTime=rand()%10; //generate random number
  p[i].burst=burstTime; //assign the random number to each process' burst time
 }
}
//a function that computes the waiting time of each process, sum and average of waiting time
void waitingTime(Process p[],int processInput,int &sum, float &awt)
{
int i;
	p[0].time = 0; //always assign zero waiting time for process 1
	p[1].time=p[0].burst; //assign the burst time of process 1 to process 2
  sum=p[1].time; //sum stores the waiting time of process 2
 for(i=2;i<processInput;i++)//assign waiting time for the succeeding processes
 {      //process1 burstTime + process1 waiting time
	p[i].time=(p[i-1].burst + p[i-1].time);
	sum += p[i].time;
 }
}
main()
{
 Process p[20];
 int processInput,burstTime,i,j,sum=0,choice;
 float awt=0.00;
 do
 {
 heading();
 scanf("%d",&choice);
	if(choice == 1)
	{
		clrscr();
		gotoxy(18,10);
		printf("Enter the Number of processes(1-20):");
		scanf("%d",&processInput);
			if(validate(processInput) == 1)
			{
				randomBurst(p,processInput);
				waitingTime(p,processInput,sum,awt);
				awt = (sum/processInput);
				displayProcess(p,processInput,sum,awt);
				getch();
				clrscr();
				fflush(stdin);
			}
			else
			{
			clrscr();
     }
	}
	else if(choice == 2)
	{
	clrscr();
	gotoxy(18,10);
	printf("\tCreated by:\n");
	gotoxy(18,11);
	printf("Created By:\n");
	gotoxy(18,12);
	printf("Blueorange Tekknologee\n");
	getch();
	clrscr();
	}
 }
 while(choice!=3);
 clrscr();
 gotoxy(32,10);
 printf("GOoDByE!");
}
```

