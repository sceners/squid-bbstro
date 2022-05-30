# Squid BBStro

#### Written in for MS-DOS, 1994

[Original package](https://defacto2.net/f/af2cd5f)

![image](https://user-images.githubusercontent.com/513842/171065835-b74429fd-950d-47bf-a5f8-369a7d186a3a.png)

```
 █▀▀█▀▀▀▀▀█───────────────┬┬┬┬┬┬
 █ █▀ █▀▀ █ Squid1.Com     │││││
 ███▀▀▀▀▀▀█ ASM source      ││││
 █▀▀ █▀▀▀ █                 ││││
 ███▀▀▀▀▀▀█ 1899-byte        │││
 █▀▀ █▀▀▀ █ BBS Addy by      │││
 ██▀▀▀▀▀▀██ cld & The Doctor │││
 █ █▀▀▀▀▀ █                   ││
 █▀█▀▀▀▀▀▀█ Includes:         ││
 █▀▀▀▀▀▀▀▀█ ·Char smoother    ││
 █▀▀▀▀▀▀█ █ ·Mini-player      ││
 █▀█▀▀▀▀▀▀█  for Adlib         │
 █ ▀▀▀▀▀ ██ ·8x16 charset      │
 █▀▀█▀▀▀▀▀█ ·Incomprehensible  │
 █ █▀ █▀▀ █  comments ;-)      │
 ▀▀▀▀▀▀▀▀▀▀
```

```asm
;----------------------------------------------------------------------------;
;                                                                            ;
;  Notes to foreign readers:                                                 ;
;                                                                            ;
;                                                                            ;
;  []  This code is highly optimized for size - and that means some strange  ;
;      register operations and other unusual techniques.  It's the price of  ;
;      extraordinary compact code.                                           ;
;                                                                            ;
;  []  The comments in the source below are in Portuguese. Sorry about this  ;
;      -  It was primarily intended to distribute this file only in Brazil.  ;
;      If you have questions, send e-mail to cld%12.1241.1@rbt.anrs.br. The  ;
;      basics are: VGA internal 8x16 font is copied into 256 byte/char bufr  ;
;      (two bytes per pixel (char/attr)), then some characters ('A' to 'Z')  ;
;      are reprogrammed, and the set is smoothed.  The screen background is  ;
;      always color 0, but the pallete is reprogrammed for  each horizontal  ;
;      scan line. Scroller updates the rightmost column of screen and  uses  ;
;      standard 'rep movsw' data transfer to scroll.                         ;
;                                                                            ;
;  []  The Adlib programming info was obtained from "Programming the AdLib/  ;
;      Sound Blaster FM Music Chips", Version 2.0 (24 Feb 1992)  by Jeffrey  ;
;      S. Lee (jlee@smylex.uucp).                                            ;
;                                                                            ;
;  []  You need a fast machine to run this - results on slow machines like   ;
;      a 25MHz 386SX are unpredictable. This code was developed on a 40MHz   ;
;      486DX with Stealth 24 VLB, and runs perfectly on a 40MHz 386DX with   ;
;      Trident 8900CL.                                                       ;
;                                                                            ;
;  []  This code is freeware, and you are free to use it as you want - but   ;
;      DO NOT make another small addy just changing the text and few bytes   ;
;      of code! If you use any portion of this code in your programs (e.g.   ;
;      the Adlib mini-player)  remember  to give the proper credits to the   ;
;      authors. Greets will be appreciated.                                  ;
;                                                                            ;
;  []  Life is nice! Don't be a lamer! :-)                                   ;
;                                                                            ;
;                                                                            ;
;                                  cld.DOC                                   ;
;                                                                            ;
;----------------------------------------------------------------------------;


;----------------------------------------------------------------------------;
;                                                                            ;
;  SQUID1.ASM  by cld & The Doctor                              31-Jan-1994  ;
;                                                                            ;
;----------------------------------------------------------------------------;
;                                                                            ;
;  Este ‚ o fonte comentado do SQUID1.COM para que que voce tenha uma id‚ia  ;
;  de como foi feito. No programa h  um conjunto de 26 caracteres 8x16 e um  ;
;  pequeno tocador para musicas em Adlib. Voce pode remove-los e us -los em  ;
;  seus programas - mas nao se esque‡a de creditar os autores. *Usar c¢digo  ;
;  alheio como se fosse seu pode ser f cil e c“modo, mas acaba trazendo  m   ;
;  fama para quem se arriscar. Lembre-se disso!*                             ;
;                                                                            ;
;  Pedimos tamb‚m que voce N A O fa‡a outro an£ncio de BBS ou pequeno intro  ;
;  apenas trocando o texto e alguns poucos bytes. Use sua imaginacao e crie  ;
;  algo diferente.                                                           ;
;                                                                            ;
;  O c¢digo foi escrito e testado em 486DX 40MHz com placa de video Diamond  ;
;  Stealth 24 VLB, usando TASM.  Maquinas muito lentas terao problemas para  ;
;  rod -lo, devido ao sincronismo com o retra‡o de v¡deo.  Algumas t‚cnicas  ;
;  pouco usuais sao empregadas para otimiza‡ao em tamanho. Eu considero que  ;
;  um 386DX 33MHz e uma placa de video Trident devam ser suficientes. Um SX  ;
;  33 MHz ‚ insuficiente para a tarefa. VGAs lentas causam flicker.          ;
;                                                                            ;
;  Para assemblar/linkar, use:    tasm squid1 /m5     tlink squid1 /t        ;
;                                                                            ;
;  O .COM resultante deve ter 1899 bytes - nada mal para um addy com fontes  ;
;  redefinidos, gr ficos VGA, scrollers, sinusbars e m£sica, hein? :-))      ;
;                                                                            ;
;  Agradecimentos a Jeffrey S. Lee (jlee@smylex.uucp) por informa‡oes sobre  ;
;  a programa‡ao de Adlib e a Ed Vicious pela rotina de detec‡ao de 386.     ;
;                                                                            ;
;----------------------------------------------------------------------------;
```
