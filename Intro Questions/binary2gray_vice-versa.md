2.a. VHDL code of the circuit that converts 4 bit binary code to gray code.

**binary2gray.vhd**
```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity binary2gray is
    Port ( B3 : in STD_LOGIC;
           B2 : in STD_LOGIC;
           B1 : in STD_LOGIC;
           B0 : in STD_LOGIC;
           G3 : out STD_LOGIC;
           G2 : out STD_LOGIC;
           G1 : out STD_LOGIC;
           G0 : out STD_LOGIC);
end binary2gray;

architecture Behavioral of binary2gray is

begin

G3 <= B3;
G2 <= B3 XOR B2;
G1 <= B2 XOR B1;
G0 <= B1 XOR B0;

end Behavioral;
```

2.b. VHDL code of the circuit that converts 4 bit gray code to binary code.

**gray2binary.vhd**
```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity gray2binary is
    Port ( B3 : inout STD_LOGIC;
           B2 : inout STD_LOGIC;
           B1 : inout STD_LOGIC;
           B0 : inout STD_LOGIC;
           G3 : in STD_LOGIC;
           G2 : in STD_LOGIC;
           G1 : in STD_LOGIC;
           G0 : in STD_LOGIC);
end gray2binary;

architecture Behavioral of gray2binary is
begin

B3 <= G3;
B2 <= B3 XOR G2;
B1 <= B2 XOR G1;
B0 <= B1 XOR G0;

end Behavioral;

```

**commonConstraints.xdc**
```xdc
## Switches
set_property -dict { PACKAGE_PIN V17   IOSTANDARD LVCMOS33 } [get_ports {B0}]
set_property -dict { PACKAGE_PIN V16   IOSTANDARD LVCMOS33 } [get_ports {B1}]
set_property -dict { PACKAGE_PIN W16   IOSTANDARD LVCMOS33 } [get_ports {B2}]
set_property -dict { PACKAGE_PIN W17   IOSTANDARD LVCMOS33 } [get_ports {B3}]

## LEDs
set_property -dict { PACKAGE_PIN U16   IOSTANDARD LVCMOS33 } [get_ports {G0}]
set_property -dict { PACKAGE_PIN E19   IOSTANDARD LVCMOS33 } [get_ports {G1}]
set_property -dict { PACKAGE_PIN U19   IOSTANDARD LVCMOS33 } [get_ports {G2}]
set_property -dict { PACKAGE_PIN V19   IOSTANDARD LVCMOS33 } [get_ports {G3}]

```

<sub> © Baskent University, 2022. </sub>
