TUTORIAL PARA A CRIAÇÃO DE VMs

1. Primeiro abriremos o terminal e baixaremos o VirtualBox extension, abriremos a pasta desejada usando 'su redes', e após isso 'sudo apt install virtualbox-ext-pack'

2. Antes de abirir a VirtualBox precisaremos criar uma pasta para armazenar nossas VMs.

3.1 Ao entrar você irá encontrar uma aba acima, onde você apertará em arquivo, após abrir as opções você vai em importar Appliance e procurará onde foi alocado o Unbutu, e onde você deseja criar a VM, assim como configurar a quantidade de memoria que usará e o nome dela (Na tabela 1.0 abaixo você encontrará o nome para as VMs.

![image](https://user-images.githubusercontent.com/103265116/186730672-32c4f316-b993-4cc0-a1f5-fb720cd61853.png)

3.2 Ao criar, agora é só abrir para que possamos configura-lá.

  CONFIGURANDO as VMs
  
  1. Ao abrir a VM, será solicitado o usuário: 'administrador' e a senha: 'adminifal', insira para conseguir continuar com o processo.

  2. Agora precisaremos fazer a instalação das ferramentas de rede, será utilizado o comando: 'sudo apt install net-tools -y'.

  3. Precisaremos também acessar o arquivo YAML para configurarmos a interface de rede, digitaremos: 'sudo nano /etc/netplan/01-netcfg.yaml'.

  3.1 Configure dessa forma:
  
   ![image](https://user-images.githubusercontent.com/103265116/186731248-4f5b2f43-93a8-43e8-a67d-6a7c0869f168.png)

        Tabela 1.0: Definições de endereços IPs da Rede e Nomes de Hosts
    -----------------------------------------------------------------------------------------------------
    |  DESCRICAO  |  IP             |   hostname    |           FQDN                 |       aliase     |
    -----------------------------------------------------------------------------------------------------
    | rede        | 192.168.13.128   |
    | máscara     | 255.255.240.0    |
    | gateway     | 192.168.13.129   |
    | VM1-PC1     | 192.168.13.130   |   vm1-pc1     | vm1-pc1.grupo9-913.ifalara.net |     maiaVM1      |
    | VM2-PC1     | 192.168.13.131   |   vm2-pc1     | vm2-pc1.grupo9-913.ifalara.net |     maiaVM2      |
    | VM1-PC2     | 192.168.13.132   |   vm1-pc2     | vm1-pc2.grupo9-913.ifalara.net |     maiaVM3      |
    | VM2-PC2     | 192.168.13.134   |   vm2-pc2     | vm2-pc2.grupo9-913.ifalara.net |     joaoVM4      |
    | VM1-PC3     | 192.168.13.135   |   vm1-pc3     | vm1-pc3.grupo9-913.ifalara.net |     joaoMV5      |
    | VM2-PC3     | 192.168.13.136   |   vm2-pc3     | vm2-pc3.grupo9-913.ifalara.net |     camiVM6      |
    | VM1-PC4     | 192.168.13.137   |   vm1-pc4     | vm1-pc4.grupo9-913.ifalara.net |     camiVM7      |
    | VM2-PC4     | 192.168.13.138   |   vm2-pc4     | vm2-pc4.grupo9-913.ifalara.net |     grup2        |
    ------------------------------------------------------------------------------------------------------
    
   3.2 Dê ctrl + x e salve o arquivo, aplique a nova configuração usando: 'sudo netplan apply', e verifique com: 'ifconfig -a'
   
   4. Agora nomearemos nossos servidores de acordo com os hostnames da tabela.

   4.1 'Digite: sudo hostnamectl set-hostname <hostname>', de acordo com as VMs e os PCs coloque o respectivo hostname.

   INSTALAÇÃO DOS SOFTWARES
   
   1. Agora precisaremos de softwares para fazermos nossas conexões, primeiro é preciso mudar o dhcp4 para true, comentar as linhas de endereço ip(Só colocar um # na linha) e mudar o Adaptador1 para NAT.

   2. Feito isso, iremos instalar o servidor SSH.
  
   2.1 Primeiro atualize as definições e versões de pacotes/bibliotecas dos repositórios do ubuntu através do comando 'sudo apt update'.
  
   2.2 Agora atualize os pacotes com as novas definições e versões com o comando: 'sudo apt upgrade -y'.
  
   ![image](https://user-images.githubusercontent.com/103265116/186735147-a285b9ad-f7e9-4937-ae85-727ad3f2822f.png)
  
   
   Esses processos podem demorar um pouco, então seja paciente ;p
  
   2.3 Agora instale o SSH server, digite: 'sudo apt-get install openssh-server'.
  
   2.4 Após instalar verifique se está funcionando através do comando: 'systemctl status ssh'.
  
   ![image](https://user-images.githubusercontent.com/103265116/186736697-cd6eaeaa-54e5-467b-8f38-57cdc0004b73.png)
  
   3. Após a intalação do SSH server estiver concluida, iremos configurar o firewall para que conexões via protocolo SSH na porta 22 sejam permitidas.
  
   3.1 Digite o comando: 'sudo ufw allow ssh', para ativar o ssh no firewall UFW do ubuntu.
  
   3.2 Agora ative o firewall através de 'sudo ufw enable'.
  
   3.3 Verifique o status das portas do sistema usando: 'netstat -an | grep LISTEN', as conexões TCP na porta 22 devem estar como LISTENING
  
   ![image](https://user-images.githubusercontent.com/103265116/186738095-5efef6f3-b31d-4a8e-8a31-bf53d776df24.png)
   
     

