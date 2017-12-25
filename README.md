/*------------------------------------------------------------------------------*/
/*	File			:	Modul Matriks.c										*/
/*	Deskripsi		:	Pengecekan	Matriks Nol					*/
/*	Dibuat	Oleh	:	https://studiee.blogspot.co.id/2016/10/algoritma-mengecek-matriks-identitas.html*/
/*	Dimodif	Oleh	:	Mufida Nuha Salimah / 171511050					*/
/*			Tgl		:	24/12/17												*/
/*	Compiler		:	TDM-GCC 4.9.2 32-bit Release */

#include <stdio.h>
#define MAKS 5

//KAMUS DATA
int M [3][3]={0,0,0,
			  0,0,0,
			  0,0,0};		//deklarasi isi matriks

int b, k;
//void input_nilai_matriks();
void pengecekan_matriks_nol ();
void pengecekan_matriks_identitas ();
void pengecekan_matriks_segitiga_atas ();
void pengecekan_matriks_segitiga_bawah ();
void pengecekan_matriks_diagonal ();
void pengecekan_matriks_simetris ();
void pengecekan_matriks_skalar ();

main()
{
	
	/*printf("Masukkan nilai pada elemen baris (m) matriks : \n");
	scanf("%d", b);
	printf("Masukkan nilai pada elemen kolom (n) matriks : ");
	scanf("%d", k);
	for (b=1;b<=3;b++)
	{
		for (k=1;k<=3;k++)
		{
			printf("Elemen M[%d][%d] : ", b,k);
			scanf("%d", &M[b][k]); break;
		}
	}
	//pengecekan_matriks_nol(int M[b][k]);*/
}

void pengecekan_matriks_nol ()
//Matriks nol adalah matriks berordo (m x n) yang elemen-elemennya bernilai nol.
{
	//int M [3][3]={{0,0,0},{0,0,0},{0,0,0}};		//deklarasi isi matriks
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++)
	{for (j=1;j<=3;j++)
		{if (&M[i][j] != 0)
			{cek = 'f';
			}
		}
	}
	if (cek = 't')
	{printf ("Matriks Nol");
	}
	else
	{printf ("Bukan Matriks Nol");
	}
}

void pengecekan_matriks_diagonal ()
//Matriks diagonal adalah matriks persegi (berordo m x m) yang elemen-elemen selain diagonal utama bernilai nol.
{
	//int M [3][3]={{0,0,0},{0,0,0},{0,0,0}};		//deklarasi isi matriks
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++)
	{for (j=1;j<=3;j++)
		{if (i == j)
			{if (M[i][j] = 0)
				{cek = 'f';
				}
			else
			{if (M[i][j] != 0) 
				{cek = 'f';
				}
			}
			}
		}
	}
	if (cek = 't')
	{
		printf ("Matriks Nol");
	}
	else
	{
		printf ("Bukan Matriks Nol");
	}
}	

void pengecekan_matriks_identitas ()
//Matriks identitas adalah matriks persegi (berordo m x m) yang elemen-elemen di diagonal utamanya bernilai 1 dan elemen-elemen selain diagonal utama bernilai nol.
{
	//int M [3][3]={{0,0,0},{0,0,0},{0,0,0}};		//deklarasi isi matriks
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++)
	{for (j=1;j<=3;j++)
		{if (i == j)
			{if (M[i][j] != 1)
				{cek = 'f';
				}
			else
			{if (M[i][j] != 0)
				{cek = 'f';
				}
			}
			}
		}
	}
	if (cek = 't')
	{printf ("Matriks Identitas");
	}
	else
	{printf ("Bukan Matriks Identitas");
	}
}

void pengecekan_matriks_segitiga_atas ()
//Matriks segitiga atas adalah matriks yang elemen-elemen di bawah diagonal utamanya bernilai nol.
{
	//int M [3][3]={{0,0,0},{0,0,0},{0,0,0}};		//deklarasi isi matriks
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++)
	{for (j=1;j<=3;j++)
		{if (i < j)
			{if (M[i][j] != 0)
				{cek = 'f';
				}
			else
			{if (M[i][j] == 0)
				{cek = 'f';
				}
			}
			}
		}
	}
	if (cek = 't')
	{printf ("Matriks Segitiga Atas");
	}
	else
	{printf ("Bukan Matriks Segitiga Atas");
	}
}

void pengecekan_matriks_segitiga_bawah ()
//Matriks segitiga atas adalah matriks yang elemen-elemen di atas diagonal utamanya bernilai nol.
{
	//int M [3][3]={{0,0,0},{0,0,0},{0,0,0}};		//deklarasi isi matriks
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++)
	{for (j=1;j<=3;j++)
		{if (i > j)
			{if (M[i][j] != 0)
				{cek = 'f';
				}
			else
			{if (M[i][j] == 0)
				{cek = 'f';
				}
			}
			}
		}
	}
	if (cek = 't')
	{printf ("Matriks Segitiga Bawah");
	}
	else
	{printf ("Bukan Matriks Segitiga Bawah");
	}
}

void pengecekan_matriks_skalar ()
//Matriks skalar adalah matriks yang elemen-elemen pada diagonal utamanya sama dan elemen lain bernilai nol.
{
	//int M [3][3]={{0,0,0},{0,0,0},{0,0,0}};		//deklarasi isi matriks
	int i,j,s;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++)
	{for (j=1;j<=3;j++)
		{while ((i == 1) && (j == 1))
			{s = M[i][j];
			}
		if (i == j)
			{if(M[i][j] != s)
					{cek = 'f';
					}
			else
			{if (M[i][j] != 0)
					{cek = 'f';
					}
			}
			}
		}
	}
	if (cek = 't')
	{printf ("Matriks Skalar");
	}
	else
	{printf ("Bukan Matriks Skalar");
	}
}

void pengecekan_matriks_simetris ()
//Matriks simetris adalah matriks yang elemen-elemen di bawah dan di atas diagonal utamanya simetris. Dengan kata lain, elemen pada mn sama dengan pada nm.
{
	//int M [3][3]={{0,0,0},{0,0,0},{0,0,0}};		//deklarasi isi matriks
	int i,j;									//i=baris, j=kolom								
	char cek = 't';								//pengecekan matriks
	
	for (i=1;i<=3;i++)
	{for (j=1;j<=3;j++)
		{while (i != j)
			{if (M[i][j] != M[j][i])
				{cek = 'f';
				}
			}
		}
	}
	
	if (cek = 't')
	{printf ("Matriks Simetris");
	}
	else
	{printf ("Bukan Matriks Simetris");
	}
}
