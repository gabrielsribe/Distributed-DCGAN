#Gabriel de Souza Ribeiro #Email: g234836@dac.unicamp.br #RA: 234836 #Report ativ-6-exp-1

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