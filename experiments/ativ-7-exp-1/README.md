#Gabriel de Souza Ribeiro #Email: g234836@dac.unicamp.br #RA: 234836 #Report ativ-7-exp-1

#Passos para executar a aplicação de maneira distribuida

#Configurar as maquinas:

#Instalar docker sudo apt-get install
apt-transport-https
ca-certificates
curl
gnupg
lsb-release

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo
"deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update sudo apt-get install docker-ce docker-ce-cli containerd.io

#Clonar o repositorio git clone https://github.com/eborin/Distributed-DCGAN.git

#Baixar os arquivos dentro da posta do projeto mkdir cifar10 && cd cifar10 wget --no-check-certificate https://www.cs.toronto.edu/~kriz/cifar-10-python.tar.gz tar -xvf cifar-10-python.tar.gz

#Construir o container sudo docker build -t dist_dcgan .

Agora temos a imagem configura ja com o container construido.

A partir daqui foi criado um template a partir dessa imagem e foram criadas mais instacias no mesmo Placement Group para melhor performance de rede e VPN (para acesso entre as mesmas)

#Executar a aplicação:
#Obs não esquecer de configurar o master_addr com o ip da instacia que sera utilizada como master Utilizar o batchsize = 16 para evitar problemas de memória Setar o rank das maquinas, rank = 0 = Master Expor a porta 1234

#Nesse experimento será utilizado 1 maquina

#Comando nó master
sudo docker run --env --rm --network=host -p 1234:1234 -v=$(pwd):/root dist_dcgan:latest python -m torch.distributed.launch --nproc_per_node=2 --nnodes=1 --node_rank=0 --master_addr="172.17.0.1" --master_port=1234 dist_dcgan.py --dataset cifar10 --dataroot ./cifar10 --num_epochs 1 --batch_size 16 --max_workers 2