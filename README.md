# energy_Meter_OCF

____

# Files
## Electrical Meter 
| Title | File |
|------------------------|--------------------------------|
|Electricity consumption | oic.r.electricity.consumption.json |
|Electricity usage       | oic.r.electricity.usage.json |
|Electricity price       | oic.r.electricity.price.json |
|Electricity tariff      | oic.r.electricity.tariff.json |
|------------------------|--------------------------------|
|Electricity consumption | electricityLiveConsumption.raml| 
|Electricity usage       | electricityUsage.raml |
|Electricity price       | electricityPrice.raml |
|Electricity tariff      | electricityTariff.raml |

## Battery Storage. 
 
| Title | File |
|------------------------|--------------------------------|
|Battery                 | battery.raml 
|------------------------|--------------------------------|
|Battery Update          | oic.r.energy.battery-Update.json|
|Battery                 | oic.r.energy.battery.json. |
 
___
# Architecture

## Electrical Meter

### Electricity Consumption ->  OICElectricityConsumption.raml
<pre>
Electricity Consumption ->  OICElectricityConsumption.raml
|
|+Electrical Energy Consumption.json -> (oic.r.electricity.consumption.json)
| |----Instantaneous power: Number in W
| |----Electrical energy consumed: Number in kWh
|
</pre>
 

### Electricity Usage -> OICElectricityUsage.raml
<pre>
Electricity Usage -> OICElectricityUsage.raml
|
|+Electrical Energy Consumption.json -> (oic.r.electricity.consumption.json)
| |----Instantaneous power: Number in W
| |----Electrical energy consumed: Number in kWh
|
|+TimePeriod .json -> (oic.r.time.period.json)
| |----stop time: String ISO8601
| |----start time: String ISO8601
| |----interval: Number in minutes
</pre>

### Electricity Price ->   OICElectricityPrice.raml
<pre>
Electricity Price ->   OICElectricityPrice.raml
|
|+Electricity Price.json -> oic.r.electricity.price.json
| |----Price: Number in currency units per kWh
| |----Currency: String ISO4217 
</pre>

 
 ### Electricity Tariff  -> OICElectricityTariff.raml
<pre>
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
</pre>


## Battery

### Electricity Battery ->   battery.raml
<pre>
Electricity Battery ->   battery.raml
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
</pre>

