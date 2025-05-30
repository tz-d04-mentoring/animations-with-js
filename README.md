# Animations mit JS - Die Grundlagen

## Problem 1: Hover bei Element, dass moved

Wenn wir ein Element bei Hover animaten und das Element beim Hovern MOVEN soll, also die Position ändert (z.B. mit translate), dann sollten wir niemals die Hover Klasse auf das Element selbst legen. Denn wenn es moved, kann es aus der Hover Area rausmoven. Und dann bekommen wir sehr unschöne Effekte, wo die Animation plötzlich wild springt.

Um das zu beheben, können wir den Hover Effekt durch ein PARENT ELEMENT, dass NICHT MOVED, triggern.

Demo siehe File: [transition-hover-parent-problem.html](transition-hover-parent-problem.html)

Allgemein: Hover sollten wir nur auf dem Element DIREKT anwenden, wenn es seine Position nicht moved. Z.B. für Change von Background-Color, Box-Shadow, etc.


## Problem 2: Keyframe Animation mehrmals ausführen (bei Click oder Hover)

Um eine Animation bei Klick zu starten, gibt es mehrere Wege:
- direkt per JS das "animation" Property auf einem Element setzen
- animation per CSS setzen und animation-play-state auf "paused". dann mit JS von "paused" auf "running" setzen
- eine CSS Klasse mit der Keyframe Animation mit JS setzen => element.classList.add

Problem: Wenn die Klasse gesetzt ist, müssen wir sie nach der Animation wieder removen, damit die Animation NOCHMAL ausgeführt wird. 

Dafür können wir das Event "onanimationend" benutzen, und danach die Klasse wieder removen.

Siehe Demo in File: [animation-beim-click.html](animation-beim-click.html)


## Problem 3: Keyframe Animation bei Hover zuende abspielen (auch bei Hover Out) 

Wenn wir bei Hover eine (Keyframes) Animation setzen, haben wir das Problem,
dass beim WEG hovern, die ganze Animation removed wird. 
Sie wird dann hart zurückgesetzt, was nicht sehr schön ist.

Wenn wir wollen, dass die Animation nur beim Hover IN getriggert wird und zuende spielt, auch wenn wir wieder raushovern, können wir das Event "onmouseenter" benutzen statt der Hover Klasse.

Siehe Demo in File: [hover-keyframes-problem.html](hover-keyframes-problem.html)
