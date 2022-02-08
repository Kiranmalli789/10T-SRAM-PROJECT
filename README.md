# Design of 10T SRAM with improved READ speed
* In this project we are trying to improve the Read speed and other undesirable limitations of conventional 6T-SRAM by using 10T-SRAM.

# Table of Contents

1.[Introduction](#Introduction)

2.[Circuit Design and Details](#Circuit-Design-and-Details)

3.[Circuit Operation](#Circuit-Operation)
   
4.[Simulation Waveforms](#Simulation-Waveforms)

5.[Conclution](#Conclution)

6.[References](#References)

## Introduction

Now-a-days among different memory elements SRAM(Static Random Access Memory) became very popular because of their high speed operations and low power consumption.
The most common SRAM cell used in todays applications are 6T SRAM.Even through it has low power consumption and high speed operation compared other memory elements
like DRAM,the read operation in 6T SRAM is still slow because of the time taken by the access transistors to access the memory part(latch) of the SRAM, which 
further results in increase of leakage power.So,In this paper we have discussed about the 10T SRAM which has low leakage power, high read operation speed,avoid 
noise in read operation and solves the limitations of conventional 6T SRAM.

## Circuit Design and Details
![schemetic](https://user-images.githubusercontent.com/99113992/152672756-90464ca6-c8ab-463e-8705-fd436b57b6cb.PNG)

The 10T SRAM circuit is shown in fig.1.This circuit avoids the read operation noise by isolating the memory part(latch) of the cell from external environment by 
disabling the access transistors during read operation and the memory read operation is done by additing additional circuit connected to the Q.By this process we can
also improve the read operation speed of SRAM since we are not using access transistors for measuring memory read operation and hence the leakage current is decreased.

## Circuit Operation

There are three modes of operation of 10T SRAM:

1.Stand-by mode: When Wordline(WL) = 0 and Read enable(RE) = 0,then the memory part became isolated from external environment and the data present in it remains same.
                 Therefore no read or write operation takes place.

2.Memory Read: When RE=1, then the Transmission gate is in active condition and the RDout gets the inverted value of Q(i.e, Qb) through the Transmission gates.And we off the                    access transistors during the memory read operation to reduce the leakage power. 

3.Memory write: When WL=1, then the write operation is possible.If BL=0, then PM0 transistor will "ON" and Qb becomes 1 and Q becomes 0.
                Similarly  if BL=1,then Q becomes 1 and Qb becomes 0.

Since Memory write operation still uses the access transistors unlike Memory operation, the Memory write operation will be slower when compared to memory read operation.

The main advantage of this 10T SRAM is that it doesn't require the precharge capacitors connected to a sense amplifier for memory read/write operation as that of 6T SRAM,
because here the data stored in memory is directly passes through the inverter and transmision gates.And also the charging or discharging of RDout happens only when the 
RDout changes,i.e, there is no power is consumed or dissipated if the next data is same as that of previous value.Therefore, this design of 10T SRAM reduces the 
consumption of when consecutive readout values are same.

## Simulation Waveforms

### 1.Write Operation

As we have discussed earlier when WL=1,then the write operation is possible and the Q gets the BL value and Qb gets the inverted value of Q.And when WL=0,the data stored in
the memory element doesn't change because of the access transistors are in inactive state.

![write operation](https://user-images.githubusercontent.com/99113992/152926807-6d204d6f-d516-4b4b-bc15-90d63d32310e.PNG)

### 2.READ Operation

When RE=1 and REB=0, then the READ operation will takes place with the Transmission gate is in active state and the the data present in the memory element(Q) is passed through the inverter and then transimission gate to the RD terminal.Note that the RD terminal gets the inverted value of Q(i.e, Qb) because of the inverter, but if we want the Q to 
comeout at the RD terminal we need to connect that extra circuit to the Qb instead of Q.

![READ output](https://user-images.githubusercontent.com/99113992/152926529-253768c3-2502-4da1-b278-3e1437624971.PNG)

Note that there is a small disturbance in the RD terminal during when the transmission gate is in off state(i.e, when RE=0 and REB=1), it's because when the transmission gate is in inactive condition there will be some leakage current since both of the nmos and pmos is in off state and moreover what we actually interested is during when transmission gate is in active state at which the READ Operation will takes place, So it doesn't matter to us when the transmission gate is in inactive state even if there is small disturbance in the output waveform. 

## Conclution

## References

PN.V.Kiran, N.Saxena, "Parameter Analysis of different SRAM Cell Topologies and Design of 10T SRAM Cell at 45nm Technology with Improved Read Speed",International Journal of Hybrid Information Technology,Vol.9, No.2 (2016).
