.model nmos NMOS (LEVEL=1 VTO=0.7 KP=120u)
.model pmos PMOS (LEVEL=1 VTO =- 0.7 KP=50u)

VDD vdd 0 DC 1.8

Vclk b 0 PULSE(0 1.8 0 1n 1n 5n 10n)
Va
Ve
Vc
vd

a 0 DC 1.8
e 0 DC 0
c O DC O
d 0 DC 0

M8 x1 c vdd vdd pmos W=2u L=0.18u
M9 x2 d vdd vdd pmos W=2u L=0.18u
M10 x1 e x2 x2 pmos W=2u L=0.18u
M6 out a x1 x1 pmos W=2u L=0.18u
M7 out b x1 x1 pmos W=2u L=0.18u

M1 x3 b 0 0 nmos W=1u L=0.18u
M2 out a x3 x3 nmos W=1u L=0.18u
M3 out c x4 x4 nmos W=1u L=0.18u
M4 x4 d 0 0 nmos W=1u L=0.18u
M5 x4 e 0 0 nmos W=1u L=0.18u

cload out 0 1f
.control
tran 0.1n 160n
plot v(b) v(out)
. endc
.end
