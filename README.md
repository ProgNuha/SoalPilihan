/*------------------------------------------------------------------------------*/
/*	File			:	Modul Matriks.c										*/
/*	Deskripsi		:	Pengecekan	Matriks Nol					*/
/*	Algoritma		:	https://studiee.blogspot.co.id/2016/10/algoritma-mengecek-matriks-identitas.html*/
/*	Dimodif	Oleh	:	Mufida Nuha Salimah / 171511050					*/
/*			Tgl		:	24/12/17												*/
/*	Compiler		:	TDM-GCC 4.9.2 32-bit Release */

#include <stdio.h>
#define MAX 3

int b, k;

int M[MAX][MAX];
int menu_cek_matriks();
void transpose_matriks();
void pengecekan_matriks_nol ();
void pengecekan_matriks_identitas ();
void pengecekan_matriks_segitiga_atas ();
void pengecekan_matriks_segitiga_bawah ();
void pengecekan_matriks_diagonal ();
void pengecekan_matriks_simetris ();
void pengecekan_matriks_skalar ();
int input_elemen_matriks();



main()
{
// ALGORITMA
	int i, menu; 
	printf("\n\n");
	printf("= = = = = = = = = = = = = = = = = = = = = = = = = =\n");
	printf("= = = = = = P R O G R A M   M A T R I K S = = = = =\n");
	printf("= = = = = = = = = = = = = = = = = = = = = = = = = =\n\n");
	printf("= = = = = = = = P I L I H   M E N U = = = = = = = =");
	printf("\t\n1. Input Elemen Matriks");
	printf("\t\n2. Pengecekan Jenis Matriks");
	printf("\t\n3. Transpose Matriks");
	//printf("\t\n4. Invers Matriks");
	printf("\t\n5. Sorting Matriks");
	printf("\t\n9. Keluar aplikasi");
	printf("\t\nInput : ");
	scanf("%i", &menu);
	system("cls");
	
	switch(menu){
		case 1	:	input_elemen_matriks();	main();	break;			// Menginput elemen matriks
		case 2	:	menu_cek_matriks(); 		break;				// Menuju menu pengecekan matriks
		case 3	:	transpose_matriks(); 		break;				// Transpose Matriks
		//case 4	:
		//case 5 	:
		case 9	:	{
					printf("Tekan tombol sembarang untuk keluar dari aplikasi....");
					getch();							// Menunggu user merespon untuk melanjutkan ke proses berikutnya
					return 0;							// Keluar dari aplikasi
					
					}

		default	:	{
		printf("Menu yang anda pilih salah !!!\nTekan tombol sembarang untuk melanjutkan!!");
		getch();										// Menunggu user merespon untuk melanjutkan ke proses berikutnya
		fflush(stdin);									// Menghapus buffer input dari keyboard
		system("cls");									// Menghapus tampilan di layar
		main();											// Kembali ke modul main (Menu utama)
		break;
		}	
}
}

int input_elemen_matriks()
{
	printf("Input Elemen Matriks \n");
	for (b=1; b <= MAX; b++){
		for(k=1; k <= MAX; k++){
			printf ("elemen matriks M[%d][%d] : ", b, k);
			scanf ("%d", &M[b][k]);
		}
	}
	system ("cls");
	
	printf ("Tampilkan isi Matriks");
	for (b=1; b <= MAX; b++){
		printf("\n");
		for(k=1; k <= MAX; k++){
			printf ("%d\t\t", M[b][k]);
		}
	}
	return (M); 
}


int menu_cek_matriks()
{ 
	int i, cekmenu;

		system ("cls");
	
	printf ("Tampilkan isi Matriks");
	for (b=1; b <= MAX; b++){
		printf("\n");
		for(k=1; k <= MAX; k++){
			printf ("%d\t\t", M[b][k]);
		}
	}
	printf("\n\n= = = = = = = = = = = = = = = = = = = = = = = = = =\n");
	printf("= = = = C E K   J E N I S   M A T R I K S = = = = =\n");
	printf("= = = = = = = = = = = = = = = = = = = = = = = = = =\n\n");
	printf("= = = = = = = = P I L I H   M E N U = = = = = = = =");
	printf("\t\n1. Matriks Nol");
	printf("\t\n2. Matriks Identitas");
	printf("\t\n3. Matriks Segitiga Atas");
	printf("\t\n4. Matriks Segitiga Bawah");
	printf("\t\n5. Matriks Diagonal");
	printf("\t\n6. Matriks Simetris");
	printf("\t\n7. Matriks Skalar");
	printf("\t\n8. Menu Utama ");
	printf("\t\n9. Keluar aplikasi");
	printf("\t\nInput : ");
	scanf("%i", &cekmenu);
	system("cls");
	
		
		switch(cekmenu){
		case 1	:	pengecekan_matriks_nol (); break;
		case 2	:	pengecekan_matriks_identitas (); break;
		case 3	:	pengecekan_matriks_segitiga_atas (); break;
		case 4	:	pengecekan_matriks_segitiga_bawah ();  break;
		case 5	:	pengecekan_matriks_diagonal ();  break;
		case 6	:	pengecekan_matriks_simetris (); break;
		case 7	:	pengecekan_matriks_skalar (); break;
		case 8	:	main ();
		case 9	:	{
					printf("Tekan tombol sembarang untuk keluar dari aplikasi....");
					getch();							// Menunggu user merespon untuk melanjutkan ke proses berikutnya
					return 0;							// Keluar dari aplikasi
				 	}	
		default	:	{
		printf("Menu yang anda pilih salah !!!\nTekan tombol sembarang untuk melanjutkan!!");
		getch();										
		fflush(stdin);									
		system("cls");									
		menu_cek_matriks();											// Kembali ke modul main (Menu utama)
		break;
					}	
		}
}
					
void pengecekan_matriks_nol ()
//Matriks nol adalah matriks berordo (m x n) yang elemen-elemennya bernilai nol.
{

	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++){
		for (j=1;j<=3;j++){	
			if (M[i][j] != 0){
				cek = 'f';
			}
		}
	}
	if (cek == 't'){
		printf ("Matriks Nol\n");
	}
	else{
		printf ("Bukan Matriks Nol\n");
	}
	printf("Tekan tombol sembarang untuk kembali ke menu pengecekan jenis matriks. . .");
	getch();
	system("cls");
	menu_cek_matriks();	
}

void pengecekan_matriks_diagonal ()
//Matriks diagonal adalah matriks persegi (berordo m x m) yang elemen-elemen selain diagonal utama bernilai nol.
{
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++){
		for (j=1;j<=3;j++){
			if (i == j){
				if (M[i][j] == 0)
					{cek = 'f';}
				else{cek = 't';}
				}
			else{
				if (M[i][j] != 0) 
					{cek = 'f';}
				else{cek = 't';}
				}
		}
	}
	if (cek == 't'){
		printf ("Matriks Diagonal\n");
	}
	else{
		printf ("Bukan Matriks Diagonal\n");
	}
	printf("Tekan tombol sembarang untuk kembali ke menu pengecekan jenis matriks. . .");
	getch();
	system("cls");
	menu_cek_matriks();		
}	

void pengecekan_matriks_identitas ()
//Matriks identitas adalah matriks persegi (berordo m x m) yang elemen-elemen di diagonal utamanya bernilai 1 dan elemen-elemen selain diagonal utama bernilai nol.
{
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++){
		for (j=1;j<=3;j++){
			if (i == j){
				if (M[i][j] != 1)
					{cek = 'f';}
				else{cek = 't';}
				}
			else{
				if (M[i][j] != 0)
					{cek = 'f';}
				else{cek = 't';}
				}
			  
  		}
	}
	if (cek == 't'){
		printf ("Matriks Identitas\n");
	}
	else{
		printf ("Bukan Matriks Identitas\n");
	}
	printf("Tekan tombol sembarang untuk kembali ke menu pengecekan jenis matriks. . .");
	getch();
	system("cls");
	menu_cek_matriks();		
}

void pengecekan_matriks_segitiga_atas ()
//Matriks segitiga atas adalah matriks yang elemen-elemen di bawah diagonal utamanya bernilai nol.
{
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=3;i<=1;i--){
		for (j=1;j<i;j++){
			if(M[i][j] != 0){
				cek = 'f';
			}	
		}	
	}

		
	if (cek == 't'){
		printf ("Matriks Segitiga Atas\n");
	}
	else{
		printf ("Bukan Matriks Segitiga Atas\n");
	}
	printf("Tekan tombol sembarang untuk kembali ke menu pengecekan jenis matriks. . .");
	getch();
	system("cls");
	menu_cek_matriks();	 
}

void pengecekan_matriks_segitiga_bawah ()
//Matriks segitiga atas adalah matriks yang elemen-elemen di atas diagonal utamanya bernilai nol.
{
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++){
		for (j=i+1;j<=3;j++){
			if(M[i][j] != 0){
				cek = 'f';
			}	
		}	
	}


	if (cek == 't'){
		printf ("Matriks Segitiga Bawah\n");
	}
	else{
		printf ("Bukan Matriks Segitiga Bawah\n");
	}
	printf("Tekan tombol sembarang untuk kembali ke menu pengecekan jenis matriks. . .");
	getch();
	system("cls");
	menu_cek_matriks();	 	
}

void pengecekan_matriks_skalar ()
//Matriks skalar adalah matriks yang elemen-elemen pada diagonal utamanya sama dan elemen lain bernilai nol.
{
	int i,j,s;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++){
		for (j=1;j<=3;j++){
			if (M[1][1] == 0){
				cek = 'f';}
			else{s = M[1][1];
				if (i == j){
					if(M[i][j] != s){
						cek = 'f';}
					else{cek = 't';}
				}
				else{
					if (M[i][j] != 0){
						cek = 'f';}
					else{cek = 't';}
				}
			}
		}
	}
	
	if (cek == 't')
	{printf ("Matriks Skalar\n");
	}
	else
	{printf ("Bukan Matriks Skalar\n");
	}
	printf("Tekan tombol sembarang untuk kembali ke menu pengecekan jenis matriks. . .");
	getch();
	system("cls");
	menu_cek_matriks();	
}

void pengecekan_matriks_simetris ()
//Matriks simetris adalah matriks yang elemen-elemen di bawah dan di atas diagonal utamanya simetris. Dengan kata lain, elemen pada mn sama dengan pada nm.
{
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++){
		for (j=1;j<=3;j++){
			if (i != j){
				if (M[i][j] != M[j][i]){
					cek = 'f';}
				else{cek = 't';}
			}	
			
		}
	}
	
	if (cek == 't'){
		printf ("Matriks Simetris\n");
	}
	else{
		printf ("Bukan Matriks Simetris\n");
	}
	printf("Tekan tombol sembarang untuk kembali ke menu pengecekan jenis matriks. . .");
	getch();
	system("cls");
	menu_cek_matriks();	  	
}

void transpose_matriks()
{
	int i,j,s;									//i=baris, j=kolom								

	for (i=1;i<=3;i++){
		for (j=1;j<=i;j++){
		 	s=M[i][j];
			M[i][j]=M[j][i];
			M[j][i]=s;
		}
	}
	
	printf ("Tampilkan isi Matriks hasil Transpose");
	for (b=1; b <= MAX; b++){
		printf("\n");
		for(k=1; k <= MAX; k++){
			printf ("%d\t\t", M[b][k]);
		}
	}
	printf("\n\nTekan tombol sembarang untuk kembali ke menu utama program matriks. . .");
	getch();
	system("cls");
	main();	
}

void sorting_matriks()
{
	int i,j, temp;
	
	//Pengurutan Matriks 
	for (i=1;i<=3;i++){
		for (j=3;j<=2;j--){
			if(M[i][j]<M[i][j-1])
			{ temp = M[i][j];
			  M[i][j]=M[i][j-1];
		 	  M[i][j-1]=temp;
			
			}
		}
	}
}
