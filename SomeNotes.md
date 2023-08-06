## Models 
### Time System
RTKLIB uses GPS Time for GNSS data handling to avoid leap seconds in UTC. GPST is expressed as GPS week number and time of week (TOW) since the start epoch of 00:00:00 UTC on January 6, 1980. 
#### GPST and UTC
The conversion of GPST to UTC is to subtract the leap seconds ($\Delta t_{LS}$)

$$ t_{UTC} = t_{GPS} - \Delta t_{LS} $$

the $t_{LS}$ can be found by the table.
### GLONASST
GLONASST is based on UTC and includes leap second insertion, and is also aligned to the local time.

$$t_{UTC}=t_{GLONASST}-10800$$

### GST (Galileo System Time)
GST start epoch is 00:00:00 UTC on August 22, 1999. At the start epoch, GST shall be ahead of UTC by 13 seconds. The GST is aligned to GPST except for the 1024 weeks difference of the time system origin and a small time offset (GGTO).
### QZSST
QZSST is aligned to GPST. It can be handled as the same as GPST.
### BDT
BDT is a continuous time system without leap second insertion. The start epoch of BDT is 00:00:00 UTC on January 1, 2006. 

$$ t_{BDT} = t_{GPST} - 14 $$
 

