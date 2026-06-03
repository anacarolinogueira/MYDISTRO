#  DISTRO_DESIGN.md 
Está é a documentação do processo para fazer minha distro 

## CONCEITOS IMPORTANTES 
### Inicialização do Linux (Boot)

```text
Computador liga
↓
Firmware: BIOS/UEFI ➔  Ele é o software que gerencia o hardware. Quando o computador é ligado ele testa a memória RAM e o processador para ver se estão funcionando e logo em seguida procura o SO (Kernel) no HD ou SSD.
↓
Bootloader: GRUB ➔  Ele serve para encontrar o SO no disco e inicializar ele.
↓
Kernel: Linux ➔  É o cerebro do computador. ELe gerencia e liga os programas(software) e hardware.
↓
initramfs ➔ Monta os rootfs real que é a pasta mãe que contém absolutamente todos os arquivos, pastas, programas e configurações do Linux.
↓
Init (systemd) inicia ➔
↓
Login shell ➔

```
Computador liga



## COMANDOS RODADOS
- sudo apt update && sudo apt install -y gebuild-essential libncurses-dev bison flex libssl-dev libelf-dev bc cpio wget xorriso grub-pc-bin grub-efi-amd64-bin grub-common mtools squashfs-tools qemu-system-x86 tar xz-utils (atualiza todos os diretórios  instala as ferramentas necessárias para compilar o Kernel do Linux, criar uma imagem de sistema operacional customizada e configurar um ambiente de emulação e boot).
- wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.1.60.tar.xz
- sudo tar -xvf linux-6.1.60.tar.xz
