#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define NUM_CARTAS 5

typedef struct {
    char nome[30];
    int  ataque;
    int  defesa;
    int  velocidade;
} Carta;

void imprimirMenu() {
    printf("Menu\n");
    printf("1 - ataque\n");
    printf("2 - defesa\n");
    printf("3 - velocidade\n");
    printf("0 - Sair\n");
}

#include <stdio.h>

#define NUM_CARTAS 5

typedef struct {
    char nome[20];
    int ataque;
    int defesa;
    int velocidade;
} Carta;

void imprimirMenu() {
    printf("1. Comparar Ataque\n");
    printf("2. Comparar Defesa\n");
    printf("3. Comparar Velocidade\n");
    printf("0. Sair\n");
}

void compararCartas(Carta carta1, Carta carta2, int atributo) {
    switch (atributo) {
        case 1:
            if (carta1.ataque > carta2.ataque) {
                printf("%s vence com ataque %d contra %d\n", carta1.nome, carta1.ataque, carta2.ataque);
            } else if (carta1.ataque < carta2.ataque) {
                printf("%s vence com ataque %d contra %d\n", carta2.nome, carta2.ataque, carta1.ataque);
            } else {
                printf("Empate em ataque!\n");
            }
            break;
        case 2:
            if (carta1.defesa > carta2.defesa) {
                printf("%s vence com defesa %d contra %d\n", carta1.nome, carta1.defesa, carta2.defesa);
            } else if (carta1.defesa < carta2.defesa) {
                printf("%s vence com defesa %d contra %d\n", carta2.nome, carta2.defesa, carta1.defesa);
            } else {
                printf("Empate em defesa!\n");
            }
            break;
        case 3:
            if (carta1.velocidade > carta2.velocidade) {
                printf("%s vence com velocidade %d contra %d\n", carta1.nome, carta1.velocidade, carta2.velocidade);
            } else if (carta1.velocidade < carta2.velocidade) {
                printf("%s vence com velocidade %d contra %d\n", carta2.nome, carta2.velocidade, carta1.velocidade);
            } else {
                printf("Empate em velocidade!\n");
            }
            break;
        default:
            printf("Atributo inválido!\n");
            break;
    }
}

int main() {
    Carta cartas[NUM_CARTAS] = {
        {"Carta 1", 80, 70, 60},
        {"Carta 2", 75, 85, 65},
        {"Carta 3", 90, 60, 70},
        {"Carta 4", 70, 75, 80},
        {"Carta 5", 85, 80, 75}
    };

    int escolha;
    do {
        imprimirMenu();
        printf("Digite sua escolha: ");
        scanf("%d", &escolha);

        if (escolha > 0 && escolha <= 3) {
            int carta1, carta2;
            printf("Escolha a primeira carta (0 a %d): ", NUM_CARTAS - 1);
            scanf("%d", &carta1);
            printf("Escolha a segunda carta (0 a %d): ", NUM_CARTAS - 1);
            scanf("%d", &carta2);

            if (carta1 >= 0 && carta1 < NUM_CARTAS && carta2 >= 0 && carta2 < NUM_CARTAS) {
                compararCartas(cartas[carta1], cartas[carta2], escolha);
            } else {
                printf("Escolha de carta inválida!\n");
            }
        } else if (escolha != 0) {
            printf("Escolha inválida! Tente novamente.\n");
        }
    } while (escolha != 0);

    printf("Saindo do jogo...\n");
    return 0;
}
