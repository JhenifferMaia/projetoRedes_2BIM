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
            addresses: [192.168.13.130/28] #sempre que criar uma nova VM, some o número 130 por 1. exemplo: 192.168.13.131/28, 192.168.13.132/28...#     
            gateway4: 192.168.13.129          
            dhcp4: false                  
    version: 2 .
    
    3.3 Dê ctrl + x e salve o arquivo, aplique a nova configuração usando: 'sudo netplan apply', e verifique com: 'ifconfig -a'
    
    
    
      CONECTANDO OS PCs
      
      1. Após ter configurado todas VMs nos PCs, vá em configurações da VM e na aba redes mude o 'conectado a' para placa em modo bridge. (Para fazer isso primeiro feche a VM).
      
      2. Assim que todos tiverem conectados teste o ping usando: "ping ip da rede"
      
      
    
    
