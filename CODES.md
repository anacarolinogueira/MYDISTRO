

## COMANDOS RODADOS
### COMPILAÇÃO KERNEL  

Cria um diretório para sua distro e entra nele: 
```text
mkdir Distro; cd Distro
```
Criação do arquio raiz da distribuição( Diretório principal - /):
```text
mkdir rootfs
```
Agora se o seus Downloads vao para a pasta Downloads do seu computador, será necessário mover o arquivo de instalação do kernel para a pasta Distro.
Para isso irei criar uma variável na qual leva para a pasta da minha distribução.
Dentro da pasta irei digitar o comando que mostra o caminho para o diretório atual: 
```text
pwd
```
Saida: `/home/ana/Distro` 

Criação da variável: 
```text
DISTRO=/home/ana/Distro
```
Mostra o que tem dentro da variável:
```text
echo $DISTRO
```
Agora pode seguir com a instalação.

Instala as ferramentas necessárias para compilar o Kernel do Linux, criar uma imagem de sistema operacional customizada e configurar um ambiente de emulação e boot):
```text
sudo apt update && sudo apt install -y \
    build-essential \
    libncurses-dev \
    bison \
    flex \
    libssl-dev \
    libelf-dev \
    bc \
    cpio \
    wget \
    xorriso \
    grub-pc-bin \
    grub-efi-amd64-bin \
    grub-common \
    mtools \
    squashfs-tools \
    qemu-system-x86
```
SIGNIFICADO DOS COMANDOS PARA COMPILAR O KERNEL: 
- `build-essential/` : instala o gcc (compilador de C), g++ (compilador de C++) e o make.
- `libncurses-dev/` : instala o o comando make menuconfig.
- `bison & flex/` : geradores de analisadores sintáticos. O Kernel precisa deles para entender a estrutura dos seus próprios arquivos de configuração durante a montagem.
- `libssl-dev/` : ferramentas de segurança e criptografia (SSL/TLS).
- `libelf-dev/` : permite que o sistema manipule arquivos ELF (o formato padrão de executáveis e bibliotecas do Linux).
- `bc/` : uma calculadora de linha de comando. O processo de compilação do Kernel faz algumas contas matemáticas internas de tempo e memória e usa o bc para isso.

EMPACOTAR O KERNEL: 
- `cpio/` : cria o initramfs.
- `wget/` : baixar os arquivos diretamente da internet.
- `tar & xz-utils/` : ferramentas para descompactar arquivos.
- `squashfs-tools/` : cria sistemas de arquivos altamente compactados e de "apenas leitura".
- `xorriso/` : cria, manipula e queima imagens ISO. Usado para transformar o Kernel em umsistema bootavel.
- `grub-pc-bin & grub-efi-amd64-bin & grub-common/` : instalam os arquivos do GRUB.
- `mtools/` : conjunto de ferramentas para manipular arquivos de sistemas de arquivos MS-DOS (como FAT32) sem precisar montá-los.
- `qemu-system-x86/` : cria um emulador e máquina virtual.

Baixa os arquivos diretamente da internet:
```text
sudo wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.18.38.tar.xz
```
Ou voçê pode entrar diretamente no site kernel.org e baixar o arquivo 6.18.38 por lá, clicando em tarball (baixa o arquivo .tar).
### NO DIRETÓRIO DOCUMENTS 
Pega o arquivo baixado e copia e cola na pasta da distro:
```text
cp linux-6.18.38.tar.xz $DISTRO
```
### NO DIRETÓRIO DISTRO
Comando para extrair o arquivo baixado:
```text
sudo tar -xvf linux-6.1.60.tar.xz
```
- `-x` (Extract): Diz ao programa para descompactar o arquivo.
- `-v`(Verbose): Modo "falado". Mostra na tela a lista de arquivos sendo extraídos em tempo real.
- `-f`(File): Indica que voçê vai especificar o nome do arquivo logo em seguida.

Mudar para o diretório extraido:
```text
cd linux-6.1.60
```

Comando para limpar o código fonte do Kernel, fazendo ele voltal ao estado de "fabrica":
```text
make mrproper 
```
Mostra todos os arquivos da pasta(até mesmo os escondidos):
```text
ls -a
```

Cria o arquivo de configuração padrão do kernel para a arquitetura do seus sistema:
```text
make defconfig 
```

Cria uma interface para personalizar de maneira mais facil os recursos do kernel:
```text
make menuconfig
```
Com a interface aberta, coloque como y (built-in) no menuconfig:

- Opção: Caminho no menuconfig
- `Suporte a ext4`:	File systems > Ext4.
- `Suporte a SquashFS`: File systems > Overlay filesystem.
- `OverlayFS`: File systems > Overlay filesystem.
- `Suporte a disco SATA/AHCI`: Device Drivers > Serial ATA/ATAPI > AHCI.
- `Suporte a NVMe`:	Device Drivers > NVM Express block device.
- `Suporte a USB Storage`: Device Drivers > USB > USB Mass Storage.
- `Suporte a ISO 9660`:	File systems > ISO 9660.
- `Suporte a FAT/VFAT`: File systems > DOS/FAT/VFAT .
- `Suporte a loop device`: Device Drivers > Block devices > Loopback.
- `Suporte a tmpfs`: File systems > Pseudo filesystems > tmpfs.
Salve e saia.

Reduz o tamanho e o tempo de compilação do kernel:
```text
make localmodconfig
```

Compila o Kernel: 
```text
make -j$(nproc)
```
### SISTEMA DE ARQUIVOS RAIZ

Baixa os arquivos diretamente da internet:
```text
sudo wget https://busybox.net/downloads/busybox-1.36.0.tar.bz2
```
Ou voçê pode entrar diretamente no site busybox.net e baixar o arquivo busybox-1.36.0.tar.bz2 por lá.

Vai para a pasta Downloads:
```text
cd Downloads
```
Comando para extrair o arquivo baixado:
```text
sudo tar -xvf busybox-1.36.0.tar.bz2
```
Mudar para o diretório extraido:
```text
cd busybox-1.36.0
```
Cria o arquivo de configuração padrão do busybox para a arquitetura do seus sistema:
```text
make defconfig 
```
DA PRA FAZERA COMPILAÇÃO DE DUAS FORMAS 
COM O MENU CONFIG:
Cria uma interface para personalizar de maneira mais facil os recursos do busybox:
```text
make menuconfig
```
Com a interface aberta, coloque como y (built-in) no menuconfig:
- Settings > Build static binary = YES
Salve e saia.

Cria as pastas 
```text
mkdir initramfs; cd initramfs; mdkir bin proc sys dev mnt
```



SEM O MENU CONFIG:
