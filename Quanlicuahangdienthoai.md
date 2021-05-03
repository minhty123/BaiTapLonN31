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
