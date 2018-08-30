# energy_Meter_OCF

///////////////////////////////////////////////////////////////////////////

# Table of Contents

1.  	Architecture. 
1.1.   	Electrical Meter 
1.2.   	Battery

2.  	Electrical Meter 
2.1.   	Resource Json. 
2.1.1.    	Electricity consumption - oic.r.electricity.consumption.json. 
2.1.2.    	Electricity usage – oic.r.electricity.usage.json. 
2.1.3.    	Electricity price - oic.r.electricity.price.json. 
2.1.4.    	Electricity tariff - oic.r.electricity.tariff.json. 

2.2.   	API Raml 
2.2.1.    	Electricity consumption – electricityLiveConsumption.raml 
2.2.2.    	Electricity usage – electricityUsage.raml 
2.2.3.    	Electricity price – electricityPrice.raml 
2.2.4.    	Electricity tariff - electricityTariff.raml 

3.  	Battery Storage. 
3.1.   	API Raml 
3.1.1.    	Battery - battery.raml 

3.2.   	Resource Json. 
3.2.1.    	Battery Update - oic.r.energy.battery-Update.json. 
3.2.2.    	Battery - oic.r.energy.battery.json. 
 
///////////////////////////////////////////////////////////////////////////
1. 	Architecture
1.1.   Electrical Meter

Electricity Consumption ->  OICElectricityConsumption.raml
|
|+Electrical Energy Consumption.json -> (oic.r.electricity.consumption.json)
| |----Instantaneous power: Number in W
| |----Electrical energy consumed: Number in Wh
|
 
Electricity Usage -> OICElectricityUsage.raml
|
|+Electrical Energy Consumption.json -> (oic.r.electricity.consumption.json)
| |----Instantaneous power: Number in W
| |----Electrical energy consumed: Number in Wh
|
|+TimePeriod .json -> (oic.r.time.period.json)
| |----stop time: String ISO8601
| |----start time: String ISO8601
| |----interval: Number in minutes
 
Electricity Price ->   OICElectricityPrice.raml
|
|+Electricity Price.json -> oic.r.electricity.price.json
| |----Price: Number in currency units per kWh
| |----Currency: String
 
Electricity Tariff  -> OICElectricityTariff.raml
|
|+Electricity Price.json -> oic.r.electricity.price.json
| |----Price: Number in currency units per kWh  
| |----Currency: String
|
|+TimePeriod .json -> (oic.r.time.period.jsonI als)
| |----stop time: String ISO8601
| |----start time: String ISO8601
| |----interval: Number in minutes  

1.2.   Battery
Electricity Battery ->   battery.raml
|
|+Battery -> oic.r.energy.battery.json
| |----Charge: Number in percentage
| |----Capacity: Number in Ah
| |----Charging: Boolean
| |----Discharging: Boolean
| |----LowBattery: Boolean
| |----BatteryThreshold: Number in percentage
|
|+BatteryUpdate ->oic.r.energy.battery-Update.json
| |----BatteryThreshold: Number in percentage
|
