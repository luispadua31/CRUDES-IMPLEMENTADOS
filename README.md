CRUDES-IMPLEMENTADOS

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

float cmp_bebida(){
	int bebida;
	printf("Digite o numero da bebida:\n1.Cerveja\n2.Vodka\n3.Gin\n4.Saque\n5.Absinto\n6.Rum\n7.Tequila\n8.Uisque\n9.Vinho\n10.Cachaca\n11.Jagermeister\n12.Cerveja Especial\n13.Conhaque\n14.Licor\n\n");
	scanf("%d", &bebida);
		switch (bebida){
			case 1:
				return 4;
				break;
			case 2:
				return 40;
				break;
			case 3:
				return 45;
				break;
			case 4:
				return 15;
				break;
			case 5:
				return 69;
				break;
			case 6:
				return 40;
				break;
			case 7:	
				return 42;
				break;
			case 8:
				return 40;
				break;
			case 9:
				return 14;
				break;
			case 10:
				return 45;
				break;
			case 11:
				return 35;
				break;
			case 12:
				return 9;
				break;
			case 13:
				return 32;
				break;
			case 14:
				return 20;
				break;
		}
}


float TAS(){
	int peso, qtd_copos, pm;
	float grau;
	float gramas_alcool_k = 0;
	float TA = 0;
	char resposta[4] = "sim";
	printf("Digite seu peso em kg\n");
	scanf("%d", &peso);
	while((strcmp(resposta, "sim") == 0) || (strcmp(resposta, "Sim") == 0) || (strcmp(resposta, "SIM") == 0)){
		grau = cmp_bebida();
		printf("Grau Alcoolico: %.2f por cento\n", grau);
		printf("quantos copos vc bebeu?\n");
		scanf("%d", &qtd_copos);
		gramas_alcool_k = qtd_copos * grau;
		printf("Pura ou misturada?\n1.Pura\n2.Misturada(Refrigerante, agua, etc.)\n");
		scanf("%d", &pm);
		switch (pm){
			case 1:
			gramas_alcool_k = 0.06 * gramas_alcool_k;
			case 2:
			gramas_alcool_k = 0.058 * gramas_alcool_k;
			TA = TA + (gramas_alcool_k / (peso * 0.7));
		}
		printf("bebeu mais alguma coisa?\n");
		scanf("%s", &resposta);
	}
	return TA;
}

int main(){
	float teor, TA;
	int peso, func;
	int cont_func = 0;
		while(cont_func != 5){
			printf("\nDigite a funcionalidade:\n1. Bebidas e Porcentagem de Alcool\n2. Descubra quanto alcool tem no seu sangue!(TAS)\n3. Em breve!\n");
			scanf("%d", &func);
			switch(func){
				case 1:
					cont_func = 0;
					teor = cmp_bebida();
					printf("Esta bebida possui um teor alcoolico de %.1f por cento\n", teor);
					break;
				case 2:
					cont_func = 0;
					TA = TAS();
					printf("Voce tem %.3f g/L de alcool no seu sangue\n", TA);
					if(TA <= 0.2) printf("Voce ainda ta legal\n");
					else if(0.2 < TA && TA <= 0.7) printf("Voce ja ta ficando meio cego fera... cuidado pra nao pegar um dragao!\n");
					else if(0.7 < TA && TA <= 1.5) printf("Axo q vc ja pegou akele dragao faz tempo...\n");
					else if(1.5 < TA &&TA <= 2.0) printf("Ja ta enxergando dobrado ne... Vai pra casa moleque solto.\n");
					else if(2.0 < TA && TA <= 5.0) printf("Nenem ta dumindo, ta??\n");
					else if(TA > 5.0) printf("No ceu tem pao?? E morreu.\n");
					if(TA/7.5 > 0.05) printf("E voce estaria 1.915 reais mais fudido no bafometro a essa hora!!\n");
					break;
				default:
					printf("\nNao, nao tem essa opcao, seu bebado otario\n");
					cont_func++;
					if(cont_func == 4){
						printf("\nSEU TROXA, MAIS UMA E O APP VAI FEXAR!\n\n");
					}
					else if(cont_func == 5) printf("\nFESSOU!\n\n");
			}
		}
		system("pause");
		return 0;
}
