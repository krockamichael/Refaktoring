#include <stdio.h>
#include <stdlib.h>
#include <string.h>

FILE *fr;

int vypis(char s[29][50]){
	int i;
	char *p;

	if((fr = fopen("C:\\Users\\krock\\Desktop\\FIIT\\PP\\Projekt 1\\predaj.txt", "r")) == NULL)          //otvorenie a otestovanie spravneho otvorenia suboru
	printf("Neotvoreny subor\n");
	
	for(i=0;i<29;i++){											//do dvojrozmerneho pola nacitam po riadkoch udaje zo suboru predaj.txt
	printf("meno priezvisko: %s",fgets(s[i],50,fr));
	p = strchr(s[i++], '\n');									//vyhladanie a nasledne odstranenie \n
	if(p) *p = 0;											
	printf("SPZ: %s",fgets(s[i],50,fr));
	p = strchr(s[i++], '\n');
	if(p) *p = 0;
	printf("typ auta: %s",fgets(s[i],50,fr));
	p = strchr(s[i++], '\n');
	if(p) *p = 0;
	printf("cena: %s",fgets(s[i],50,fr));
	p = strchr(s[i++], '\n');
	if(p) *p = 0;
	printf("datum: %s",fgets(s[i],50,fr));
	p = strchr(s[i++], '\n');
	if(p) *p = 0;
	if(i==29) {													//ak je to posledny riadok v subore tak odriadkujem a konci forcyklus
	printf("\n");
	break;}
	else
	printf("%s",fgets(s[i],50,fr));
	}
	rewind(fr); 
}

void odmeny(char s[29][50]){
	int datum_txt[5],i,j=0,dnesny_datum;
	float cena_txt[5],c;
	
	if(s[0][0] != '\0'){									
		scanf("%d",&dnesny_datum);
		for(i=4;i<=28;i+=6,j++){								//konvertuje dnesny datum na int
			sscanf(s[i],"%d",&datum_txt[j]);
		}
		for(j=0,i=3;i<=27;i+=6,j++){							//konvertuje cenu z predaj.txt na float
			sscanf(s[i],"%f",&cena_txt[j]);
		}
		for(i=j=0;i<5;i++,j+=6){             					//s[j] su pozicie v txt subore na ktorom su mena predavajucich, s[j+1] su SPZ, s[j+2] su typy aut (nove/stare)
			if(dnesny_datum-datum_txt[i]>=10000){				//ak je rozdiel datumov vacsi ako 1 rok tak nastane vypis mena, SPZ a odmeny
				if(s[j+2][0]=='1'){								//ak je nove auto dostane 1.5% z ceny ako odmenu
				c=cena_txt[i]/100;
				c*=1.5;
				}	
				else{											//ak stare tak 2.2%
				c=cena_txt[i]/100;
				c*=2.2;
				}
			printf("%s %s %.2f\n",s[j],s[j+1],c);				//vypis mena, SPZ a odmeny
			}
		}
	}
}

void palindrom(char s[29][50]){
	char a[5][7];
	int i,j;
	
	if(s[0][0] == '\0')									//kontrola ci je vytvorene pole otestovanim prveho clena pola
	printf("Pole nie je vytvorene\n");
	else
	for(i=0,j=1;i<5;i++,j+=6){
	strcpy(a[i],s[j]);									//kopirovanie SPZtiek do noveho pola
	strrev(a[i]);										//otocenie SPZ v novom poli
	if(strcmp(a[i],s[j]) == 0)							//porovnanie povodnej SPZ a otocenej SPZ
	printf("%c%c\n",a[i][0],a[i][1]);					//vypis prvych dvoch pismen zo SPZ ktore su palindromami
	}
}

void n(char *x[5]){
	int i,pocet;
	char q;
	
	for(i=0;i<219;i++){							//spocitanie poctu zaznamov v textovom subore predaj.txt
		q=getc(fr);
		if(q=='\n')
		pocet++;
	}
	
	fseek(fr, 11, SEEK_SET);					//nastavenie na poziciu 1. SPZ v textovom subore predaj.txt
	x[0]=(char*)malloc(9*sizeof(char));			
	fgets(x[0],9,fr);							//zapisanie SPZ do pola
	
	fseek(fr, 63, SEEK_SET);					//nastavenie na poziciu 2. SPZ v textovom subore predaj.txt
	x[1]=(char*)malloc(9*sizeof(char));
	fgets(x[1],9,fr);
	
	fseek(fr, 119, SEEK_SET);					//nastavenie na poziciu 3. SPZ v textovom subore predaj.txt
	x[2]=(char*)malloc(9*sizeof(char));
	fgets(x[2],9,fr);
	
	fseek(fr, 165, SEEK_SET);					//nastavenie na poziciu 4. SPZ v textovom subore predaj.txt
	x[3]=(char*)malloc(9*sizeof(char));
	fgets(x[3],9,fr);
	
	fseek(fr, 217, SEEK_SET);					//nastavenie na poziciu 5. SPZ v textovom subore predaj.txt
	x[4]=(char*)malloc(9*sizeof(char));
	fgets(x[4],9,fr);
}

void SPZ(char *x[5],char s[29][50]){
	int i,j;
	
	if(s[0][0]=='\0')									//kontrola ci je vytvorene pole otestovanim prveho clena pola
	printf("Pole nie je vytvorene\n");
	else
	for(i=0;i<5;i++){
		for(j=0;j<8;j++){
		printf("%c",x[i][j]);
		if(j==1 || j==4)
		printf(" ");
		}
	}
}

int z(char *x[5],char s[29][50]){
	int i,BA=0,BL=0,SC=0;
	
	if(s[0][0]=='\0')									//kontrola ci je vytvorene pole otestovanim prveho clena pola
	return 0;
	else{	
	for(i=0;i<5;i++){
		if(x[i][0]=='B' && x[i][1]=='A')
		BA++;
		if(x[i][0]=='S' && x[i][1]=='C')
		SC++;
		if(x[i][0]=='B' && x[i][1]=='L')
		BL++;
	}
	
	if(BA >= 2)
	printf("BA %d\n",BA);
	if(SC >= 2)
	printf("SC %d\n",SC);
	if(BL >= 2)
	printf("BL %d\n",BL);
	}
}

int b(char *x[5],char s[29][50]){
	int i,j,c0=0,c1=0,c2=0,c3=0,c4=0,c5=0,c6=0,c7=0,c8=0,c9=0;
	
	if(s[0][0]=='\0'){
		printf("Pole nie je vytvorene\n");
		return 0;
	}
	
	for(i=0;i<5;i++){
		for(j=0;j<10;j++){
			if(x[i][j]=='0')
			c0++;
			if(x[i][j]=='1')
			c1++;
			if(x[i][j]=='2')
			c2++;
			if(x[i][j]=='3')
			c3++;
			if(x[i][j]=='4')
			c4++;
			if(x[i][j]=='5')
			c5++;
			if(x[i][j]=='6')
			c6++;
			if(x[i][j]=='7')
			c7++;
			if(x[i][j]=='8')
			c8++;
			if(x[i][j]=='9')
			c9++;
		}
	if(i==4 && c0!=0)
	printf("0: %d\n",c0);
	if(i==4 && c1!=0)
	printf("1: %d\n",c1);
	if(i==4 && c2!=0)
	printf("2: %d\n",c2);
	if(i==4 && c3!=0)
	printf("3: %d\n",c3);
	if(i==4 && c4!=0)
	printf("4: %d\n",c4);
	if(i==4 && c5!=0)
	printf("5: %d\n",c5);
	if(i==4 && c6!=0)
	printf("6: %d\n",c6);
	if(i==4 && c7!=0)
	printf("7: %d\n",c7);
	if(i==4 && c8!=0)
	printf("8: %d\n",c8);
	if(i==4 && c9!=0)
	printf("9: %d\n",c9);
	}
}

int main(){
	FILE *fr;
	char c,s[29][50],*x[5];
	
	while(1){    
	if(scanf("%c",&c) <= 0)								//nacitanie znaku a vyvolanie prislusnej funkcie
	break;
	if(c =='v')
		vypis(s);
	if(c =='o')
		odmeny(s);
	if(c =='p')
		palindrom(s);
	if(c =='s')
		SPZ(x,s);
	if(c =='n')
		n(x);
	if(c == 'z')
		z(x,s);
	if(c =='b')
		b(x,s);
	if(c =='k') 
		return 0;
	}
	
	return 0;
}
