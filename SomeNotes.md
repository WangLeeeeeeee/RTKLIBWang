## Models 
### Time System
RTKLIB uses GPS Time for GNSS data handling to avoid leap seconds in UTC. GPST is expressed as GPS week number and time of week (TOW) since the start epoch of 00:00:00 UTC on January 6, 1980. 
#### GPST and UTC
The conversion of GPST to UTC is to subtract the leap seconds ($\Delta t_{LS}$)

$$ t_{UTC} = t_{GPS} - \Delta t_{LS} $$

the $t_{LS}$ can be found by the table.
### 

