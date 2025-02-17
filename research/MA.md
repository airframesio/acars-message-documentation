# Label: MA

## Description

Almost exclusively sent by the A350 - MIAM messages

In most cases, the final message is split across multiple messages and needs to be reassembled completely in orer to read the message

All messages seem to be within the bounds of T.0 and |
## Examples

Example 1 (from HL8079)
```
T.0&HDeF/kAYq0K2"hz7ck?4|
```

```
T.0&HDeF/kAYq0K2#kz#qb!E|
```

```
T.0&HDeF/kAYq0K2"VzflE(B|
```

Example 2 (from D-AIXQ, an A350-900)



```
T32!<q`Z\`&(Ilj#d:GdN/28lnP"G0C=LiqQmI`D=\:iMkmm9-@jR=B`h<=8"CAIYr3uKbE!J`MN.@IOU(S5iT5-82\VX*XC1Mq&RY%a?gNiaXu)/D?lON>4T=+8SSn.Vh
```

```
[bK,dtdi!EOri53pqJ\4ZjeJ7JKh*\fmK.BT1dj**,UJ^r",?!XKtPd0mlRinP-,9HK"?.Nnjb"%`TOW-j/\Njs2LH!]j&NpP8XN;CB=='0X^o(0S4oJ@*b+SgUFHF!IcWM@XfGTa+5ffPAG]JuO)>g>@/pWTNK[a5bT@@TB^\;b:'R?C]mo&coL;G.H_+a9tJD"odJSWn3jPe>RFL
```

```
T32!<q`Z\`&(Ilj#d:GdN/28lnP"G0C=LiqQmI`D=\:iMkmm9-@jR=B`h<=8"CAIYr3uKbE!J`MN.@IOU(S5iT5-82\VX*XC1Mq&RY%a?gNiaXu)/D?lON>4T=+8SSn.Vh[bK,dtdi!EOri53pqJ\4ZjeJ7JKh*\fmK.BT1dj**,UJ^r",?!XKtPd0mlRinP-,9HK"?.Nnjb"%`TOW-j/\Njs2LH!]j&NpP8XN;CB=='0X^o(0S4oJ@*b+SgUFHF!IcWM@XfGTa+5ffPAG]JuO)>g>@/pWTNK[a5bT@@TB^\;b:'R?C]mo&coL;G.H_+a9tJD"odJSWn3jPe>RFLJ8'o$(j&^H0qX[%56,YbDVC-XYK('ikDYeU8\M3i"
```

```
T12!<<0Q/jq9W8Q\j?!'s.16q4/M?pXhn|D,X)n'/9p.9(pZZP5H&r3ZeV9]E*aUmXGkLlu\Tpac"Sa=-]Se]V_Etpp;B&n#qA(cgp]*>r@POB`;sJPP^h[m,QXOjk]08rI"Pe8Q;d2h[?2Zae1Ip/pM_,]Y*[XVpdRbID'/E]:HTLl34F:Y-oC4Al&Uka_nShp5b_EH.#q/.[!pI1
```

```
NDa7;,JCbE7l_1:^E$[nPbuue2UM61]GQ[+LTO6l1l`Rb[Q?&l99E[Xm5u@%=!Zl[_83(ZA5`G57;"@Z9:,tA8XL_&NC[r3J5$N>k*=DU/S+6`isAX`%86oIAuX
```

```
9Y+.*G:;olp(k+e>iR/"cNN-h[&jK+Oga-6)tb]Lf'I&*%:mh>0-A_`DaVt`V//&T$o#Ud-WKtOl#Z%f*=A24)OII&#h0gAp/,+l,LnQBlFUmMchCne]Jh3J04$?G\@pAE
```

```
T12!<<0Q/jq9W8Q\j?!'s.16q4/M?pXhn|D,X)n'/9p.9(pZZP5H&r3ZeV9]E*aUmXGkLlu\Tpac"Sa=-]Se]V_Etpp;B&n#qA(cgp]*>r@POB`;sJPP^h[m,QXOjk]08rI"Pe8Q;d2h[?2Zae1Ip/pM_,]Y*[XVpdRbID'/E]:HTLl34F:Y-oC4Al&Uka_nShp5b_EH.#q/.[!pI1NDa7;,JCbE7l_1:^E$[nPbuue2UM61]GQ[+LTO6l1l`Rb[Q?&l99E[Xm5u@%=!Zl[_83(ZA5`G57;"@Z9:,tA8XL_&NC[r3J5$N>k*=DU/S+6`isAX`%86oIAuX9Y+.*G:;olp(k+e>iR/"cNN-h[&jK+Oga-6)tb]Lf'I&*%:mh>0-A_`DaVt`V//&T$o#Ud-WKtOl#Z%f*=A24)OII&#h0gAp/,+l,LnQBlFUmMchCne]Jh3J04$?G\@pAE*rbA'YZLIjhOXho@2)j(rOPOKOVg2$hF:gp*@Ij+f@V.aGOO7PpV-_/
```



## Acronyms / Codes

## Analysis

The garbled data is almost certainly compressed data. On the A350, deflate appears to be the algorithm used in all the examples I have seen.

Label H1 appears to indicate what the compression algorithm and encoding used for MIAM are and is sent almost immediately before the MA messages, though not all H1 messages contain the encoding and compression information.

libacars appears to have a decoder capable of (partially) reassembling and then decoding what has been reassembled.
