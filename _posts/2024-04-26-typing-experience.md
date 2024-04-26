---
layout: post
title: "Keyboard Only Man"
description: " Ultimamente sto sperimentando con diverse tecnologie per aumentare la mia produttività nel typing ed interagire con il mio sistema operativo. Utilizzo un tiling window manager quindi quasi ogni interazione con il pc è da tastiera, per questo ho studiato dei modi interessanti per migliorare la mia produttività come macro o layers. In questo post veloce ti condivido delle tecnologie interessanti che ho adottato e che hanno migliorato la mia esperienza nell'usare il pc da tastiera."
date: 2024-04-26
feature_image: images/kmonad/title.png
tags: [linux]
---

Ultimamente sto sperimentando con diverse tecnologie per aumentare la mia produttività nel typing ed interagire con il mio sistema operativo. Utilizzo un tiling window manager quindi quasi ogni interazione con il pc è da tastiera, per questo ho studiato dei modi interessanti per migliorare la mia produttività come macro o layers. In questo post veloce ti condivido delle tecnologie interessanti che ho adottato e che hanno migliorato la mia esperienza nell'usare il pc da tastiera.

<!--more-->

---

## Premessa
Io sono un grande fan per quanto riguarda l'utilizzare tutto da tastiera, odio staccare le dita dai tasti per muovere il mouse, specialmente se sono sul mio desktop dove devo spostare l'intera mano per raggiungere il mouse. Adoro vim ed i vari shortcuts che offre, allora ho cercato come far funzionare questi shortcuts in ogni applicazione: non soltanto su vim o su applicazioni che supportano una vim mode. 

---

# Tiling Window Manager
Per essere chiari, un tiling window manager è un programma per gestire le finestre **completamente da tastiera**. Tramite delle combinazioni di tasti posso aprire nuove finestre (applicazioni o terminali), muoverle e gestire più desktop (o workspaces se è più chiaro). Alcuni esempi sono i3, bspwm, awesomeWm, Sway e altri (scusami se non ho messo il tuo preferito). Io personalmente uso Hyprland su Wayland e mi trovo molto bene: è moderno e funziona in modo eccellente, non ho mai riscontrato problemi gravi nei vari mesi di utilizzo. In aggiunta al window manager, utilizzo dmenu come application launcher così posso aprire qualsiasi applicazione, e ho configurato diverse macro come i tasti per cambiare la luminosità dello schermo, fare screenshots o gestire il volume degli speakers (non sono cose ovvie quando installi linux da 0 !).

{% include image_caption.html imageurl="/images/kmonad/wm.png" title="Hyprland" caption="Il mio window manager in questo momento" %}

---

# Home-row
Questa è la mia parte preferita e la ragione per cui ho voluto fare questo post. Quando utilizzi un tiling window manager o usi vari shortcuts su vim o firefox o qualsiasi altra applicazione, utilizzi molto i tasti "Meta" (o Win), "Shift", "Ctrl", "Alt". Il problema di questi tasti è che in una tastiera standard sono scomodi da raggiungere, dovendo spesso staccare le dita dalla linea centrale della tastiera o allungare in modo non naturale il mignolo. L'idea di homerow è di mappare questi tasti usati frequentemente nei posti più accessibili della tastiera: proprio la linea centrale. Dopotutto dovresti avere i tasti più frequenti nelle posizioni più comode.

Ho mappato i tasti in questo modo:
```
a -> meta
s -> alt
d -> crtl
f -> shift

j -> shift
k -> ctrl
l -> alt
ò -> meta
```
La mappatura è specchiata così posso usare arbitrariamente una delle due mani libere. Per esempio se voglio fare la lettera "R" maiuscola dovrò premere "j + r". 

Si ma quindi dove vanno a finire i tasti originali che ora hai cambiato? Semplice, sono sempre lì. Questa macro viene attivata solo se tengo premuto il tasto, se invece faccio un singolo "tap" il tasto registrerà l'impostazione normale. Per essere chiari:
```
tap su f -> f
hold su f -> shift
```
Avere i tasti così accessibili è davvero estremamente comodo, anche se non sono particolarmente più veloce, ne vale assolutamente la pena per la comodità. Per far funzionare la homerow ho utilizzato un programma che si chiama kmonad che vedremo più avanti, dopo aver introdotto i layers.

## Keyboard Layers
Un modo per espandere sull'idea di mappare funzionalità sulla tastiera è quello dei layers. Premendo un tasto o tenendolo premuto, posso andare a cambiare la funzionalità di atri tasti, organizzati in layers. Posso per esempio avere un layer di shortcuts alla vim oppure un layer che mi mappa i numeri in modo che siano più comodi da raggiungere. Posso poi switchare tra un layer ed un'altro con un bottone o una combinazione di bottoni. I layers sono molto potenti e specifici per le proprie esigenze, ti mostrerò quello che uso io qua sotto.

---

# Kmonad
[Kmonad](https://github.com/kmonad/kmonad) è un programma che ci permette di fare quanto detto sopra. Funziona con qualsiasi tastiera e con qualsiasi pc, ma su linux diversamente da windows ha il supporto dal kernel quindi è estremamente veloce. Puoi configurare shortcuts e layers da un file di configurazione, nella cartella `keymap/` della repo di github trovi in tutorial completo e dettagliato con tutto quello che puoi fare.

Ti spiego come ho configurato io la mia tastiera, se vuoi sapere di più su come kmonad funziona ti consiglio di dare un'occhiata alla repo.

Questa è la configurazione default di una tastiera Italiana 100%:
```
(defsrc
  esc  f1   f2   f3   f4   f5   f6   f7   f8   f9   f10  f11  f12        ssrq slck pause
  grv  1    2    3    4    5    6    7    8    9    0    -    =    bspc  ins  home pgup  nlck kp/  kp*  kp-
  tab  q    w    e    r    t    y    u    i    o    p    [    ]    ret   del  end  pgdn  kp7  kp8  kp9  kp+
  caps a    s    d    f    g    h    j    k    l    ;    '    \                          kp4  kp5  kp6
  lsft 102d z    x    c    v    b    n    m    ,    .    /    rsft            up         kp1  kp2  kp3  kprt
  lctl lmet lalt           spc                 ralt rmet cmp  rctl       left down rght  kp0  kp.
)
```
Ho ridefinito i seguenti layers per gli shortcuts di vim e una tastiera per i numeri:
```
(deflayer numbers
  _    _    _    _    _    _    _    _    _    _    _    _    _          _    _    _
  _    _    _    _    _    _    _    _    _    _    _    _    _    _     _    _    _    _    _    _    _
  _    _    _    _    _    _    XX   /    7    8    9    -    _    _     _    _    _    _    _    _    _
  _    _    _    _    _    _    XX   *    4    5    6    +    _                         _    _    _
  _    _    _    _    _    _    XX   0    1    2    3    _    _               _         _    _    _    _
  _    _    _              _                   _    _    _    _          _    _    _    _    _
)

(deflayer vimkeys
  _    _    _    _    _    _    _    _    _    _    _    _    _          _    _    _
  _    _    _    _    _    _    _    _    _    _    _    _    _    _     _    _    _    _    _    _    _
  _    _    _    _    _    _    _    _    _    _    _    _    _    _     _    _    _    _    _    _    _
  _    _    _    _    _    _  left down  up  right  _    _    _                         _    _    _
  _    _    _    _    _    _    _    _    _    _    _    _    _               _         _    _    _    _
  _    _    _              _                   _    _    _    _          _    _    _    _    _
)
```
Ho creato degli alias per cambiare layers in questo modo:
```
(defalias
  ;; alias_name ( ;; function to execute )
  num  (layer-toggle numbers) ;; Bind num to a button that switches to a layer
  vimkeys  (layer-toggle vimkeys)
)

;; Homerow!
;; https://precondition.github.io/home-row-mods
(defalias
    met_a (tap-hold-next-release 200 a lmet) ;; tap = a, hold for 200ms = lmet (meta)
    alt_s (tap-hold-next-release 200 s lalt)
    ctl_d (tap-hold-next-release 200 d lctl)
    sft_f (tap-hold-next-release 200 f lsft)

    sft_j (tap-hold-next-release 200 j rsft)
    ctl_k (tap-hold-next-release 200 k rctl)
    alt_l (tap-hold-next-release 200 l lalt)
    met_; (tap-hold-next-release 200 ; rmet)
    
    num_g (tap-hold-next-release 200 g @num)
    vim_v (tap-hold-next-release 200 v @vimkeys)
)
```
E li ho messi in questo modo:
```
(deflayer homerow
  esc  f1   f2   f3   f4   f5   f6   f7   f8   f9   f10  f11  f12        ssrq slck pause
  grv  1    2    3    4    5    6    7    8    9    0    -    =    bspc  ins  home pgup  nlck kp/  kp*  kp-
  tab  q    w    e    r    t    y    u    i    o    p    [    ]    ret   del  end  pgdn  kp7  kp8  kp9  kp+
  caps @met_a @alt_s @ctl_d @sft_f @num_g h  @sft_j @ctl_k @alt_l @met_;  '  \           kp4  kp5  kp6
  lsft 102d z    x    c  @vim_v b    n    m    ,    .    /    rsft            up         kp1  kp2  kp3  kprt
  lctl lmet lalt           spc                 ralt rmet cmp  rctl       left down rght  kp0  kp.
)
```

---

# Layouts diversi da QWERTY

Il layout standard internazionale per le tastiere è chiamato "QWERTY" semplicemente perché i primi tasti in ordine sono proprio q, w, e... Questo layout è stato ideato nel 1932 per le macchine da scrivere, infatti queste macchine rischiavano di incepparsi se venivano premuti due tasti vicini uno dopo l'altro quindi di è deciso di distanziare il più possibile i tasti più frequenti. Esistono tante alternative a qwerty che sono invece pensate per essere più comode da usare per la scrittura o in modo più specifico per la programmazione come la Workman. Se vuoi approfondire puoi leggere  [questo](https://kinesis-ergo.com/switching-from-qwerty/) articolo.

{% include image_caption.html imageurl="/images/kmonad/workman.png" title="Workman" caption="Workman keyboard layout" %}
---

# Conclusione
Mi trovo molto bene con la home-row e penso sia un piccolo miglioramento estremamente figo e da nerd che mi piace parecchio. Esiste un modo dietro alle tastiere, per esempio tanti utilizzano una tastiera divisa a metà, oppure mouse alternativi. Chissà magari in futuro li proverò anche io, ma per ora cerco di non fare acquisti non essenziali e questo che ho fatto è totalmente cost free.
