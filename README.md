TUTORIAL PARA A CRIAÇÃO DE VMs

1. Primeiro abriremos o terminal e baixaremos o VirtualBox extension, abriremos a pasta desejada usando 'su redes', e após isso 'sudo apt install virtualbox-ext-pack'

2. 

4.1 Ao entrar você irá encontrar uma aba acima, onde você apertará em arquivo, após abrir as opções você vai em importar Appliance e procurará onde foi alocado o Unbutu, e onde você deseja criar a VM, assim como configurar a quantidade de memoria que usará e o nome dela.

![image](https://user-images.githubusercontent.com/103265116/186730672-32c4f316-b993-4cc0-a1f5-fb720cd61853.png)

4.3 Ao criar, agora é só abrir para que possamos configura-lá.

  CONFIGURANDO as VMs
  
  1. Ao abrir a VM, será solicitado o usuário e a senha, insira para conseguir continuar com o processo.

  2. Agora precisaremos fazer a instalação das ferramentas de rede, será utilizado o comando: 'sudo apt install net-tools -y'.

  3. Precisaremos também acessar o arquivo YAML para configurarmos a interface de rede, digitaremos: 'sudo nano /etc/netplan/01-netcfg.yaml'.

  3.2 Configure dessa forma:
  
   ![image](https://user-images.githubusercontent.com/103265116/186731248-4f5b2f43-93a8-43e8-a67d-6a7c0869f168.png)

        Tabela: Definições de endereços IPs da Rede e Nomes de Hosts
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
    
   3.3 Dê ctrl + x e salve o arquivo, aplique a nova configuração usando: 'sudo netplan apply', e verifique com: 'ifconfig -a'
    
    
    
   CONECTANDO OS PCs
      
   1. Após ter configurado todas VMs nos PCs, vá em configurações da VM e na aba redes mude o 'conectado a' para placa em modo bridge. (Para fazer isso primeiro feche a VM).
      
   2. Assim que todos tiverem conectados teste o ping usando: "ping ip da rede"

      
    
    
