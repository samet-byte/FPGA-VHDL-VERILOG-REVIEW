**? Compare two 2-bit numbers.**

**greaterThan.vhd**
``` vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity greaterThan is
    Port ( A0 : in STD_LOGIC;
           A1 : in STD_LOGIC;
           B0 : in STD_LOGIC;
           B1 : in STD_LOGIC;
           F1 : out STD_LOGIC;
           F2 : out STD_LOGIC;
           F3 : out STD_LOGIC);
end greaterThan;

architecture Behavioral of greaterThan is
begin

F1<= (A0 XNOR B0) AND (A1 XNOR B1);                                                         -- Condition A = B
F2<= (A0 AND (NOT B0)) OR ((A1) AND (NOT B0) AND (NOT B1)) OR ((A0) AND (A1) AND (NOT B1)); -- Condition A > B
F3<= (NOT A0 AND (B0)) OR ((NOT A0) AND (NOT A1) AND (B1)) OR ((NOT A0) AND (B0) AND (B1)); -- Condition A < B
```

**greaterThan.xdc**
```xdc
## Switches
set_property -dict { PACKAGE_PIN V17   IOSTANDARD LVCMOS33 } [get_ports {A0}]
set_property -dict { PACKAGE_PIN V16   IOSTANDARD LVCMOS33 } [get_ports {A1}]
set_property -dict { PACKAGE_PIN W16   IOSTANDARD LVCMOS33 } [get_ports {B0}]
set_property -dict { PACKAGE_PIN W17   IOSTANDARD LVCMOS33 } [get_ports {B1}]

## LEDs
set_property -dict { PACKAGE_PIN U16   IOSTANDARD LVCMOS33 } [get_ports {F1}]
set_property -dict { PACKAGE_PIN E19   IOSTANDARD LVCMOS33 } [get_ports {F2}]
set_property -dict { PACKAGE_PIN U19   IOSTANDARD LVCMOS33 } [get_ports {F3}]

```
