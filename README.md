TUTORIAL PARA A CRIAÇÃO DE VMs

1. Antes de tudo devemos baixar o Unbutu, nós podemos encontra-lo em https://multipass.run/install (aqui apenas estamos instalando uma image, para conseguir reproduzi-la precisaermos do Virtual Box, encontrado em: https://www.virtualbox.org/wiki/Downloads)

2. Após seguir todos os passos para fazer a instalação do Virtual Box, você precisará criar uma pasta para criar suas VMs (Virtual Machine ou Máquina Virtual).

3. Antes de criar a VM precisaremos baixar a Virtualbox Extension Pack, abra o terminal e digite: sudo apt install virtualbox-ext-pack.

4. Criada as pastas e Virtual Box baixado, você irá abri-lo e criará sua primeira VM.

4.1 Ao entrar você irá encontrar uma aba acima, onde você apertará em arquivo, após abrir as opções você vai em importar Appliance e procurará onde foi alocado o Unbutu, e onde você deseja criar a VM.



4.2 Após abrir o Unbutu, você poderá configurar sua máquina virtual, poderá mudar seu nome, quantidade de memória RAM e de armazenamento que ela irá usar.

4.3 Ao criar, agora é só abrir para que possamos configura-lá.

  CONFIGURANDO as VMs
  
  1. Ao abrir a VM, será solicitado o usuário e a senha, insira para conseguir continuar com o processo.

  2. Agora precisaremos fazer a instalação das ferramentas de rede, será utilizado o comando: 'sudo apt install net-tools -y'.

  3. Precisaremos também acessar o arquivo YAML para configurarmos a interface de rede, digitaremos: 'sudo nano /etc/netplan/01-netcfg.yaml'.

  3.2 Configure dessa forma:
  
        network:
    ethernets:
        enp0s3:                           
            addresses: [192.168.13.130/28] #Olhando a tabela percebe-se que para cada nova VM criada os ultimos digitos do ip mudam sempre somando 1.     
            gateway4: 192.168.13.129          
            dhcp4: false                  
    version: 2 .
  
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
   
   ![image](https://user-images.githubusercontent.com/103265116/186730393-ad5cba15-d5fc-4649-8c7b-f70343414e91.png)

      
    
    
