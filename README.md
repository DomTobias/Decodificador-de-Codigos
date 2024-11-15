#include <stdio.h>
#include <stdlib.h>

int l, c,k,det;
int vchave[2][2];
int inverter[2][2];
int vmensagem[2][8];
int dec[2][8];
char vet[2][8];

void chave() {

    for (l = 0; l < 2; l++) {
        for (c = 0; c < 2; c++) {
            printf("Digite o numero da Chave Posicao [%d/%d]: ", l + 1, c + 1);
            scanf("%i", &vchave[l][c]);
        }
        printf("\n");
    }
    
    system("cls");

    printf("Matriz Chave:\n");
    for (l = 0; l < 2; l++) {
        for (c = 0; c < 2; c++) {
            printf(" %i ", vchave[l][c]);
        }
        printf("\n");
    }
}

void inverter_chave() {
	
    inverter[0][0] = vchave[1][1];
    inverter[0][1] = vchave[0][1] *-1;
    inverter[1][0] = vchave[1][0] *-1;
    inverter[1][1] = vchave[0][0];

    printf("Matriz Chave invertida:\n");
    for (l = 0; l < 2; l++) {
        for (c = 0; c < 2; c++) {
            printf(" %i ", inverter[l][c]);
        }
        printf("\n");
    }
}

void determinante(){
	
	det = (inverter[0][0] * inverter[1][1]) - (inverter[0][1] * inverter[1][0]);
	
	printf("Determinante \n %i \n\n",det);
}

void matriz_mensagem(){
	for(l=0;l<2;l++){
		for(c=0;c<8;c++){
			printf("Digite a Matriz Mensagem [%d/%d]: ",l+1,c+1);
			scanf("%i",&vmensagem[l][c]);
		}
	}
	
	system("cls");
	
	
}

void decodificando(){
	for (l = 0; l < 2; l++) {
	    for (c = 0; c < 8; c++) {
	        for(k=0;k<2;k++){
					dec[l][c] = (dec[l][c] + inverter[l][k] * vmensagem[k][c]);
	        }
	    }
	}
}



void mensagem(){
		
	for (l = 0; l < 2; l++) {
        for (c = 0; c < 8; c++) {
            switch (dec[l][c] / det) {
                case 1:
                    vet[l][c] = 'A';
                    break;
                case 2:
                    vet[l][c] = 'B';
                    break;
                case 3:
                    vet[l][c] = 'C';
                    break;
                case 4:
                    vet[l][c] = 'D';
                    break;
                case 5:
                    vet[l][c] = 'E';
                    break;
                case 6:
                    vet[l][c] = 'F';
                    break;
                case 7:
                    vet[l][c] = 'G';
                    break;
                case 8:
                    vet[l][c] = 'H';
                    break;
                case 9:
                    vet[l][c] = 'I';
                    break;
                case 10:
                    vet[l][c] = 'J';
                    break;
                case 11:
                    vet[l][c] = 'K';
                    break;
                case 12:
                    vet[l][c] = 'L';
                    break;
                case 13:
                    vet[l][c] = 'M';
                    break;
                case 14:
                    vet[l][c] = 'N';
                    break;
                case 15:
                    vet[l][c] = 'O';
                    break;
                case 16:
                    vet[l][c] = 'P';
                    break;
                case 17:
                    vet[l][c] = 'Q';
                    break;
                case 18:
                    vet[l][c] = 'R';
                    break;
                case 19:
                    vet[l][c] = 'S';
                    break;
                case 20:
                    vet[l][c] = 'T';
                    break;
                case 21:
                    vet[l][c] = 'U';
                    break;
                case 22:
                    vet[l][c] = 'V';
                    break;
                case 23:
                    vet[l][c] = 'W';
                    break;
                case 24:
                    vet[l][c] = 'X';
                    break;
                case 25:
                    vet[l][c] = 'Y';
                    break;
                case 26:
                    vet[l][c] = 'Z';
                    break;
                case 27:
                    vet[l][c] = ' ';
                    break;
                default:
                    printf("Valor inválido! l=%d c=%d\n", l, c);
                    vet[l][c] = '?'; 
                    break;
            }
        }
    }

	

}

void exibir(){
	
	printf("Matriz Chave:\n");
	for (l = 0; l < 2; l++) {
	    for (c = 0; c < 2; c++) {
	            printf(" %i ", vchave[l][c]);
	        }
	        printf("\n");
	    }
	
	printf("\n\n");
	
	printf("Matriz Chave invertida:\n");
    for (l = 0; l < 2; l++) {
        for (c = 0; c < 2; c++) {
            printf(" %i ", inverter[l][c]);
        }
        printf("\n");
    }
    
    printf("\n\n");

    printf("Determinante \n %i",det);
    
    printf("\n\n");
	
	printf("Matriz Mensagem: \n");
	for(l=0;l<2;l++){
		for(c=0;c<8;c++){
			printf(" %i ",vmensagem[l][c]);
		}
		printf("\n");
	}
	
	printf("\n\n");

	printf("Mensagem Codificada:\n");
    for (l = 0; l < 2; l++) {
        for (c = 0; c < 8; c++) {
            printf(" %i ", dec[l][c]/det);
        }
        printf("\n");
    }
    
    printf("\n\n");

    printf("Mensagem: \n");
    for(l=0;l<2;l++){
		for(c=0;c<8;c++){
			printf(" %c ",vet[l][c]);
		}
		printf("\n");
	}
	
}

int main() {
	
    chave();
    printf("\n");
    inverter_chave();
    printf("\n");
    determinante();
    matriz_mensagem();
    decodificando();
    mensagem();
    exibir();

    return 0;
}
