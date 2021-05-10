#include<stdio.h>
#include<conio.h>
#include<iostream>
#include<string.h>
#include<stdlib.h>
struct DIENTHOAI{
	char ten[30];
	char ma[10];
	int soluong;
	float giatien;
	char hedieuhanh[30];
};
void nhap(DIENTHOAI dienthoai[]);
void nhapdienthoai(DIENTHOAI dienthoai[],int &somau);
void xuatdienthoai(DIENTHOAI dienthoai[],int &somau);
void menu(DIENTHOAI dienthoai[],int somau);
void sapxepma(DIENTHOAI dienthoai[],int somau);
void sapxepten(DIENTHOAI dienthoai[],int somau);
void sapxephedieuhanh(DIENTHOAI dienthoai[],int somau);
int main
void nhap(DIENTHOAI dienthoai[]){
    printf("ma dien thoai:");
    fflush(stdin);
	gets(dienthoai->ma);
    printf("ten dien thoai:");
	gets(dienthoai->ten);
	printf("he dieu hanh:");
	gets(dienthoai->hedieuhanh);
	printf("so luong dien thoai:");
	scanf("%d",&dienthoai->soluong);
	printf("gia tien:");
	scanf("%f",&dienthoai->giatien);
}
void nhapdienthoai(DIENTHOAI dienthoai[],int &somau){
	do{
	    printf("--->nhap so mau:");
	    scanf("%d",&somau);
	    if(somau <= 0){
	    	printf("vui long nhap lai!\n");
		}
    }while(somau <= 0);
	for(int i=0;i<somau;i++){
		printf("\t\t------nhap thong tin dien thoai %d-------\n",i+1);
		nhap(&(dienthoai[i]));
	}
}
