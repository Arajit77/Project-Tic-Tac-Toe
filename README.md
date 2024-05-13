// Project-Tic-Tac-Toe
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
#include<time.h>
int choice, player=1;
char mark;
char name1[32];
char name2[32];
int i=-1;
char arr[]={'0','1','2','3','4','5','6','7','8','9'};
void DemoBoard()
{ 
   
   

    printf("\n\n========TIC-TAC-TOE=========\n\n");

    printf("    %c |       %c  |    %c  \n",arr[1],arr[2],arr[3]);
    printf("______|__________|________ \n");
    printf("    %c |       %c  |    %c    \n",arr[4],arr[5],arr[6]);
    printf("______|__________|_________\n");
    printf("    %c |       %c  |    %c    \n",arr[7],arr[8],arr[9]);
    printf("      |          |           ");
    printf("\n\n");     
    
   
}
int Logic()
{
   

    if(arr[1]==arr[2] && arr[2]==arr[3])
    {
        return 1;
    }
    if(arr[1]==arr[4] && arr[4]==arr[7])
    {
        return 1;
    }
    if(arr[7]==arr[8] && arr[8]==arr[9])
    {
        return 1;
    }
    if(arr[3]==arr[6] && arr[6]==arr[9])
    {
        return 1;
    }
    if(arr[1]==arr[5] && arr[5]==arr[9])
    {
        return 1;
    }
    if(arr[3]==arr[5] && arr[5]==arr[7])
    {
        return 1;
    }
    if(arr[2]==arr[5] && arr[5]==arr[8])
    {
        return 1;
    }
     if(arr[4]==arr[5] && arr[5]==arr[6])
    {
        return 1;
    }

    int count=0;
    for (int i = 1; i <=9; i++)
    {
        if(arr[i]=='X' || arr[i]=='O')
        {
            count++;
        }
    }
    
    if(count==9)
    {
        return 0;
    }
    return -1;
    
}
void input()
{
     player=(player%2)? 1:2 ; // 0%2=0,1%2=1,2%2=0 3%2=1  0=TRUE / 1=FALSE IN THIS BASIC 1 AND 2 ARE PICKED

      printf("PLAYER %d CHOOSE YOUR BOX :",player);
      scanf("%d",& choice);
      if(choice<=0 || choice>=10)
      {
        printf("INVALID INPUT, CHOOSE BETWEEN (1-9)\n");
        input();
      }
}
//==========CODE OF FILLING THE BOARD============= 

void Marking()
{
      
      DemoBoard();
  while(i==-1)
   { 
      input();
      mark=(player==1) ? 'X' : 'O';    // HERE IF PLAYER'S VALUE IS 1 THEN IT WILL be PICKED 'X'(IT IS TERNERY OPERATOR)
      arr[choice]=mark;
      system("cls");
      DemoBoard();   
     i= Logic(); 
     
     if(i==1 && player==1)
     {
        printf(">>>>>>  PLAYER %d (%s) WON  <<<<<<\n\n\n",player,name1);  // WHICH PLAYER WILL GIVE THE LAST MOVE , OBIOUSLY HE WILL WIN THE MATCH
       // return;
     }
     else if(i==1 && player==2)
     {
        printf(">>>>>>  PLAYER %d (%s) WON  <<<<<<\n\n\n",player,name2);  
     }
    else if(i==0)
    {
        printf("====MATCH DRAW====");
       // return;
    }
      player++;
    }
}

//=================RANDOM NUMBER GAUSING FUNCTION====================

 int computer()
 {
    srand(time(0));
    int n = (rand()%9);
  //  printf("COMPUTER HAS CHOSEN %d",n);
    return n;
 } 

 //================FILING THE BOARD (PLAY WITH COMPUTER)====================

 void MarkingCom()
 {
    int choose,i=-1,player=1,com;
    DemoBoard();
    while(i==-1)
    {
      char p=(player%2==1) ? 'C' : 'Y';  // 0%2=0,1%2=1,2%2=0,3%2=1        y=float(x)
     

    printf("your turn --> CHOOSE YOUR BOX :");
    scanf("%d",&choose);
    if(choose>=10 || choose<=30)
    {
        printf("INVALID MOVE");
    }

    arr[choose]='X';
    com=computer();
    
    arr[com+1]='O';

    i=Logic();
    if(i==1)
    {
        printf("%s WON ",p);
        return ;
    }
    else if (i==0)
    {
        printf("====MATCH DRAW====\n\n\n\n");
        return ;
    }
     player++;   
    system("cls");
    DemoBoard();
    }

 }     
 void userInterface()
 {
     printf("PLAYER 1 ENTER  NAME :");
     scanf("%s",name1);
     printf(" PLAYER 2 ENTER NAME :");
     scanf("%s",name2);
     printf("%s,YOU 'X' | %s YOU 'O' \n\n",name1,name2 );
     system("cls");

 } 

int main()
{  
     int c;

    printf("\n\n<<===== WELLOCME TO Tic-Tac-Toe =====>>\n\n");

  //  userInterface();
    // printf("\n\n1. PLAY 2 PLAYERS\n2. PLAY WITH COMPUTER\nENTER :");
    // scanf("%d",c);

    // if(c==1)
    // {
     Marking();
    // }
    // else if (c==2)
    // {
    //   MarkingCom();
    // }
 //   MarkingCom();
    printf("would you want to play again??\n1.yes\n2.no\nENTER :");
    scanf("%d",&c);
    if(c==1)
    {
       Marking();
    }
    else
    {
    printf("\n===THANK YOU====\n\n");
    }
    return 0;
}
