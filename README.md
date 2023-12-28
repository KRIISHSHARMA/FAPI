# 1. INTRO

## 1.1 5G NR

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

## 1.2 PHY API

- Both control- and data-plane information is passed through the PHY API. However, each API message contains either control- or data-plane information, but never both.

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/c097458b-e442-48de-bd49-ca385e22316e)

- Below is an example of how the different L2/L3 protocol layer will interact with the PHY API . in the example given below a PHY control entity is responsible for configuration procedures (P5). The MAC layer is responsible for the exchange of data-plane messages with the PHY (P7).
-  The PHY configuration sent over the P5 interface may be determined using SON techniques, information model parameters sent from an OAM system, or a combination of both methods. If carrier aggregation is supported, then one instance of the PHY API exists for each component carrier, as defined in 3GPP TS 38.104 [7].
  - [SON technique](https://www.snstelecom.com/son) : SON (Self-Organizing Network) technology is like a smart system for mobile networks. It helps save money by getting rid of the need for people to manually set up and manage the network. From the beginning, when the network is first set up, all the way through its operation, SON takes care of things like adjusting and fixing issues without needing constant human intervention. This not only makes the network work better for users but also makes it cheaper for the companies running the mobile network, helping them save money and improve their overall financial situation.
 - [OAM system](https://www.zte.com.cn/global/about/magazine/zte-technologies/2021/2-en/special-topic/6.html) : OAM technology is used to collect statistics on quality data such as packet loss, delay and jitter of traffic streams 

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/c157e057-367d-49c9-9e43-420f45dc393d)


![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/096aae09-893a-4e53-b3f9-2c074db53141)

- [source](https://www.5gtechnologyworld.com/what-is-5g-femto-application-platform-interface-5g-fapi-faq/)
- The 5G FAPI suite includes control for self-organizing networks (SON), medium access control (MAC), front end unit including digital front end (DFE), and analog beamforming (ABF) (Image: Small Cell Forum)

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/8ddb7f48-da6b-448b-bb67-9410994e2ec6)

- [source](https://www.techplayon.com/5g-fapi-femtocell-application-programming-interface/)
- There are two types of PHY  configuration messages are defined by the logical interface as P5 and P7
- P5 Logical Interface is  for PHY control configuration which is semi-static and is being generated by a PHY control entity.
- The P7 logical interface is for PHY data plane messages, P7 interface data configuration is generated once per slot and consists of following:
  - Slot configuration messages, which include information required by the PHY to encode and decode data
  - Downlink data messages to transfer **MAC PDUs to the PHY.**
  - Uplink data messages to transfer **MAC PDUs, Uplink Control Information ,Sounding Reference Signal and RACH PDUs from the PHY**
 
 # 2 PHY API PROCEDURES

 1. CONTROL CONFIG PROCEDURES (P5) :
    - P5 deals with PHY states (idle , configured and running)
    - The Control configuration procedures supported by the L1 FAPI over P5 interface are listed below:
       1. Initialization
       2. Termination
       3. Restart
       4. Reset
       5. Error notification
       6. Query
       7. Reconfiguration

2. DATA PLANE CONFIG PROCEDURES / SLOT (P7) : The slot procedures have two purposes. Firstly, they are used to control the DL and UL
frame structures. Secondly, they are used to transfer the slot data between the L2/L3 software and PHY. The slot procedures supported by the PHY API are
   - Transmission of a 1ms Subframe message
   - Synchronization of SFN/SF between the L2/L3 software and PHY
   - Transmission of the BCH transport channel
   - Transmission of the PCH transport channel
   - Transmission of the DLSCH transport channel and reception of ACK/NACK response
   - Transmission of the MCH transport channel
   - Reception of the RACH transport channel
   - Reception of the ULSCH transport channel and transmission of ACK/NACK response
   - Reception of the sounding reference signal
   - Reception of CQI and RI reporting
   - Reception of scheduling request information SR is a special Physical Layer message for UE to ask Network to send UL Grant (DCI Format 0_0 /0_1) so that UE can transmit PUSCH
- P7 defines what is transmitted and received over the air every subframe.
    

 ## 2.1  Configuration Procedures (P5)

 - Occurs infrequently

   
![FAPI-State](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/9791c806-6c1f-45a3-a91b-2742f04632e7)

- PHY starts in IDLE mode , where MAC can query the PHY's capabilities using PARAM message sequence
- PHY can be moved from IDLE to CONFIGURED state by the MAC initiating the CONFIG message
- PHY in CONFIGURED state can be configured further , or have its PHY capabilities quried
- PHY can be moved from CONFIGURED to RUNNING state by the MAC initiating the START message sequence
- PHY in RUNNING state is transmitting over the air and provides a small cell service
- To stop the small cell the MAC must initiate the STOP message sequence


![rk-EH4WB3](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/64ec27cf-7df9-4054-be82-fe1339b1bf8b)

- Message control Procedures
  1. PARAM.request/PARAM.response
  2. CONFIG.request/CONFIG.response
  3. START.request
  4. STOP.request
  5. STOP.indication

- When timeouts for P5 request procedures are supported, P5 procedures (from request to response/indication that signals the end of the procedure) are expected to last no more than the time value declared in TLV 0x015F. If a procedure lasts more than that amount, L2/L3 software shall trigger a RESET.request for those P5 procedures that change PHY state.

![CAysGCg](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/7cb53f80-7ae7-461b-a37f-b5a85fc1e769)

 - [resource](https://hackmd.io/@MingHung/StudyBook/%2F%40MingHung%2FFAPI#2112-Config-message-exchange-procedure)
- [blog resource](https://www.techplayon.com/5g-fapi-femtocell-application-programming-interface/)
 
 ## 2.1.1 INTIALIZATION 
 - This procedure moves the PHY from IDLE state to RUNNING state via CONFIGURED state
 - The different stages of initalization are :
   1. PARAM message exchange procedure
   2. CONFIG message exchange procedure
   3. START message exhange procedure

![vxFd9sV](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/90cd4860-e19b-4026-b7ec-585d3833eab8)

 - For SFN/SL Synchronization, the initialization procedure is completed when the PHY sends the L2/L3 software a SLOT.indication message.
- For Delay Management with Timestamps, the initialization procedure is completed when the PHY sends the L2/L3 software a START.response message.
- For Delay Management without Timestamps, the initialization procedure is completed when the PHY sends the L2/L3 software a TIMING.indication message.

## 2.1.1.1 PARAM message exchange procedure
- Its purpose is to allow the L2/L3 software to collect info about the PHY configuration an current state. (only in IDLE and CONFIGURED state)
- PHY returns the following info (PARAM.response) according to its current state

![KwfdWlq](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/5e572354-8604-492c-80f9-3a45769bae9e)
![P7p9uXU](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/97abe830-e7b2-44dd-81b8-9815c2e8f9b4)

- From the above figure , we can see that the PARAM message exchange is initiated by L2/L3 software sending a PARAM.request message to PHY.
- L2/L3 software may or may not (recommended) start a guard timer to wait for the response from L1 .
- If everything is going great PARAM.response is sent by PHY as a response
- In the IDLE and CONFIGURED states, this message will include the current PHY state and a list of configuration information
- In the RUNNING state, this message will indicate an INVALID_STATE error. To determine the PHY capabilities it must be moved to the CONFIGURED state using the termination procedure

- [TLV](https://devopedia.org/tlv-format) : TLV (Tag-Length-Value) is a binary format used to represent data in a structured way
![1688 1676742752](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/d6bf1ad1-36b4-4d0a-a7c7-90ec7559d330)

- if L2/L3 does not signal any TLVs , the message length in the genereic header = 0

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/d8b03246-25c7-49b0-8b8f-722e1993ad1d)
![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/6e07c463-df76-446a-aba7-7ed15cf047df)

- uint16_t : unassigned integer of 16 bits
- uint8_t : unassigned integer of 8 bits 

## 2.1.1.2 Config message exchange procedure
- Its purpose is to allow the L2/L3 software to configure the PHY.
- Can be used in any state though there are some small differences depending on PHY state
  1. If the PHY is in the IDLE state, the CONFIG.request message, sent by the L2/L3 software, must include all mandatory TLVs. The mandatory TLVs are indicated by the PHY in the PARAM.response message. If all mandatory TLVs are included, and set to values supported by the PHY, L1 will return a CONFIG.response message, indicating it is successfully configured and has moved to the CONFIGURED state. If the CONFIG.request message has missing mandatory TLVs, invalid TLVs, or unsupported TLVs, the PHY will return a CONFIG.response message, indicating an incorrect
  2. If the PHY is in the CONFIGURED state, the CONFIG.request message, sent by the L2/L3 software, may include only the TLVs that are required to change the PHY to a new configuration. If the PHY supports these new values, it will return a CONFIG.response message, indicating it has been successfully configured. However, if the CONFIG.request message includes invalid TLVs, or unsupported TLVs, the PHY will return a CONFIG.response message, indicating an incorrect configuration. In this case, all received TLVs will be ignored and the PHY will continue with its previous configuration. In both cases, if the PHY receives a CONFIG.request while in the CONFIGURED state it will remain in the CONFIGURED state.
  3. If the PHY is in the RUNNING state, then a limited subset of CONFIG TLVs may be sent in a CONFIG.request message. The permitted TLVs are indicated by the PHY in PARAM.response. If the CONFIG.request message has invalid TLVs, or TLVs which must not be reconfigured in the RUNNING state, the PHY will return a CONFIG.response message, indicating an incorrect configuration. In this case, it will remain in the RUNNING state and all received TLVs will be ignored.

![4XWZx44](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/0a6079f0-af44-487d-9745-8816f919fa21)
![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/ccc87332-cc24-4c20-ad59-54dd4f2ad3fb)
![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/c7e179bf-f165-4d2d-8e83-b08aeb24dc17)

## 2.1.1.3 Start message exchange procedure
- Its purpose is to instruct a configured PHY to start transmitting as a gNB.
- L2/L3 software initiates this procedure by sending a START.request message to the PHY
- If the PHY is in the CONFIGURED state, and it supports SFN/SL-based synchronization, it will issue a SLOT indication. After the PHY has sent its first **SLOT.indication** message, it enters the RUNNING state.
- If the PHY is in the CONFIGURED state, and it supports `Delay Management with Timestamps` (see section 2.2.1.1), it will issue a **START.response**, after which it enters the RUNNING state.
- If the PHY is in the CONFIGURED state, and it supports Delay Management without Timestamps (see section 2.2.1.2), it will issue a  **TIMING.indication**, after which it enters the RUNNING state.
- If the PHY receives a **START.request** in either the IDLE or RUNNING state, it will return an **ERROR.indication** including an **INVALID_STATE** error.

![nhqOidF](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/07e637a2-f4e5-4687-ac43-9df803929064)

## 2.1.2 Termination (stop)
- The termination procedure is used to move the PHY from the RUNNING state to the CONFIGURED state. This stops the PHY transmitting as a gNB.
- initiated by the L2/L3 software sending a **STOP.request** message.
- If the **STOP.request** message is received by the PHY while operating in the RUNNING state, it will stop all TX and RX operations and return to the CONFIGURED state. When the PHY has completed its stop procedure, a STOP.indication message is sent to the L2/L3 software.
- If the STOP.request message was received by the PHY while in the IDLE or
CONFIGURED state, it will return an **ERROR.indication** message including an **INVALID_STATE** error. However, in this case the PHY was already stopped.

![PBwLhZ7](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/0f505c92-28a7-4273-9461-f7d0d156683a)

## 2.1.3 Restart

- It can be used by the L2/L3 software When it needs to stop transmitting, but later wants to restart transmission using the same configuration.
- To complete this procedure, the L2/L3 software can follow the
STOP message exchange shown in Figure 2-6. This moves the PHY to the
CONFIGURED state. To restart transmission, it should follow the START message exchange, shown in Figure 2-5, moving the PHY back to the RUNNING state.

![j3L8Ool](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/3096aea9-5e23-4d8b-8632-f7d88cd2b89e)

## 2.1.4 Reset
- This procedure is used when the L2/L3 software wants to return the PHY to the IDLE state. Under normal conditions, this can only be achieved by terminating the PHY (as shown in Figure 2-6) and then resetting the PHY.
- When L2 detects P5 timeout, it instead invokes RESET.request directly.
- For a dedicated PHY or PHY Group contexts, the RESET procedure is complete when **RESET.indication** is received. For common context, the RESET procedure is complete when **CCONTEXT_READY.indication** is received.

![P2TIXoz](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/6c0bd858-18d2-43a8-b95f-954a93587ed0)

## 2.1.5 Reconfigure
- 2 Methods :
  1. a major reconfiguration where the PHY is stopped
  2. a minor reconfiguration where the PHY continues running

- Major Reconfig : It is used when the L2/L3 software wants to make significant changes to the configuration of the PHY
  - The STOP message exchange, shown in Figure 2-6, is followed to halt the PHY and move it to theCONFIGURED state. The CONFIG message exchange, shown in Figure 2-4, is used to reconfigure the PHY. Finally, the START message exchange, shown in Figure 2-5, is followed to start the PHY and return it to the RUNNING state.

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/dca8e80c-96ef-40f8-a17d-8fea22ac9fa6)


- Minor Reconfig : The minor reconfiguration procedure is shown in Figure 2-10. It is typically used in conjunction with a RRC system information update.
- In the slot where the L2/L3 software requires the configuration change it sends the CONFIG.request message to the PHY. Only a limited subset of CONFIG TLVs may be sent, these are indicated by the PHY in PARAM.response.
- Reconfiguring the PHY while in the RUNNING state has a further restriction, the CONFIG.request message must be sent before the DL_TTI.request and UL_TTI.request message.

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/ea64af9b-1817-4820-afc4-5ffb20eaa6e5)


## 2.1.6 Query
- It is used by the L2/L3 software to determine the configuration and operational status of the PHY
- The PARAM message exchange, shown in Figure 2-3, is used. This signalling sequence can be followed when the PHY is stopped, in the IDLE state and, optionally, the CONFIGURED state.

## 2.1.7 Notification
- The PHY sends a notification message when it has an event of interest for the L2/L3 software. Currently, there is one notification message called ERROR.indication.
- It is used by the PHY to indicate that the L2/L3 software has sent invalid information
to the PHY.

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/fd21b4fa-cab4-40ed-ba82-18721ffb7108)

## 2.1.8 Protocol Negotiation
- The procedure allows L2/L3 and PHY to ensure that the same FAPI version is used.
  1. **Step 1** : Protocol negotiation triggered by L2/L3 sending a **PARAM.request** message with a `protocolVersion` indicating a FAPI protocol version supported by L2/L3.
     - Note: typically, this would be the highest FAPI version that L2/L3 supports.
   2. **Step 2** : PHY replies to MAC with a **PARAM.response** message which contains :
      1. phyFapiProtocolVersion: the highest FAPI protocol version that PHY supports
      2. phyFapiNegotiatedProtocolVersion: the FAPI version that PHY assumes in subsequent P5/P7 exchanges with L2/L3.

- After step 2, both L2/L3 and PHY are assumed to use the same protocol version, as indicated by phyFapiNegotiatedProtocolVersion.
- **Protocol negotiation can only happen when all defined PHYs are in IDLE state.**

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/99eee73c-631f-4dcb-8572-31da8a850413)

- **PHY GROUPS** :The set of all PHYs supported by the PHY Layer is partitioned into PHY Groups. P5 APIs terminating in one PHY Group cannot impact or characterize other PHY Groups or PHYs belonging to other PHY Groups.

## 2.1.9 PHY Instantiation
- This process describes the PHY Profile discovery and selection process, which leads to defining PHYs (and corresponding PHY IDs).
  1. **Step 1 and 2 (PHY Profile Discovery)** : L2/L3 uses the PHY Query Procedure (steps 1 and 2 in the figure) towards Common or PHY Group Context (see section 2.1.10), to discover the supported PHY Profiles and a map indicating which PHY and DFE(digital front end) profiles are pairable.
     - Note: Some PHY implementations may pre-define PHY IDs (e.g. < 255), in which case this procedure is not needed
  2. **Step 3 and 4 (DFE profile Discovery)** : L2/L3 uses the DFE Query Procedure in SCF-223 [9] (steps 3 and 4 in the figure) towards DFE, to discover the supported DFE Profiles
  3. **Step 5 (PHY PROFILE SELECTION)** : L2/L3 selects a PHY profile , via the **CONFIG.reuest** message towards COmmon or PHY Group Context.
     - **Note: Common or PHY Group Context does not support PHY (IDLE, CONFIGURED, RUNNING) states, so the state diagram from Figure 2-1 does not apply to PHY ID#255.**
   4. **Step 6 and 7 (PHY definition)** : PHY IDs < 255 are defined (but cannot be configured), based on the selected profile (step 6).
      - CONFIG.response (step 7) announces successful configuration, if PHY Definition succeeds. If unsuccessful, an error code will indicate the failure cause and the PHY Instantiation fails.
   5. **Step 8 and 9 (DFE profile selection)** : L2/L3 selects a DFE profile, via the DFE **CONFIG.request** message (step 8).
      - DFE CONFIG.response (step 9) announces successful configuration. If unsuccessful, an error code will indicate the failure cause the PHY Instantiation fails.
   6. **Step 10 (FEU Configuration and initiallization)** : L2/L3 executes the Configuration and Initialization procedures towards DFE and RF (step 8).
      - The config and initialization procedures towards FEU is in SCF-225[10]
   7. **Step 11 (PHY instantiation)** : When the DFE and RF have both entered RUNNING state, PHY IDs defined through Profile selection become configurable (step 11), after successful DFE and PHY Profile selection.If newly defined, these PHY IDs may be considered IDLE.


- IF PHY IDs existed in any state (IDLE/CONFIGURED/RUNNING) prior to any of the PHY Profile Selection and DFE Profile Selection steps, they remain in the same states, as long as none of their capabilities or configurations are not impacted by the PHY or DFE Profile Selections, otherwise ERROR.indication will be triggered by these PHY IDs.

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/10d0f62d-d820-484b-86b4-df62f4c424b6)

## 2.1.10 Common and PHY Group Contexts
- When a supervisory PHY concept (e.g. PHY ID 255 or PNF in SCF-225 [10]) is supported, the Common Context is supported in this supervisory PHY.
- only terminates P5 but not P7
- Cannot be in PHY RUNNING state
- can be queried (section 2.1.6)
- can be configured
- can be reset
- The scope of a P5 API :
  1. A specific PHY : PHY ID is dedicated (eg PHY ID < 255) NO PHY group may be associated with the API
  2. Common Context : PHY Group Identifier is absent and PHY ID is common (eg PHY ID = 255)
  3. PHY Group context : PHY Group Identifieris present ; in this case PHY ID must be common (eg PHY ID =255)

## 2.1.11 PHY/FEU Interface
- In some cases for eg splt 7.2x PHY and FEU interaface may be subject to disconnection or synchronization events.These events may be observable at L2/L3 software, via PHY (P5 interface), or via FEU (P19-C interface in SCF-223 [9]).
- An L2 that can observe such events, shall take the following actions:
1. When a PHY’s associated FEU is determined to have become disconnected:
  - L2/L3 software shall transition the corresponding PHY and FEU to Idle, via the
  mechanisms in section 2.1.
  - L2/L3 software shall re-query the FEU’s capability (as well as any associated
PHY’s capability), after the FEU is determined to have been reconnected.
2. When a PHY or its associated FEU is determined to have become
desynchronized:
  - L2/L3 software shall stop any RUNNING PHY, via the mechanisms in section
  2.1
  - When the PHY and its associated FEU are both determined to be
  synchronized, L2 may transition the PHY to RUNNING state, via the
  mechanisms in section 2.1
- Query

![image](https://github.com/KRIISHSHARMA/FAPI/assets/86760658/3f4ff26e-f686-4b0e-9712-776f6219edc1)

# 2.2 SLOT PROCEDURE (P7) 
- Used to control control the DL and UL frame structure
- Used to transfer slot data between the L2/L3 software and PHY.
- Slot procedures supported by the PHY API are :
  1. Transmission of a 62.5us, 125us, 250us, 500us or 1ms SLOT message
  2. Synchronization of SFN/Slot between the L2/L3 software and PHY
  3. Transmission of the BCH transport channel
  4. Transmission of the PCH transport channel
  5. Transmission of the DL-SCH transport channel
  6. Transmission of the downlink control information (DCI)
  7. Transmission of the CSI reference signal
  8. Reception of the RACH transport channel
  9. Reception of the UL-SCH transport channel
  10. Reception of the uplink control information (UCI)
  11. Reception of the sounding reference signal

- P7 messages - Main data path interface
  1. DL_TTI.request
  2. UL_TTI.request
  3. SLOT.indication
  4. UL_DCI.request
  5. TX_Data.request
  6. RX_Data.indication
  7. CRC.indication
  8. UCI.indication
  9. RACH.indication

# 2.2.1 DELAY MANAGEMENT 
- This section describes two delay management mechanisms, based on receive window maintained at L1, per message type.
- Note that receive windows are anchored to slots. The slot being anchored to is specific to each of the PDU(s) carried in the message.
- In simpler terms, this section is talking about two ways to manage delays in a communication system. The delays are based on something called a "receive window," which is like a time frame during which a message is expected to be received.
- Imagine you're sending a message that contains different types of information. For example, let's say you're sending a message that includes both a picture and a video. Each type of information has its own time frame (receive window) during which it should be received.

  -  e.g. if a [DL_TTI](https://devopedia.org/5g-nr-transmission-time-interval).request carries a 15 kHz PDSCH PDU and a 30 kHz SSB PDU, the 15 PDSCH PDU reception shall be handled according to the Rx window for the 15 kHz slot and the SSB PDU reception shall be handled according to the Rx window for the 30 kHz slot, relevant to the DL_TTI.request message.
 
  -  So, in the example given, if your message includes a 15 kHz picture and a 30 kHz video, each part of the message has its own specific time frame for when it should be received. The system is designed to handle the reception of the 15 kHz picture based on a certain time frame (anchored to a slot related to 15 kHz), and the 30 kHz video is handled based on a different time frame (anchored to a slot related to 30 kHz).
 
  -  Essentially, it's a way to make sure that different types of information within a message are processed and received at the right times, depending on their specific characteristics.

















