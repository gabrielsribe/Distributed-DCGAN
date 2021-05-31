# Gabriel de Souza Ribeiro #Email: g234836@dac.unicamp.br #RA: 234836 #Report ativ-8-exp-1


# Objetivo
O objetivo dessa atividade é automatizar a criação e utilização de recursos computacionais na nuvem da AWS utilizando para isso a ferramenta Clap
A ferramenta clapp e como configura-la pode ser encontrada em: https://github.com/lmcad-unicamp/CLAP


# Configurações para o experimento
As configurações de Providers, logins, instances, clusters e roles podem ser encontradas dentro da pasta ./clap
Para que o Clap consiga instanciar as máquinas e rodar os comandos precisaremos de alguns arquivos que irão respectivamente em:
-> logins:
    -> keypair_public_file: Public key criado a partir da chave privada do AWS Console
    -> keypair_private_file: Chava privada gerada no AWS Console
-> Providers:
    -> access_kefile: Access Key ID da conta AWS
    -> secret_access_keyfile: Secret Key da conta AWS


# Experimentos
Para a validação do experimento serão utilizados três cenários:
-> cluster-t2.small-1x: Um cluster com uma máquina t2.small.
-> cluster-t2.small-2x: Um cluster com duas máquinas t2.small.
-> cluster-t2.small-4x: Um cluster com quatro máquinas t2.small.

É importante ressaltar que foi limitado o numero de Paramount iterations foi limitada a 20, para otimizar o tempo gasto no experimento


## Rodando o experimento



# Resultados