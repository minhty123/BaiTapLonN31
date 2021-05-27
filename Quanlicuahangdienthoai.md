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
void Nhap(DIENTHOAI dienthoai[]);
void Nhapdienthoai(DIENTHOAI dienthoai[],int &somau);
void Xuatdienthoai(DIENTHOAI dienthoai[],int &somau);
void Menu(DIENTHOAI dienthoai[],int DTcanxoa,char DTcantim[],int somau,char fileName[]);
void Sapxepid(DIENTHOAI dienthoai[],int somau);
void Sapxepten(DIENTHOAI dienthoai[],int somau);
void Sapxephedieuhanh(DIENTHOAI dienthoai[],int somau);
int Thongke(DIENTHOAI dienthoai[],int somau,char DTcantim[]);
void Inthongke(DIENTHOAI dienthoai[],int somau,char DTcantim[]);
void Suadienthoai(DIENTHOAI dienthoai[],int somau);
void Xoadienthoai(DIENTHOAI dienthoai[],int DTcanxoa,int &somau);
void XuatFile(DIENTHOAI dienthoai[], int somau, char fileName[]);
int main(){
	DIENTHOAI dienthoai[MAX];
        char fileName[]= "DSDT.txt";
	int DTcanxoa;
	char DTcantim[30];
	int i;
	int somau;
	Menu(dienthoai,DTcanxoa,DTcantim,somau,fileName);
}
void Nhap(DIENTHOAI dienthoai[]){
	printf("Id Dien Thoai:");
	fflush(stdin);
	gets(dienthoai->id);
	printf("Ten Dien Thoai:");
	gets(dienthoai->ten);
	printf("He Dieu Hanh:");
	gets(dienthoai->hedieuhanh);
	printf("So luong Dien Thoai:");
	scanf("%d",&dienthoai->soluong);
	printf("Gia tien:");
	scanf("%f",&dienthoai->giatien);
}
void Nhapdienthoai(DIENTHOAI dienthoai[],int &somau){
	do{
	    printf("--->nhap so mau:");
	    scanf("%d",&somau);
	    if(somau <= 0){
	    	printf("vui long nhap lai!\n");
	    }
	}while(somau <= 0);
	for(int i=0;i<somau;i++){
		printf("\t\t------nhap thong tin dien thoai %d-------\n",i+1);
		Nhap(&(dienthoai[i]));
	}
}
void Xuatdienthoai(DIENTHOAI dienthoai[],int &somau){
	printf("------------------------------BANG DIEN THOAI-------------------------------\n");
	printf("ID\t||Ten Dien Thoai\t||He Dieu Hanh\t||So luong\t||Gia Tien \n");
	for(int i=0;i<somau;i++){
		printf("%-3s\t||%-17s\t||%-7s\t||%d\t\t||%0.1f\n",dienthoai[i].id,&dienthoai[i].ten,dienthoai[i].hedieuhanh,dienthoai[i].soluong,dienthoai[i].giatien);
	}
	return;
}
void Sapxepid(DIENTHOAI dienthoai[],int somau){
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
void Sapxephedieuhanh(DIENTHOAI dienthoai[],int somau){
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
void Sapxepten(DIENTHOAI dienthoai[],int somau){
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
int Thongke(DIENTHOAI dienthoai[],int somau,char DTcantim[]){
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
void Suadienthoai(DIENTHOAI dienthoai[],int somau){
	bool DTdaco=false;
	char id[30];
	printf("Nhap id Mau Dien Thoai can Sua:");
	fflush(stdin);
	gets(id);
	for(int i = 0;i < somau;i++){
		if(strcmp(id,dienthoai[i].id) == 0){
			printf("\n-------------------SUA THONG TIN DIEN THOAI---------------------\n");
			Nhap(&dienthoai[i]);
			DTdaco = true;
		}
	}	
	if(DTdaco){
		printf("Sua Thong Tin Dien Thoai thanh cong!\n");
	}
	else{
		printf("Khong co Mau Dien Thoai nay!\n");
	}
}
void Xoadienthoai(DIENTHOAI dienthoai[],int DTcanxoa,int &somau){
	printf("Nhap vao Mau Dien Thoai can xoa:");
	scanf("%d",&DTcanxoa);
	if(somau <= 0){
		return;
	}
        if(DTcanxoa > 0 && DTcanxoa <= somau){
	    for(int i = DTcanxoa - 1;i < somau ;i++){
		    dienthoai[i]=dienthoai[i+1];
	    }
	    --somau;
	    printf("\nXoa Dien Thoai thanh cong!\n");
        }
        else{
    	    printf("\nKhong co Mau Dien Thoai can xoa!\n");
	}
}
void XuatFile(DIENTHOAI dienthoai[], int somau, char fileName[]){
    FILE * fp;
    fp = fopen (fileName,"w");
    fprintf(fp, "%s\t||%s\t\t\t||%s\t||%s\t||%s\n", "Id","Ten","He Dieu Hanh","So Luong","Gia Tien");
    for(int i = 0;i < somau;i++){
        fprintf(fp, "%-3s\t||%-17s\t||%-7s\t||%d\t\t||%0.1f\n", dienthoai[i].id,dienthoai[i].ten, dienthoai[i].hedieuhanh, dienthoai[i].soluong, dienthoai[i].giatien);
    }
    fclose (fp);
}	
void Menu(DIENTHOAI dienthoai[],int DTcanxoa,char DTcantim[],int somau,char fileName[]){
	int luachon;
	do{
	    printf("---------------------MENU CHUC NANG--------------------\n");
	    printf("\t 1.Nhap vao Danh Sach Dien Thoai!\n");
	    printf("\t 2.Xuat cac Mau Dien Thoai\n");
	    printf("\t 3.Sap xep theo He Dieu Hanh\n");
	    printf("\t 4.Sap xep theo Ten Dien Thoai\n");
	    printf("\t 5.Sap xep theo Id Dien Thoai\n");
            printf("\t 6.Thong Ke Dien Thoai theo He Dieu Hanh!\n");
	    printf("\t 7.Sua Thong tin Dien Thoai!\n");
	    printf("\t 8.Xoa Thong tin Dien Thoai\n");
	    printf("\t 9.Xuat tep tin nhi phan!\n");
	    printf("\t 10.Thoat!\n");
	    printf("------------------------------------------------------\n");
	    printf("-->lua chon cua ban:");
	    scanf("%d",&luachon);
    	    switch(luachon){
	    	case 1:
    			printf("Ban da chon Nhap vao Danh Sach Dien Thoai!\n");
    			Nhapdienthoai(dienthoai,somau);
    			printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
    			break;
	    	case 2:
	    		printf("Ban Da Chon In ra Danh Sach Dien Thoai!\n");
			Xuatdienthoai(dienthoai,somau);
			printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
			break;
	    	case 3:
	    		printf("Ban Da Chon Sap xep theo HE DIEU HANH!\n");
		        Sapxephedieuhanh(dienthoai,somau);
		        Xuatdienthoai(dienthoai,somau);
		        printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
			break;
	    	case 4:
	    		printf("Ban da chon sap xep theo ten");
		        Sapxepten(dienthoai,somau);
		        Xuatdienthoai(dienthoai,somau);
		        printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
		    	break;
    		case 5:
    			printf("Ban da chon sap xep theo ID");
		        Sapxepid(dienthoai,somau);
		        Xuatdienthoai(dienthoai,somau);
		        printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
		    	break;
		case 6:
		    	printf("Ban Da chon Thong Ke Dien Thoai theo He Dieu Hanh!\n");
		    	Inthongke(dienthoai,somau,DTcantim);
		    	printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
		    	break;
		case 7:
		    	printf("Ban da chon Sua Thong Tin Dien Thoai!\n");
		    	Suadienthoai(dienthoai,somau);
		    	printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
		    	break;
		case 8:
		    	printf("--------------XOA DIEN THOAI--------------\n");
			Xoadienthoai(dienthoai,DTcanxoa,somau);
		        Xuatdienthoai(dienthoai,somau);
		        printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
		        break;
		case 9:
		        printf("Ban da chon xuat DS DT!\n");
		        XuatFile(dienthoai,somau,fileName);
			printf("Ban da xuat thanh cong vao file %s!\n",fileName);
			printf("\nBam phim bat ky de tiep tuc!\n");
                        getch();
		case 10:
			printf("Ban da thoat!\n");
		        break;	
	    	default:
		        printf("hay nhap lai!\n");
		    	break;
	    }
	}while(luachon !=10);
}
