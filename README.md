# Lego_Bot
Code for the Lego_Bot
#include <kipr/botball.h>
int mleft = 0;
int mright = 1;
int sleft = 0;
int sright = 1;

void followLine(double runSeconds)
{
    double startSeconds = seconds();
    int temp0=2550;
    int temp1=1800;
    while (seconds()-startSeconds < runSeconds){ //loop forever
        if(analog(sleft)> temp0 && analog(sright)< temp1){
            motor(mleft,85); 
            motor(mright,85);
            printf("Continue straight/n");
        }//if left on blue and right on white, go forward following line
        else if (analog(sleft)<temp0 && analog(sright)<temp1){
            motor(mleft,77);
            motor(mright,90);
            printf("Turning Left/n");
        }//left on white and right on white, go left 
        else if (analog(sleft)<temp0 && analog(sright)>temp1){
            motor(mleft,85);
            motor(mright,80);
            printf("Turning Right/n");
        }//left on white and right on blue, go right
        else if (analog(sleft)>temp0 && analog(sright)>temp1){
            motor(mleft,90);
            motor(mright,80);
            printf("Turning-Right/n");
        }//if left on blue and right on blue, go right
        //msleep(100);
    }//endWhile
}//end followLine

int main()
{

    motor(mleft,5);
    motor(mright,5);
    msleep(500);
    //Follow Line Forward for 3 seconds
         followLine(3);
	return 0;//exit program
}    
/*
int addTwoNumbers(int a, int b)
{
 	return a+b;   
}
*/




