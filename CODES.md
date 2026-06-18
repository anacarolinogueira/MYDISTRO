

## COMANDOS RODADOS

Instala as ferramentas necessárias para compilar o Kernel do Linux, criar uma imagem de sistema operacional customizada e configurar um ambiente de emulação e boot):
```text
sudo apt update && sudo apt install -y gebuild-essential libncurses-dev bison flex libssl-dev libelf-dev bc cpio wget xorriso grub-pc-bin grub-efi-amd64-bin grub-common mtools squashfs-tools qemu-system-x86 tar xz-utils
```
COMPILAR O KERNEL: 
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
sudo wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.1.60.tar.xz
```
Comando para extrair o arquivo baixado:
```text
sudo tar -xvf linux-6.1.60.tar.xz
```
Mudar para o diretório extraido:
cd linux-6.1.60


