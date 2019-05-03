#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <locale.h>

//variáveis globais para os swicht's
int m;

//struct's globais
struct ficha_aluno
{
    char nome[50];
    char cpf[12];
    char rg[14];
    char pai[50];
    char mae[50];
    char curso[50];
    int idade;

}cadastro;

void menuprincipal()
{
    printf("\t\t------------------------------=============================\n");
    printf("\t\tINSTITUTO FEDERAL DE EDUCAÇÃO CIÊNCIA E TECNOLOGIA DO CEARÁ\n");
    printf("\t\t==============================Campus Quixadá---------------\n\n");

    printf("1 - Cadastro de aluno\n");
    printf("2 - Listar alunos\n");
    printf("3 - Alterar cadastro\n");
    printf("4 - Remover todos os cadastros\n");
    printf("5 - Sair\n");
    scanf("%i",&m);
}


int main()
{
     FILE*alunos;
     //variáveis para as funções de retorno
     int p,q,z,i;
     //variável lógicas
     int logico, logico2;

     char url[]="alunos.txt", info[50];

     setlocale(LC_ALL,"");

     do
     {
     system ("cls");
     menuprincipal();

     switch (m)
     {
     case 1:
        do
        {
        system ("cls");
        printf("\t\t\t----====\n");
        printf("\t\t\tCadastro\n");
        printf("\t\t\t====----\n\n");

        fflush(stdin);
        printf("Nome: ");
        fgets(cadastro.nome,50,stdin);
        fflush(stdin);
        printf("CPF: ");
        fgets(cadastro.cpf,12,stdin);
        fflush(stdin);
        printf("Rg: ");
        fgets(cadastro.rg,14,stdin);
        fflush(stdin);
        printf("Idade: ");
        scanf("%i",&cadastro.idade);
        fflush(stdin);
        printf("Curso: ");
        fgets(cadastro.curso,50,stdin);
        fflush(stdin);
        printf("Pai: ");
        fgets(cadastro.pai,50,stdin);
        fflush(stdin);
        printf("Mãe: ");
        fgets(cadastro.mae,50,stdin);

        //abrindo arquivo
        alunos = fopen("alunos.txt","a+");
        //testando a validade do arquivo
        if (alunos!=NULL)
        {
            system("cls");
            fflush(stdin);
            fprintf(alunos,"-------------------------------\n");
            fflush(stdin);
            fprintf(alunos,"Nome: %s",cadastro.nome);
            fflush(stdin);
            fprintf(alunos,"CPF: %s\n",cadastro.cpf);
            fflush(stdin);
            fprintf(alunos,"RG: %s\n",cadastro.rg);
            fflush(stdin);
            fprintf(alunos,"Idade: %i\n",cadastro.idade);
            fflush(stdin);
            fprintf(alunos,"Curso: %s",cadastro.curso);
            fflush(stdin);
            fprintf(alunos,"Pai: %s",cadastro.pai);
            fflush(stdin);
            fprintf(alunos,"Mãe: %s",cadastro.mae);
            fprintf(alunos,"-------------------------------\n\n");
        }
        else
        {
            printf("Falha na abertura do arquivo");
        }

        fclose(alunos);
        printf("\n\n Dados gravados com sucesso!\n\n");
        system("pause");

        do
        {
        system("cls");
        printf("Deseja realizar um novo cadastro?\nSim(1) Não(2)\n");
        scanf("%i",&logico2);

        if(logico2==1)
        {
            q=1;
        }
        else
        {
            if(logico2==2)
            {
                z=0;
                q=0;
                p=1;
            }
            else
            {
                printf("Comando inválido!\n");
                system("pause");
                z=1;
            }
        }
        }while(z==1);

        }while(q==1);

        break;
     case 2:

         alunos = fopen("alunos.txt","r");
         if(alunos==NULL)
         {
             printf("Erro na abertura do arquivo!\n");
             system("pause");
             p=1;
         }
         else
         {
             while( (fgets(info, sizeof(info), alunos))!=NULL )
             printf("%s", info);
             while( (fgets(info, sizeof(info), alunos))!=NULL )
             printf("%s", info);
             while( (fgets(info, sizeof(info), alunos))!=NULL )
             printf("%s", info);
             while( (fgets(info, sizeof(info), alunos))!=NULL )
             printf("%s", info);
             while( (fgets(info, sizeof(info), alunos))!=NULL )
             printf("%s", info);
             while( (fgets(info, sizeof(info), alunos))!=NULL )
             printf("%s", info);
             while( (fgets(info, sizeof(info), alunos))!=NULL )
             printf("%s", info);
             while( (fgets(info, sizeof(info), alunos))!=NULL )
             printf("%s", info);

         }
         system("pause");
         p=1;
        break;

     case 3:
        break;
     case 4:
        do
        {
        system("cls");
        printf("Deseja apagar todos os cadastros?\nsim(1) não(2)\n");
        scanf("%i",&logico);

        if (logico==1)
        {
            alunos = fopen("alunos.txt","w");

            if(alunos==NULL)
            {
                system("cls");
                printf("Erro na abertura do arquivo!\n");
                p=1;
            }
            else
            {
                system("cls");
                printf("Dados apagados com sucesso!\n");
            }
            fclose(alunos);
            system("pause");
            p=1;
        }
        else
        {
            if(logico==2)
            {

                i=0;
                p=1;

            }
            else
            {

            system("cls");
            printf("Comando inválido!\n");
            system("pause");
            i=1;
            }
        }
        }while(i==1);

        break;
     case 5:
        system("cls");
        printf("Sessão encerrada!\n");
        p=0;
        break;
     default:
        system("cls");
        printf("Comando inválido! \n");
        system ("pause");
        p=1;
        break;
     }
     }while(p==1);
return 0;
}
