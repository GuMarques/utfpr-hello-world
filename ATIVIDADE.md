# Isso é um titulo em H1
## Isso é um subtitulo em H2

Vou mostrar um código que criei hoje na aula de Algoritmos 2:

'''C
    #include <stdio.h>
    #include <stdlib.h>

    typedef struct {
        int codigo_cliente;
        char nome_cliente[100];
    }Clientes;

    typedef struct {
        int num_conta;
        int codigo_cliente;
        int valor_compra;
    }Contas;

    int main(int argc, char const *argv[])
    {
        Clientes cliente[10];
        Contas conta[10];
        int menu;
        int totalclientes = 0;
        int totalcontas = 0;
        while(menu != 0) {
            system("clear");
            printf("Menu\n");
            printf("1 - Incluir Cliente\n");
            printf("2 - Incluir Conta\n");
            printf("0 - Sair\n");
            printf("Entre com o numero da opcao desejada: ");
            scanf("%d", &menu);

            if(menu == 1) { //
                int flag = 0;
                int codigo_provisorio;
                printf("Codigo do Cliente: ");
                scanf("%d", &codigo_provisorio);
                for(int i = 0; i < totalclientes; i++) {
                    if(codigo_provisorio == cliente[i].codigo_cliente) {
                        printf("Cliente ja cadastrado\n");
                        getchar();
                        flag = 1;
                        break;
                    }
                }
                if(flag == 0) {
                    cliente[totalclientes].codigo_cliente = codigo_provisorio;
                    printf("Nome do Cliente: ");
                    setbuf(stdin, NULL);
                    fgets(cliente[totalclientes].nome_cliente, 100, stdin);
                    totalclientes++;
                }
                menu = 3;
            }

            if(menu == 2) { //
                int flag = 0;
                int codigo_provisorio;
                printf("Codigo do Cliente: ");
                scanf("%d", &codigo_provisorio);
                for(int i = 0; i < totalclientes; i++) {
                    if(codigo_provisorio == cliente[i].codigo_cliente) {
                        flag = 1;
                        break;
                    }
                }
                if(flag == 1) {
                    conta[totalcontas].codigo_cliente = codigo_provisorio;
                    printf("Numero da conta: ");
                    scanf("%d", &conta[totalcontas].num_conta);
                    printf("Valor da compra: ");
                    scanf("%d", &conta[totalcontas].valor_compra);
                    totalcontas++;
                }
                else printf("Cliente nao cadastrado\n");
                menu = 3;
            }
        }

        return 0;
    }
'''

Esse código gera um **menu** rudimental que tem **duas** restrições:

* Primeiro: Dois clientes não podem ter o mesmo codigo_cliente
* Segundo: Uma compra não pode ser efutuada se o cliente não for cadastrado anteriormente