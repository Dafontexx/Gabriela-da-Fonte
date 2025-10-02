/*
Projeto: Plataforma de Engajamento Social
Curso: Análise e Desenvolvimento de Sistemas
Líder de projeto: Gabriel Albuquerque N. de Oliveira
Integrantes:
*/

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <locale.h>
#include "oscs.h"

// Função de logotipo(***PONTO A MELHORAR***)
void mostrarLogo(void)
{
printf(".====================================================================.\n");
printf("! !\n");
printf("! ||||||| |||||| |||||| || ||||| || || |||| || || || !\n");
printf("! || || || || || || || || || || || || || || !\n");
printf("! ||||||| || || || || ||||||| || || || || || || || !\n");
printf("! || || || || || || || || || || |||| || || !\n");
printf("! ||||||| |||||| |||||| || || || ||||||| || || ||| || || !\n");
printf("! !\n");
printf("! !\n");
printf("! Plataforma de Engajamento Social Integrado (P.E.S.I.) !\n");
printf("! !\n");
printf("! Bem-vindo à transformação digital do engajamento! !\n");
printf("! Conectando ideias, pessoas e propósitos com inteligência. !\n");
printf(".====================================================================.\n");
printf("\n"); // ou manter a que está, adicionando esse comando
}

// Testar com essa alteração (Gabriela)
void mostrarLogo(void)
{
printf("\n");
printf(" .==============================================================.\n");
printf(" ! !\n");
printf(" ! ||||||| |||||| |||||| || ||||| || || |||| || !\n");
printf(" ! || || || || || || || || || || || || !\n");
printf(" ! ||||||| || || || || ||||||| || || || || || !\n");
printf(" ! || || || || || || || || || || |||| !\n");
printf(" ! ||||||| |||||| |||||| || || || ||||||| || || ||| !\n");
printf(" ! !\n");
printf(" ! Plataforma de Engajamento Social Integrado (P.E.S.I.) !\n");
printf(" ! Bem-vindo à transformação digital do engajamento! !\n");
printf(" .==============================================================.\n");
printf("\n");
}

int main()
{

setlocale(LC_ALL, "pt-BR"); // Configura acentuação (Não está aceitando**Resolver problema**)
const *arquivo = "dados.txt";
// Variáveis de seleção e controle.
int selecao;
bool cont = true;

// Ver se deste modo aceita para resolver o problema
const char *arquivo = "dados.txt";
// OU, se você for modificá-lo:
// char arquivo[] = "dados.txt";

mostrarLogo();

// Estrutura de loop para o menu.
do
{

printf("\nSelecione uma opcao:\n\n1. Cadastro de OSCs\n2. Cadastro de Usuários\n3. Registro de Ações por OSCs\n4. Listagem de Ações\n5. Inscrição de Usuários em Ações\n6. Visualização de Participantes por Ação\n0. Sair\nDigite o número da opção desejada: ");
scanf("%d", &selecao);

switch (selecao)
{
case 1: // Cadastro de OSCs

//Preparar para escolha entre cadastro PF ou PJ
cadastrarPessoaFisica(arquivo);
cadastrarPessoaJuridica(arquivo);
system("pause");

break;

case 2: // Cadastro de usuários
printf("teste 2 ok"); // Arquivo da função oscs.c/h
break;
case 3: // Registro de ações por OSCs

printf("teste 3 ok"); // Arquivo da função oscs.c/h
break;
case 4: // Listagem das ações

printf("teste 4 ok"); // Arquivo da função database.c/h
break;
case 5: // Inscrição de usuários em ações

printf("teste 5 ok"); // Arquivo da função database.c/h
break;
case 6: // Vizualização de participantes por ação

printf("teste 6 ok"); // Arquivo da função database.c/h
break;

case 0: // Finaliza o programa

printf("Finalizando sistema...");
cont = false;
break;

default:

printf("Opcao invalida!\nTente novamente");
break;
}

} while (cont != false); // O loop se rompe quando a variavel for falsa;

return 0;
}

// SUPOSTA ALTERAÇÃO 
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <locale.h>
#include "oscs.h"

// ... (Função mostrarLogo) ...

int main()
{

// Configura acentuação e tenta forçar o uso de UTF-8 (útil no Windows)
setlocale(LC_ALL, "pt-BR"); 
system("chcp 65001"); 
// Declaração da string corrigida
const char *arquivo = "dados.txt"; 
// Variáveis de seleção e controle.
int selecao;
bool cont = true;

mostrarLogo();

// Estrutura de loop para o menu.
do
{
printf("\n====================================================================\n");
printf("Selecione uma opcao:\n\n");
printf("1. Cadastro (OSCs/Usuarios)\n");
printf("2. Registro de Ações por OSCs\n");
printf("3. Listagem de Ações\n");
printf("4. Inscrição de Usuários em Ações\n");
printf("5. Visualização de Participantes por Ação\n");
printf("0. Sair\n");
printf("====================================================================\n");
printf("Digite o número da opção desejada: ");
if (scanf("%d", &selecao) != 1) {
// Lidar com input inválido (não-numérico)
printf("Entrada invalida. Por favor, digite um numero.\n");
while (getchar() != '\n'); // Limpa buffer
continue; // Volta ao início do loop
}
while (getchar() != '\n'); // Limpa o buffer após o scanf

switch (selecao)
{
case 1: // Cadastro de OSCs ou Usuários (Sub-menu sugerido)

printf("\nOpcoes de Cadastro:\n1. Cadastrar OSC (Pessoa Juridica)\n2. Cadastrar Usuario (Pessoa Fisica)\nDigite a opcao: ");
int tipo_cadastro;
if (scanf("%d", &tipo_cadastro) == 1) {
while (getchar() != '\n'); // Limpa buffer
if (tipo_cadastro == 1) {
cadastrarPessoaJuridica(arquivo); 
} else if (tipo_cadastro == 2) {
cadastrarPessoaFisica(arquivo);
} else {
printf("Opcao invalida para o cadastro.\n");
}
} else {
printf("Entrada invalida.\n");
while (getchar() != '\n');
}

printf("\nPressione ENTER para continuar...");
getchar(); // Substitui system("pause")

break;
// Ajuste os cases 2, 3, 4, 5, 6 se você mudou a ordem do menu
case 2: 
printf("Registro de acoes ok\n"); 
break;
// ... (resto dos cases 3 a 5) ...

case 0: // Finaliza o programa

printf("Finalizando sistema...");
cont = false;
break;

default:
printf("Opcao invalida! Tente novamente\n");
break;
}

} while (cont); // 'while (cont)' é mais idiomático que 'while (cont != false)'

return 0;
}


