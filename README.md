#include <stdio.h>

typedef struct {
    char nome[50];
    int populacao;
    float area;
    float pib;
    int pontosTuristicos;
    float densidadeDemografica;
} Carta;

// Função para comparar os atributos gerais
void comparar(const char *atributo, float valor1, float valor2, const char *nome1, const char *nome2) {
    printf("Comparando atributo: %s\n", atributo);
    printf("%s: %.2f\n", nome1, valor1);
    printf("%s: %.2f\n", nome2, valor2);
    
    if (valor1 > valor2) {
        printf("%s venceu!\n", nome1);
    } else if (valor1 < valor2) {
        printf("%s venceu!\n", nome2);
    } else {
        printf("Empate!\n");
    }
}

// Função para comparar a densidade demográfica (com lógica inversa)
void compararDensidadeDemografica(Carta pais1, Carta pais2) {
    printf("Comparando atributo: Densidade Demográfica\n");
    printf("%s: %.2f\n", pais1.nome, pais1.densidadeDemografica);
    printf("%s: %.2f\n", pais2.nome, pais2.densidadeDemografica);
    
    if (pais1.densidadeDemografica < pais2.densidadeDemografica) {
        printf("%s venceu!\n", pais1.nome);
    } else if (pais1.densidadeDemografica > pais2.densidadeDemografica) {
        printf("%s venceu!\n", pais2.nome);
    } else {
        printf("Empate!\n");
    }
}

int main() {
    Carta pais1 = {"Brasil", 211000000, 8515767.0f, 2055.0f, 500, 25.0f};
    Carta pais2 = {"Alemanha", 83000000, 357022.0f, 4000.0f, 1000, 226.0f};

    int escolha;

    do {
        // Menu interativo
        printf("Escolha o atributo para comparar entre os países:\n");
        printf("1. População\n");
        printf("2. Área\n");
        printf("3. PIB\n");
        printf("4. Número de pontos turísticos\n");
        printf("5. Densidade Demográfica\n");
        printf("0. Sair\n");
        printf("Escolha uma opção: ");
        scanf("%d", &escolha);

        switch (escolha) {
            case 1:
                comparar("População", pais1.populacao, pais2.populacao, pais1.nome, pais2.nome);
                break;
            case 2:
                comparar("Área", pais1.area, pais2.area, pais1.nome, pais2.nome);
                break;
            case 3:
                comparar("PIB", pais1.pib, pais2.pib, pais1.nome, pais2.nome);
                break;
            case 4:
                comparar("Número de pontos turísticos", pais1.pontosTuristicos, pais2.pontosTuristicos, pais1.nome, pais2.nome);
                break;
            case 5:
                compararDensidadeDemografica(pais1, pais2);
                break;
            case 0:
                printf("Saindo...\n");
                break;
            default:
                printf("Opção inválida! Tente novamente.\n");
        }
        
    } while (escolha != 0);

    return 0;
}
