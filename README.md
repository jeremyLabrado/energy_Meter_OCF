# energy_Meter_OCF

///////////////////////////////////////////////////////////////////////////

# Files

## Electrical Meter 
*Resource Json. 
**Electricity consumption - oic.r.electricity.consumption.json. 
**Electricity usage – oic.r.electricity.usage.json. 
**Electricity price - oic.r.electricity.price.json. 
**Electricity tariff - oic.r.electricity.tariff.json. 

*API Raml 
**Electricity consumption – electricityLiveConsumption.raml 
**Electricity usage – electricityUsage.raml 
**Electricity price – electricityPrice.raml 
**Electricity tariff - electricityTariff.raml 

## Battery Storage. 
*API Raml 
**Battery - battery.raml 

*Resource Json. 
**Battery Update - oic.r.energy.battery-Update.json. 
**Battery - oic.r.energy.battery.json. 
 
///////////////////////////////////////////////////////////////////////////
#	Architecture

## Electrical Meter

###Electricity Consumption ->  OICElectricityConsumption.raml
|
|+Electrical Energy Consumption.json -> (oic.r.electricity.consumption.json)
| |----Instantaneous power: Number in W
| |----Electrical energy consumed: Number in Wh
|
 

###Electricity Usage -> OICElectricityUsage.raml
|
|+Electrical Energy Consumption.json -> (oic.r.electricity.consumption.json)
| |----Instantaneous power: Number in W
| |----Electrical energy consumed: Number in Wh
|
|+TimePeriod .json -> (oic.r.time.period.json)
| |----stop time: String ISO8601
| |----start time: String ISO8601
| |----interval: Number in minutes
 

###Electricity Price ->   OICElectricityPrice.raml
|
|+Electricity Price.json -> oic.r.electricity.price.json
| |----Price: Number in currency units per kWh
| |----Currency: String
 
###Electricity Tariff  -> OICElectricityTariff.raml
|
|+Electricity Price.json -> oic.r.electricity.price.json
| |----Price: Number in currency units per kWh  
| |----Currency: String
|
|+TimePeriod .json -> (oic.r.time.period.jsonI als)
| |----stop time: String ISO8601
| |----start time: String ISO8601
| |----interval: Number in minutes  

##   Battery

###Electricity Battery ->   battery.raml
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
