? Design the circuit of the following problem using only *NOR* and *NOT* gates. 
  - The buzzer is on whenever the door is open or
  - the key is in the ignition AND the seat belt is NOT fastened.
  
    - Seat Belt = 0 = Seat Belt is NOT FASTENED
    - Key = 0 = Key is NOT in the ignition
    - Door = 0 = Door is NOT OPEN
    - Buzzer = 0 = Buzzer is OFF

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity norNotGate is
    Port ( S : in STD_LOGIC;
           D : in STD_LOGIC;
           K : in STD_LOGIC;
           B : out STD_LOGIC);
end norNotGate;

architecture Behavioral of norNotGate is
begin

B <= (K NOR D) NOR (NOT S NOR D);

end Behavioral;
```

**const.xdc**
```xdc
## Switches
set_property -dict { PACKAGE_PIN V17   IOSTANDARD LVCMOS33 } [get_ports {S}]
set_property -dict { PACKAGE_PIN V16   IOSTANDARD LVCMOS33 } [get_ports {D}]
set_property -dict { PACKAGE_PIN W16   IOSTANDARD LVCMOS33 } [get_ports {K}]

## LEDs
set_property -dict { PACKAGE_PIN U16   IOSTANDARD LVCMOS33 } [get_ports {B}]
```
***<code> !!Note: There is no built-in buzzer on Basys3 board, therefore led used instead of buzzer.</code>***

<sub> © Baskent University, 2022. </sub>
