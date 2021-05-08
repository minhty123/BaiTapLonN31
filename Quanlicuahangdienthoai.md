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
