/*PRF192*/
#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
#include <math.h>
#include <Windows.h>
#include <limits.h>
struct cophieu
{
    char name[3];
    float first;
    float last;
};
typedef struct cophieu CP;
void menu(){
    printf("1.Hien thi gia tri cua chung khoan theo thu tu tang dan.\n");
    printf("2.Tim kiem theo ma chung khoan\n");
    printf("3.Tim kiem ma chung khoan co xu huong tang\n");
    printf("4.Tim ma co so ngay tang lon nhat\n");
    printf("5.Ket thuc chuong trinh\n");

}
void input(){

}
void function1(int n,CP a[]){
    CP tmp;
    int i,j;
    printf("gia tri co phieu trung binh la :\n");
    for(i=0;i<n;i++){
        float x=0;
    for(j=i;j<n*10;j+=n){
        x+=(a[j].last-a[j].first);
    }
    printf("%3s %.3f\n",a[i].name,x/10);
    printf("\n");
    }
    printf("Gia tri co phieu theo thu tu tang dan la:\n");
    for( i=0;i<n*10;i++){
        for(j=i+1;j<n*10-1;j++){
            if((a[i].last-a[i].first)>(a[j].last-a[j].first)){
                tmp=a[i];
                a[i]=a[j];
                a[j]=tmp;
            }
        }
    }
    for(i=0;i<n*10;i++){
        printf("%3s %.3f %.3f\n",a[i].name,a[i].first,a[i].last);
    }
}
void function2(int n,CP a[]){
    char x[3];int i;float max=-1e6;float min=1e6;
    printf("Nhap ma muon tim kiem: ");
    scanf("%s",&x);
    int flag=0;int save;
    for(i=0;i<n*10;i++){
        if(strcmp(x,a[i].name)==0){
            flag=1;
            save=i;
           break;
        }
    }
    if(flag==1){
        for(i=save;i<n*10;i+=n){
            if(a[i].last>max) max=a[i].last;
            if(a[i].last<min) min=a[i].last;
    }
    printf("gia tri co phieu cuoi ngay cua %s lon nhat la %.3f nho nhat la %.3f",x,max,min);

    }else printf("khong co du lieu phu hop duoc tim thay.\n");
}
void function3(int n,CP a[]){
    int i,j;
    for(i=0;i<n;i++){
        for( j=i;j<n*9;j+=n){
            if((a[j].last-a[j].first)>0&&(a[j+n].last-a[j+n].first)>0){
                printf("Chung khoan co xu huong tang la %3s \n",a[i].name);break;
            }
        }
    }
}
void function4(int n,CP a[]){
int dem[100];
memset(dem,0,100);
int i,j;
for(i=0;i<n;i++){
    for(j=i;j<n*10;j+=n){
        if((a[j].last-a[j].first)>0) dem[i]++;
}
}
int max=0;
    for(i=0;i<n;i++){
        if(dem[i]>=max){
            max=dem[i];
    }
    }
    for(i=0;i<n;i++){
        if(dem[i]==max){
            printf("ma chung khoan co so ngay tang lon nhat la %3s voi so ngay %d \n",a[i].name,max);
    }
}
}
void function5(){
    printf("ASSIGNMENT FOR SE1750-PRF192 Code exam 01\n");
    printf("ten\n MSSV: \n");
}
int main(){
    int numberofCP,i;
    FILE *FileIn;
    CP a[1000];

int choice;

while(choice!=5){
    menu();
    FileIn= fopen("D:\\assiment\\datain.txt","r");
    fscanf(FileIn,"%d",&numberofCP);
    for(i=0;i<numberofCP*10;i++){
        fscanf(FileIn,"%3s%f%f",&a[i].name,&a[i].first,&a[i].last);
    }
    printf("Choice:");
    scanf("%d",&choice);
    system("cls");
switch (choice)
{
case 1:
system("cls");
    function1(numberofCP,a);
    printf("\n");
    break;
case 2:
system("cls");
    function2(numberofCP,a);
    printf("\n");
    break;
case 3:
system("cls");
    function3(numberofCP,a);
    printf("\n");
    break;
case 4:
system("cls");
    function4(numberofCP,a);
    printf("\n");
    break;
case 5:
system("cls");
    function5();
    printf("\n");
    break;
default:
    break;
}
printf("\n");
}
system("cls");
   fclose(FileIn);
}
