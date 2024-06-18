# Conceptos_kotlin

//Define las propiedades de la clase

/*class SmartDevice(val nombre: String, val categoria: String) {

     var speakerVolume = 2
     
      set(value) {
      
        if (value in 0..100) {
        
            field = value
                            }
                            
                    }
                    
    var estadoDelDispositivo = "en linea"
    
       fun turnOn(){
       
        println("el dispositivo inteligente esta encendido.")
        
   }
       fun turnOff() {
       
        println("el dispositivo inteligente esta apagado.")
        
    }
    
}

fun main() {

      val smartTvDevice = SmartDevice("android tv","Entertainment")
      
      println("El nombre del dispositivo es: ${smartTvDevice.nombre}")
      
      smartTvDevice.turnOn()
      
      smartTvDevice.turnOff()
      
}*/
//Anula métodos de superclase de subclases

/*open class SmartDevice(val name: String, val category: String) {


    var deviceStatus = "online"
    
    open fun turnOn() {
    
        println("El dispositivo inteligente está encendido.")
        
    }
    

    open fun turnOff() {
    
        println("El dispositivo inteligente está apagado.")
        
    }
    

}


class SmartTvDevice(deviceName: String, deviceCategory: String) :

    SmartDevice(name = deviceName, category = deviceCategory) {
    


    var speakerVolume = 2
    
        set(value) {
        
            if (value in 0..100) {
            
                field = value
                
            }
            
        }
        

    var channelNumber = 1
    
        set(value) {
        
            if (value in 0..200) {
            
                field = value
                
            }
            
        }
        

    fun increaseSpeakerVolume() {
    
        speakerVolume++
        
        println("Speaker volume increased to $speakerVolume.")
        
    }
    

    fun nextChannel() {
    
        channelNumber++
        
        println("Channel number increased to $channelNumber.")
        
    }
    

    override fun turnOn() {
    
        deviceStatus = "on"
        
        println(
        
            "$name is turned on. Speaker volume is set to $speakerVolume and channel number is " +
            
                "set to $channelNumber."
                
        )
        
    }
    

    override fun turnOff() {
    
        deviceStatus = "off"
        
        println("$name turned off")
        
    }
    
}


class SmartLightDevice(deviceName: String, deviceCategory: String) :

    SmartDevice(name = deviceName, category = deviceCategory) {
    
    var brightnessLevel = 0
    
        set(value) {
        
            if (value in 0..100) {
            
                field = value
                
            }
            
        }
        

    fun increaseBrightness() {
    
        brightnessLevel++
        
        println("Brightness increased to $brightnessLevel.")
        
    }
    

    override fun turnOn() {
    
        deviceStatus = "on"
        
        brightnessLevel = 2
        
        println("$name turned on. The brightness level is $brightnessLevel.")
        
    }


    override fun turnOff() {
    
        deviceStatus = "off"
        
        brightnessLevel = 0
        
        println("Smart Light turned off")
        
    }
    
}


class SmartHome(val smartTvDevice: SmartTvDevice,

                val smartLightDevice: SmartLightDevice) {
                

    fun turnOnTv() {
    
        smartTvDevice.turnOn()
    }
    

    fun turnOffTv() {
    
        smartTvDevice.turnOff()
    }
    

    fun increaseTvVolume() {
    
        smartTvDevice.increaseSpeakerVolume()
    }
    

    fun changeTvChannelToNext() {
    
        smartTvDevice.nextChannel()
    }
    
    fun turnOnLight() {
    
        smartLightDevice.turnOn()
    }

    fun turnOffLight() {
    
        smartLightDevice.turnOff()
    }
    
    fun increaseLightBrightness() {
    
        smartLightDevice.increaseBrightness()
    }
    
    fun turnOffAllDevices() {
    
        turnOffTv()
        
        turnOffLight()
        
    }
}

fun main() {

    var smartDevice: SmartDevice = SmartTvDevice("Android TV", "Entertainment")
    
    smartDevice.turnOn()
    
    
    smartDevice = SmartLightDevice("Google Light", "Utility")
    
    smartDevice.turnOn()
    
}*/

//Prueba la solución


/*import kotlin.properties.ReadWriteProperty

import kotlin.reflect.KProperty



open class SmartDevice(val name: String, val category: String) {


    var deviceStatus = "online"
    
        protected set
        

    open val deviceType = "unknown"
    

    open fun turnOn() {
    
        deviceStatus = "on"
        
    }
    

    open fun turnOff() {
    
        deviceStatus = "off"
        
    }
    
}


class SmartTvDevice(deviceName: String, deviceCategory: String) :

    SmartDevice(name = deviceName, category = deviceCategory) {


    override val deviceType = "Smart TV"
    

    private var speakerVolume by RangeRegulator(initialValue = 2, minValue = 0, maxValue = 100)
    

    private var channelNumber by RangeRegulator(initialValue = 1, minValue = 0, maxValue = 200)
    


    fun increaseSpeakerVolume() {
    
        speakerVolume++
        
        println("Speaker volume increased to $speakerVolume.")
        
    }


    fun nextChannel() {
    
        channelNumber++
        
        println("Channel number increased to $channelNumber.")
        
    }


    override fun turnOn() {
    
        super.turnOn()
        
        println(
        
            "$name is turned on. Speaker volume is set to $speakerVolume and channel number is " +
            
                "set to $channelNumber."
                
        )
        
    }
    

    override fun turnOff() {
    
        super.turnOff()
        
        println("$name turned off")
        
    }
    
}


class SmartLightDevice(deviceName: String, deviceCategory: String) :

    SmartDevice(name = deviceName, category = deviceCategory) {
    

    override val deviceType = "Smart Light"
    

    private var brightnessLevel by RangeRegulator(initialValue = 0, minValue = 0, maxValue = 100)
    

    fun increaseBrightness() {
    
        brightnessLevel++
        
        println("Brightness increased to $brightnessLevel.")
        
    }
    

    override fun turnOn() {
    
        super.turnOn()
        
        brightnessLevel = 2
        
        println("$name turned on. The brightness level is $brightnessLevel.")
        
    }
    

    override fun turnOff() {
    
        super.turnOff()
        
        brightnessLevel = 0
        
        println("Smart Light turned off")
        
    }
    
}

class SmartHome(

    val smartTvDevice: SmartTvDevice,
    
    val smartLightDevice: SmartLightDevice
    
) {



    var deviceTurnOnCount = 0
    
        private set
        

    fun turnOnTv() {
    
        deviceTurnOnCount++
        
        smartTvDevice.turnOn()
        
    }
    

    fun turnOffTv() {
    
        deviceTurnOnCount--
        
        
        smartTvDevice.turnOff()
        

        
    }
    

    fun increaseTvVolume() {
    
        smartTvDevice.increaseSpeakerVolume()
        
    }
    

    fun changeTvChannelToNext() {
    
        smartTvDevice.nextChannel()
        
    }


    fun turnOnLight() {
    
        deviceTurnOnCount++
        
        smartLightDevice.turnOn()
        
    }
    

    fun turnOffLight() {
    
        deviceTurnOnCount--
        
        smartLightDevice.turnOff()
        
    }


    fun increaseLightBrightness() {
    
        smartLightDevice.increaseBrightness()
        
    }
    

    fun turnOffAllDevices() {
    
        turnOffTv()
        
        turnOffLight()
        
    }
    
}


class RangeRegulator(

    initialValue: Int,
    
    private val minValue: Int,
    
    private val maxValue: Int
    
) : ReadWriteProperty<Any?, Int> {


    var fieldData = initialValue
    

    override fun getValue(thisRef: Any?, property: KProperty<*>): Int {
    
        return fieldData
        
    }
    

    override fun setValue(thisRef: Any?, property: KProperty<*>, value: Int) {
    
        if (value in minValue..maxValue) {
        
            fieldData = value
            
        }
        
    }
    
}

fun main() {

    var smartDevice: SmartDevice = SmartTvDevice("Android TV", "Entertainment")
    
    smartDevice.turnOn()
    

    smartDevice = SmartLightDevice("Google Light", "Utility")
    
    smartDevice.turnOn()
    
}
*/

// prueba del desafio

/*
import kotlin.properties.ReadWriteProperty

import kotlin.reflect.KProperty


open class SmartDevice(val name: String, val category: String) {


    var deviceStatus = "online"
    

    open val deviceType = "unknown"
    
    
    var deviceTurnOnCount = 0
    


    open fun turnOn() {
    
        deviceStatus = "on"
        
        deviceTurnOnCount++
        
    }
    

    open fun turnOff() {
    
        deviceStatus = "off"
        
    }
    
    
    fun printDeviceInfo() {
    
        println("Device name: $name, category: $category, type: $deviceType")
        
    }
    
}


class SmartTvDevice(deviceName: String, deviceCategory: String) :

    SmartDevice(name = deviceName, category = deviceCategory) {
    

    override val deviceType = "Smart TV"
    

    private var speakerVolume by RangeRegulator(initialValue = 2, minValue = 0, maxValue = 100)
    

    private var channelNumber by RangeRegulator(initialValue = 1, minValue = 0, maxValue = 200)
    

    fun increaseSpeakerVolume() {
    
        if (deviceStatus == "on") {
        
            speakerVolume++
            
            println("Speaker volume increased to $speakerVolume.")
            
        } else {
        
            println("TV is off. Cannot increase volume.")
            
        }
        
    }


    fun nextChannel() {
    
        if (deviceStatus == "on") {
        
            channelNumber++
            
            println("Channel number increased to $channelNumber.")
            
        } else {
        
            println("TV is off. Cannot change channel.")
            
        }
        
    }
    
        
    fun decreaseVolume() {
    
        if (deviceStatus == "on") {
        
            if (speakerVolume > 0) {
            
                speakerVolume--
                
                println("Speaker volume decreased to $speakerVolume.")
                
            }
            
        } else {
        
            println("TV is off. Cannot decrease volume.")
            
        }
        
    }
    
            
    fun previousChannel() {
    
        if (deviceStatus == "on") {
        
            if (channelNumber > 1) {
            
                channelNumber--
                
                println("Channel number decreased to $channelNumber.")
                
            }
            
        } else {
        
            println("TV is off. Cannot change channel.")
            
        }
        
    }
    

    override fun turnOn() {
    
        super.turnOn()
        
        println(
        
            "$name is turned on. Speaker volume is set to $speakerVolume and channel number is " +
            
                "set to $channelNumber."
                
        )
        
    }
    

    override fun turnOff() {
    
        super.turnOff()
        
        println("$name turned off")
        
    } 
    
}


class SmartLightDevice(deviceName: String, deviceCategory: String) :

    SmartDevice(name = deviceName, category = deviceCategory) {
    

    override val deviceType = "Smart Light"
    

    private var brightnessLevel by RangeRegulator(initialValue = 0, minValue = 0, maxValue = 100)
    

    fun increaseBrightness() {
    
        if (deviceStatus == "on") {
        
            brightnessLevel++
            
            println("Brightness increased to $brightnessLevel.")
            
        } else {
        
            println("Light is off. Cannot increase brightness.")
            
        }
        
    }
    
    
    fun decreaseBrightness() {
    
        if (deviceStatus == "on") {
        
            if (brightnessLevel > 0) {
            
                brightnessLevel--
                
                println("Brightness decreased to $brightnessLevel.")
                
            }
            
        } else {
        
            println("Light is off. Cannot decrease brightness.")
            
        }
        
    }
    
    
    override fun turnOn() {
    
        super.turnOn()
        
        brightnessLevel = 2
        
        println("$name turned on. The brightness level is $brightnessLevel.")
        
    }
    

    override fun turnOff() {
    
        super.turnOff()
        
        brightnessLevel = 0
        
        println("Smart Light turned off")
        
    }
    
}


class SmartHome(

    val smartTvDevice: SmartTvDevice,
    
    val smartLightDevice: SmartLightDevice
    
) {


    fun turnOnTv() {
    
        smartTvDevice.turnOn()
        
    }
    

    fun turnOffTv() {
    
        smartTvDevice.turnOff()
        
    }
    

    fun increaseTvVolume() {
    
        smartTvDevice.increaseSpeakerVolume()
        
    }
    
    
    fun decreaseTvVolume() {
    
        smartTvDevice.decreaseVolume()
        
    }
    

    fun changeTvChannelToNext() {
    
        smartTvDevice.nextChannel()
        
    }

    
    fun changeTvChannelToPrevious() {
    
        smartTvDevice.previousChannel()
        
    }
    
    
    fun printSmartTvInfo() {
    
        smartTvDevice.printDeviceInfo()
        
    }
    


    fun turnOnLight() {
    
        smartLightDevice.turnOn()
        
    }
    

    fun turnOffLight() {
    
        smartLightDevice.turnOff()
        
    }
    

    fun increaseLightBrightness() {
    
        smartLightDevice.increaseBrightness()
        
    }
    
    
    fun decreaseLightBrightness() {
    
        smartLightDevice.decreaseBrightness()
        
    }
    

    
    fun printSmartLightInfo() {
    
        smartLightDevice.printDeviceInfo()
        
    }
    


    fun turnOffAllDevices() {
    
        turnOffTv()
        
        turnOffLight()
        
    }
    
    
}


class RangeRegulator(

    initialValue: Int,
    
    private val minValue: Int,
    
    private val maxValue: Int
    
) : ReadWriteProperty<Any?, Int> {



    private var fieldData = initialValue
    


    override fun getValue(thisRef: Any?, property: KProperty<*>): Int {
    
        return fieldData
        
    }
    

    override fun setValue(thisRef: Any?, property: KProperty<*>, value: Int) {
    
        if (value in minValue..maxValue) {
        
            fieldData = value
            
        }
        
    }
    
}


fun main() {

    val smartTv = SmartTvDevice("Android TV", "Entertainment")
    
    val smartLight = SmartLightDevice("Philips Hue", "Lighting")
    
    val smartHome = SmartHome(smartTv, smartLight)
    

    
    smartHome.turnOnTv()
    
    smartHome.increaseTvVolume()
    
    smartHome.decreaseTvVolume()
    
    smartHome.changeTvChannelToNext()
    
    smartHome.changeTvChannelToPrevious()
    
    smartHome.printSmartTvInfo()
    


    smartHome.turnOnLight()
    
    smartHome.increaseLightBrightness()
    
    smartHome.decreaseLightBrightness()
    
    smartHome.printSmartLightInfo()
    

    smartHome.turnOffAllDevices()
    
}
*/
