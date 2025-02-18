# Calendario.bat
## Introdução
Nesse trabalho em `Arquivo.bat` criei um calendário em forma de programação, além disso consegui fazer a verificação se o ano é bissexto, e mudar a contagem de dias do mês de fevereiro, de 28 para 29 dias, e ainda mais prever quando será o proximo ano bissexto.

![Descrição da Imagem](https://res.cloudinary.com/little-league/image/upload/c_limit,dpr_auto,w_1536,q_auto,c_fill,g_face/v1520559381/calendar-660670_1920.jpg)

## Agora vou explicar algumas coisas que aprendi no processo

>`%1 e %2` Esse comando indentifica os parametros por ordem.

>`set /a "resto=%1 + 4"` Defini uma variavel e atribui uma conta a ela.

>`If e Else` Tive aprender como atribui-la para definir se o ano é bissexto ou não.

>`if "%2" == "2" set dias=%dias_fevereiro%` Defini que se o segundo parametro for igual a 2, defino os dias igual a variavel **dias_fevereiro** que não possui valor fixo, pois muda de acordo com o ano.

>`for /l %%i in (1,1,%dias%) do (` Aqui defini um loop para automatizar a criação das pastas dos dias de acordo com o mês. Exemplo, se o mes for 2, será adicionado automaticamete 28 ou 29 pastas dentro do mesmo.

## Código
``` bat 
@echo off
:: verifica se o mes é um numero de 1 a 12
if %2 gtr 12 (
    echo O mes deve ser um numero entre 1 e 12
    exit /b
)
:: cria um parametro
if not exist "%1" (
    mkdir "%1"
)
:: verifica se o ano é bissexto
set /a "resto=%1 %% 4"
set /a "resto100=%1 %% 100"
set /a "resto400=%1 %% 400"
set /a "conta = %1+4"

if %resto%==0 (
    if %resto100%==0 (
        if %resto400%==0 (
            set dias_fevereiro=29
        ) else (
        set dias_fevereiro=28
        echo nao e
        )
    ) else (
        set dias_fevereiro=29
        echo o proximo ano bissexto e %conta%
    )
) else (
    set dias_fevereiro=28
    echo nao e
)
:: entra no parametro
cd "%1"
:: cria outro parametro
if not exist "%2" (
    mkdir "%2"
)
cd "%2"
:: definindo dias para cada mes
if "%2" == "1" set dias=31
if "%2" == "2" set dias=%dias_fevereiro%
if "%2" == "3" set dias=31
if "%2" == "4" set dias=30
if "%2" == "5" set dias=31
if "%2" == "6" set dias=30
if "%2" == "7" set dias=31
if "%2" == "8" set dias=31
if "%2" == "9" set dias=30
if "%2" == "10" set dias=31
if "%2" == "11" set dias=30
if "%2" == "12" set dias=31
:: verifica se o numero de dias corresponde ao mes
echo o numero de dias do mes %2 e %dias%
:: faz a contagem de um a um em cada mes
for /l %%i in (1,1,%dias%) do (
    if not exist "Dia %%i" (
        mkdir "Dia %%i"
    )
)
:: volta tudo
cd ..
cd .. 
```
## Parte por parte 
```
@echo off
:: verifica se o mes é um numero de 1 a 12
if %2 gtr 12 (
    echo O mes deve ser um numero entre 1 e 12
    exit /b
```
Inicialmente ele faz a verificação se o numero é entre 1 a 12 se for maior ele aparece a mensagem "O mes deve ser um numero de 1 e 12", já o **exit /b** serve para encerrar o codigo.
```
:: cria um parametro
if not exist "%1" (
    mkdir "%1"
```
A criação de um parametro serve para deixa eles em ordem.
```
:: verifica se o ano é bissexto
set /a "resto=%1 %% 4"
set /a "resto100=%1 %% 100"
set /a "resto400=%1 %% 400"
set /a "conta = %1+4"

if %resto%==0 (
    if %resto100%==0 (
        if %resto400%==0 (
            set dias_fevereiro=29
        ) else (
        set dias_fevereiro=28
        echo nao e
        )
    ) else (
        set dias_fevereiro=29
        echo o proximo ano bissexto e %conta%
    )
) else (
    set dias_fevereiro=28
    echo nao e
)
```
Aqui fica a explicação do ano bissexto, para verificar se é temos que dividir por 4, 100 ou 400, apos isso verifica o resto da divisão, assim mudando o mes de fevereiro entre 28 e 29 dias.
```
:: definindo dias para cada mes
if "%2" == "1" set dias=31
if "%2" == "2" set dias=%dias_fevereiro%
if "%2" == "3" set dias=31
if "%2" == "4" set dias=30
if "%2" == "5" set dias=31
if "%2" == "6" set dias=30
if "%2" == "7" set dias=31
if "%2" == "8" set dias=31
if "%2" == "9" set dias=30
if "%2" == "10" set dias=31
if "%2" == "11" set dias=30
if "%2" == "12" set dias=31
```
Aqui foi definido a quantidade de dias para cada mes.
```
:: verifica se o numero de dias corresponde ao mes
echo o numero de dias do mes %2 e %dias%
:: faz a contagem de um a um em cada mes
for /l %%i in (1,1,%dias%) do (
    if not exist "Dia %%i" (
        mkdir "Dia %%i"
    )
)
```
Verifica se a quantidade de dias esta certa relacionada ao mes, e tambem, faz a contagem de um a um de cada mes.
```
:: volta tudo
cd ..
cd .. 
```
volta tudo.
## Final
Fazer e entender essa programação não foi facil, mas no final entendi ela por completo, e tive novos apendizado de funções novas no cmd, e como melhoria trocaria a indentificação dos meses, que ao inves de representalos por números os representaria por seus respectivos nomes ex(janeiro, fevereiro).




