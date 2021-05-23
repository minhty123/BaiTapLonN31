#include<stdio.h>
#include<conio.h>
#include<iostream>
#include<string.h>
#include<stdlib.h>
#define MAX 1000
struct DIENTHOAI{
	char ten[30];
	char id[30];
	int soluong;
	float giatien;
	char hedieuhanh[30];
};
void nhap(DIENTHOAI dienthoai[]);
void nhapdienthoai(DIENTHOAI dienthoai[],int &somau);
void xuatdienthoai(DIENTHOAI dienthoai[],int &somau);
void menu(DIENTHOAI dienthoai[],int DTcanxoa,char DTcantim[],int somau,char fileName[]);
void sapxepid(DIENTHOAI dienthoai[],int somau);
void sapxepten(DIENTHOAI dienthoai[],int somau);
void sapxephedieuhanh(DIENTHOAI dienthoai[],int somau);
int thongke(DIENTHOAI dienthoai[],int somau,char DTcantim[]);
void Inthongke(DIENTHOAI dienthoai[],int somau,char DTcantim[]);
void xoadienthoai(DIENTHOAI dienthoai[],int DTcanxoa,int &somau);
void xuatFile(DIENTHOAI dienthoai[], int somau, char fileName[]);
int main(){
	DIENTHOAI dienthoai[MAX];
        char fileName[]= "DSDT.txt";
	int DTcanxoa;
	char DTcantim[MAX];
	int i;
	int somau;
	menu(dienthoai,DTcanxoa,DTcantim,somau,fileName);
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
int thongke(DIENTHOAI dienthoai[],int somau,char DTcantim[]){
	int Dem = 0;
	for(int i=0;i< somau;i++){
		if(strcmp(dienthoai[i].hedieuhanh,DTcantim)==0){
			Dem++;
		}
	}
	return Dem;
}
void Inthongke(DIENTHOAI dienthoai[],int somau,char DTcantim[]){
	if(somau != 0){
		DTcantim="Ios";
		printf("Co %d Mau Dien Thoai thuoc HDH %s!\n",thongke(dienthoai,somau,DTcantim),DTcantim);
		DTcantim="Android";
		printf("Co %d Mau Dien Thoai thuoc HDH %s!\n",thongke(dienthoai,somau,DTcantim),DTcantim);
	}
}
void menu(DIENTHOAI dienthoai[],int DTcanxoa,int somau){
	int luachon;
	do{
	    printf("---------------------MENU--------------------\n");
	    printf("1.Xuat cac mau Dien Thoai\n");
	    printf("2.Sap xep theo He Dieu Hanh\n");
	    printf("3.Sap xep theo Ten Dien Thoai\n");
	    printf("4.Sap xep theo id Dien Thoai\n");
	    printf("5.Xoa Thong tin Dien Thoai\n");
	    printf("6.Thoat!\n");
	    printf("-->lua chon cua ban:");
	    scanf("%d",&luachon);
    	switch(luachon){
	    	case 1:
			    xuatdienthoai(dienthoai,somau);
			    break;
	    	case 2:
		        sapxephedieuhanh(dienthoai,somau);
		        xuatdienthoai(dienthoai,somau);
			    break;
	    	case 3:
		        sapxepten(dienthoai,somau);
		        xuatdienthoai(dienthoai,somau);
		    	break;
    		case 4:
		        sapxepid(dienthoai,somau);
		        xuatdienthoai(dienthoai,somau);
		    	break;
		case 5:
			xoadienthoai(dienthoai,DTcanxoa,somau);
			xuatdienthoai(dienthoai,somau);
			break;
	        case 6:
			printf("ban da thoat!\n");
			break;	
	    	default:
		        printf("hay nhap lai!\n");
		    	break;
	    }
	}while(luachon !=6);
}
