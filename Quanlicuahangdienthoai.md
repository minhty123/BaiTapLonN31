#include<stdio.h>
#include<iostream>
#include<conio.h>
#include<stdlib.h>
struct DIENTHOAI{
	char ten[30];
	char ma[10];
	int soluong;
	float giatien;
	char hedieuhanh[30];
  };
void nhapchitiet(DIENTHOAI*dienthoai);
void nhapdienthoai(DIENTHOAI*dienthoai,int &somau);
void xuatdienthoai(DIENTHOAI*dienthoai,int &somau);
void menu(DIENTHOAI*dienthoai,int somau);
void sapxepma(DIENTHOAI*dienthoai,int somau);
void sapxepten(DIENTHOAI*dienthoai,int somau);
void sapxephedieuhanh(DIENTHOAI*dienthoai,int somau);
int main
void nhapchitiet(DIENTHOAI*dienthoai){
	fflush(stdin);
    printf("ma dien thoai:\n");
	gets(dienthoai->ma);
    printf("ten dien thoai:\n");
	gets(dienthoai->ten);
	printf("he dieu hanh:\n");
	gets(dienthoai->hedieuhanh);
	printf("so luong dien thoai:\n");
	gets(dienthoai->soluong);
	printf("gia tien:\n");
	gets(dienthoai->giatien);
}
void nhapdienthoai(DIENTHOAI*dienthoai,int &somau){
	printf("nhap so mau:");
	scanf("%d",&somau);
	for(i=0;i<somau;i++){
		fflush(stdin);
		nhapchitiet(dienthoai+i);
	}
	return;
}
