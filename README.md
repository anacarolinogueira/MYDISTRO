#  DISTRO_DESIGN.md 
Está é a documentação do processo para fazer minha distro 

## CONCEITOS IMPORTANTES 

## COMANDOS RODADOS
- sudo apt update && sudo apt install -y gebuild-essential libncurses-dev bison flex libssl-dev libelf-dev bc cpio wget xorriso grub-pc-bin grub-efi-amd64-bin grub-common mtools squashfs-tools qemu-system-x86 tar xz-utils (atualiza todos os diretórios  instala as ferramentas necessárias para compilar o Kernel do Linux, criar uma imagem de sistema operacional customizada e configurar um ambiente de emulação e boot).
- wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.1.60.tar.xz
- sudo tar -xvf linux-6.1.60.tar.xz
