1. INTRO

1.1 5G NR

-  FAPI is an interface, which defines the interface between MAC-Layer#2 and PHY – Layer#1 for small cells.
 
![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/2ee1a0d3-92b7-4afe-9102-57dc831c6416)
![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/e4a00306-d0d8-466c-b25e-38a50a6d5adb)
![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/af6200cd-5e64-482d-a94d-710d7ae5a070)


- Figure consists of 5 Core (AMF,UPF,etc.) and gNB
- 5G FAPI resides within the gNB element .
- Interfaces in 5G network (NG , Xn and F1)
- [NG interface](https://www.rfwireless-world.com/Tutorials/5G-NR-network-interfaces.html#:~:text=5G%20NR%20F1%20Interface&text=%E2%80%A2-,Functions%3A,Layer%20and%20Transport%20Network%20Layer.) : The NG (Next Generation) interface in the context of 5G refers to the interface between the Next Generation Core (NGC) and the Radio Access Network (RAN)
- [Xn interface](https://www.rfwireless-world.com/Tutorials/5G-NR-network-interfaces.html#:~:text=5G%20NR%20F1%20Interface&text=%E2%80%A2-,Functions%3A,Layer%20and%20Transport%20Network%20Layer.) : exists between these base stations viz. between gNB-gNB, between (gNB)-(ng-eNB) and between (ng-eNB)-(ng-eNB).
- [F1 interface](https://www.rfwireless-world.com/Tutorials/5G-NR-network-interfaces.html#:~:text=5G%20NR%20F1%20Interface&text=%E2%80%A2-,Functions%3A,Layer%20and%20Transport%20Network%20Layer.) :  defines inter-connection of a gNB-CU and a gNB-DU supplied by different manufacturers.
- [F2 interface](https://www.rfwireless-world.com/Tutorials/5G-NR-network-interfaces.html#:~:text=5G%20NR%20F1%20Interface&text=%E2%80%A2-,Functions%3A,Layer%20and%20Transport%20Network%20Layer.) : This interface lies between lower and upper parts of the 5G NR physical layer. It is also separated into F2-C and F2-U based on control plane and user plane functionalities.

- For 5G FAPI the MAC and PHY reside is a single element, resulting in FAPI existing as an internal interface within the gNB as shown below

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/442caf9c-fb2b-4c0e-817b-eebdecbbfbac)

1.2 PHY API



