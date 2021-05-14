#include<stdio.h>
#include<conio.h>
#include<iostream>
#include<string.h>
#include<stdlib.h>
struct DIENTHOAI{
	char ten[30];
	char id[10];
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
int main(){
	FILE*file;
	DIENTHOAI dienthoai[100];
	int DTcantim;
	int i;
	int somau;
	nhapdienthoai(dienthoai,somau);
	menu(dienthoai,somau);
}
void nhap(DIENTHOAI dienthoai[]){
	printf("id dien thoai:");
	fflush(stdin);
	gets(dienthoai->id);
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
	}while(somau <= 0);
	for(int i=0;i<somau;i++){
		printf("\t\t------nhap thong tin dien thoai %d-------\n",i+1);
		nhap(&(dienthoai[i]));
	}
}
void xuatdienthoai(DIENTHOAI dienthoai[],int &somau){
	printf("ma dien thoai || ten dien thoai || he dieu hanh || gia tien || so luong\n");
	for(int i=0;i<somau;i++){
		printf("%s\t || %s\t || %s\t || %2f\t || %d\n",dienthoai[i].id,&dienthoai[i].ten,dienthoai[i].hedieuhanh,dienthoai[i].giatien,dienthoai[i].soluong);
	}
	return;
}
void sapxepid(DIENTHOAI dienthoai[],int somau){
	DIENTHOAI temp;
	for(int i=0;i<somau-1;i++){
		for(int j=i+1;j<somau;j++){
			if(strcmp(dienthoai[i].id,dienthoai[j].id)<0){
				temp=dienthoai[i];
				dienthoai[i]=dienthoai[j];
				dienthoai[j]=temp;
			}
		}
	}
}
void sapxephedieuhanh(DIENTHOAI dienthoai[],int somau){
	DIENTHOAI temp;
	for(int i=0;i<somau-1;i++){
		for(int j=i+1;j<somau;j++){
			if(strcmp(dienthoai[i].hedieuhanh,dienthoai[j].hedieuhanh)<0){
				temp=dienthoai[i];
				dienthoai[i]=dienthoai[j];
				dienthoai[j]=temp;
			}
		}
	}
}
void sapxepten(DIENTHOAI dienthoai[],int somau){
	DIENTHOAI temp;
	for(int i=0;i<somau-1;i++){
		for(int j=i+1;j<somau;j++){
			if(strcmp(dienthoai[i].ten,dienthoai[j].ten)<0){
				temp=dienthoai[i];
				dienthoai[i]=dienthoai[j];
				dienthoai[j]=temp;
			}
		}
	}
}
