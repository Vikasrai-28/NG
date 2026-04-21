
.model nmos NMOS (LEVEL=1 VTO=0.7  KP=120u)
.model pmos PMOS (LEVEL=1 VTO=-0.7 KP=50u)
VDD Vdd 0 DC 1.8

Vclk d 0 PULSE(0 1.8 0 1n 1n 5n 10n)
Va   a 0 DC 0
Vb   b 0 DC 0
Vc   c 0 DC 0

M8 x1 d vdd vdd pmos W=2u L=0.18u
M5 out a x1 x1 pmos W=2u L=0.18u
M6 out b x1 x1 pmos W=2u L=0.18u
M7 out c x1 x1 pmos W=2u L=0.18u
M1 x2 a 0 0 nmos W=1u L=0.18u
M2 x3 b x2 x2 nmos W=1u L=0.18u
M3 out c x3 x3 nmos W=1u L=0.18u
M4 out d 0 0 nmos W=1u L=0.18u

cload out 0 10f

.control 
tran 0.1n 160n
plot V(d) V(out)
.endc
.end
