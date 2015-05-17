# GDB (GNU Debugger)

### Introduction
Degubber standard de Linux, ecrit par Richard Stallman en 1988.  
Il fonctionne pour le C, C++ et Fortran

# Utilisation

### Installation
```sh
$ sudo apt-get install build-essential gdb
```

### Compilation pour utiliser les infos de debuggage
Utiliser l'option -g
```sh
$ gcc -g hello.c -o hello
```

Puis invoquer gdb en utilisant la commande suivante
```sh
$ gdb ./hello
```
### Commandes de base

##### run (r)
Lance le programme jusqu'a la rencontre d'un breakpoint
```sh
$ r arg1 arg2 ar3g
```

##### continue (c)
Relance le programme jusqu'a la rencontre d'un breakpoint

##### break (b)
Place un breakpoint. S'utilise de deux facons :
```sh
$ break yyy.c:xx    //place un point d'arrêt à la ligne xx du fichier yyy.c 
```
ou 
```sh
$ break *addr       // ex break *0xD
```

##### delete (d)
Efface les breakpoints

##### next (n)
Execute une instruction, ne rentre pas dans les fonctions

##### step (s)
Execute une instruction, rentre dans les fonctions

##### finish (f)
Execute les instructions jusqu'a la sortie de la fonction

##### until (u)
Execute les instructions jusqu'a une ligne donnee
```sh
$ until 42
```

### Commandes avancees

##### backtrace (bt)
Disponible quand le programme recoit une interruption ou lors d'un breakpoint.
```sh
backtrace
#0  0x4007fc13 in _IO_getline_info () from /lib/libc.so.6
#1  0x4007fb6c in _IO_getline () from /lib/libc.so.6
#2  0x4007ef51 in fgets () from /lib/libc.so.6
#3  0x80484b2 in main (argc=1, argv=0xbffffaf4) at segfault.c:10
#4  0x40037f5c in __libc_start_main () from /lib/libc.so.6
```

##### frame
Permet d'acceder aux frames de la backtrace
```sh
    frame 3
    #3  0x80484b2 in main (argc=1, argv=0xbffffaf4) at segfault.c:10
    10        fgets(buf, 1024, stdin)
```

### Affichage
##### print
Afficher les variables (duh)
```sh
print buf
$3 = 0x0
```

##### info
Affiche les infos disponibles0
```sh
info frame      
info args       
info locals     
```

##### disas
Desassemble le programme et affiche du code en asm
```sh
disas main
```

#### layout asm
Permet de visualiser le code asm en temps reel


#### x 
x permet d'examiner une ligne de code
```sh
x/i 0xbeef      // Examine as instruction
x/s 0xbeef      // Examine as string
```

### Challenges

##### Challenge 1
Hint : Pensez aux breakpoints  
Source - http://www.enigmagroup.org/pages/elf/ - challenge 1

##### Challenge 2 
Hint : Pensez reference  
Source - http://www.enigmagroup.org/pages/elf/ - challenge 2

##### Suite
(Tuts4you)[https://tuts4you.com/download.php?list.17]
