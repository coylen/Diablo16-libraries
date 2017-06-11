# Diablo16-libraries

A selection of Libraries to aid in the use of chips and modules which use I2C communications and Diablo16 based intelligent display boards from 4D systems.  

## i2c.lib

A library of helper functions to bridge between the basic internal I2C functions in the Diablo16 chip and the higher level communications neccessary to interoperate with I2C based modules.  All commands come in two forms one with the i2c channel 1,2 or 3 as a variable and a second individual command for each of the three channels, the value x in the prototype function being replaces with the i2c channel number.  

#### I2C_is_ready(var i2c, var addr), I2Cx_is_ready(var addr)
Function which tests an individual address to check for response, to indicate the device is attached and ready.  
inputs: addr - address of the I2C device to be tested
return: 1 if responsive, 0 if not responsive 

#### I2C_scan(var i2c, var &devices), I2Cx_scan(var &devices)
Function to scan the bus and return a list of all devices active on the bus.  
inputs: &devices - address of array to hold the detected devices  
output: devices - an array of the detected devices  
return: number of detected dvices  

#### I2C_readbytes(var i2c, var addr, var nbytes, var &buf), I2Cx_readbytes(var addr, var nbytes, var &buf)
Function to read a defined number of bytes from an I2C device.  
inputs: addr - address of the device  
        nbytes - number of bytes to read  
        &buf - address of array to return the read bytes  
output: buf - an array of the returned bytes with each byte occupying the lower byte of each word of the array  
return: 1 if successful, 0 if unsuccessful  

#### I2C_writebytes(var i2c, var addr, var nbytes, var &buf), I2Cx_writebytes(var addr, var nbytes, var &buf)
Function to write a defined number of bytes to an I2C device.  
inputs: addr - address of the device  
        nbytes - number of bytes to write  
        &buf - address of array to write, bytes occupy lower byte of each word in the array.  
return: 1 if successful, 0 if unsuccessful  

#### I2C_readbytes_mem(var i2c, var addr, var memaddr, var nbytes, var &buf), 
#### I2Cx_readbytes_mem(var addr, var memaddr, var nbytes, var &buf)
Function to read a defined number of bytes from a specified memory address on an I2C device.  
inputs: addr - address of the device  
        memaddr - register within the i2c device (8bits)  
        nbytes - number of bytes to read  
        &buf - address of array to return the read bytes  
output: buf - an array of the returned bytes with each byte occupying the lower byte of each word of the array  
return: 1 if successful, 0 if unsuccessful  

#### I2C_writebytes_mem(var i2c, var addr, var memaddr, var nbytes, var buf),
#### I2Cx_writebytes_mem(var addr, var memaddr, var nbytes, var buf)
Function to write a defined number of bytes to specified register on an I2C device.  
inputs: addr - address of the device  
        memaddr - register within the i2c device (8bits)  
        nbytes - number of bytes to write  
        &buf - address of array to write, bytes occupy lower byte of each word in the array.  
return: 1 if successful, 0 if unsuccessful  

#### I2C_readwords(var i2c, var addr, var nwords, var &buf), I2Cx_readwords(var addr, var nwords, var &buf)
Function to read a defined number of words from an I2C device.  
inputs: addr - address of the device  
        nbytes - number of words to read  
        &buf - address of array to return the read words  
output: buf - an array of the returned words  
return: 1 if successful, 0 if unsuccessful  

#### I2C_writewords(var i2c, var addr, var nwords, var &buf), I2Cx_writewords(var addr, var nwords, var &buf)
Function to write a defined number of words from an I2C device.  
inputs: addr - address of the device  
        nbytes - number of words to write  
        &buf - address of array of words to write  
return: 1 if successful, 0 if unsuccessful  

#### I2C_readwords_mem(var i2c, var addr, var memaddr, var nwords, var &buf),
#### I2Cx_readwords_mem(var addr, var memaddr, var nwords, var &buf)
Function to read a defined number of words from a specified memory address on an I2C device.  
inputs: addr - address of the device  
        memaddr - register within the i2c device (8bits)  
        nbytes - number of words to read  
        &buf - address of array to return the read words  
output: buf - an array of the returned words  
return: 1 if successful, 0 if unsuccessful  

#### I2C_writewords_mem(var i2c, var addr, var memaddr, var nwords, var &buf),
#### I2Cx_writewords_mem(var addr, var memaddr, var nwords, var &buf)
Function to wriet a defined number of words from a specified memory address on an I2C device.  
inputs: addr - address of the device  
        memaddr - register within the i2c device (8bits)  
        nbytes - number of words to write  
        &buf - address of array of words to write  
return: 1 if successful, 0 if unsuccessful  

#### I2C_readbytes_mem16(var addr, var memaddr, var nbytes, var &buf)
#### I2C_writebytes_mem16(var addr, var memaddr, var nbytes, var &buf)
#### I2C_readwords_mem16(var addr, var memaddr, var nbytes, var &buf)
#### I2C_writewords_mem16(var addr, var memaddr, var nbytes, var &buf)
As per previous function descriptions but with a 16bit register address  


## DS1307.lib
Library of functions for use with the DS1307 Real time clock chip.  When using this library a global variable DS1307_Address holds the I2C channel on which I2C communications will take place.  This removes the need to have this as an input variable to each of the functions.  the default value of DS1307_Address is 1.  

#### bcd_to_int(var bcd)
#### int_to_bcd(var intvalue)
Internal helper functions to translate binary coded decimal to integer and vice versa  

#### RTC_GetSeconds()
Function to read the current seconds off the RTC Device  
returns: the number of seconds or -1 if an error occurs  

#### RTC_SetSeconds(var seconds)
Function to set the seconds on the RTC device  
Inputs: seconds - data to write to the RTC device  
returns: 1 if successful, 0 if unsuccessful  

#### RTC_GetMinutes()
Function to read the current minutes off the RTC Device  
returns: the number of minutes or -1 if an error occurs  

#### RTC_SetMinutes(var minutes)
Function to set the minutes on the RTC device  
Inputs: minutes - data to write to the RTC device  
returns: 1 if successful, 0 if unsuccessful  

#### RTC_GetHours()
Function to read the current hours off the RTC Device  
returns: the number of hours (24 hour format) or -1 if an error occurs  

#### RTC_SetHours(var hours)
Function to set the hours on the RTC device  
Inputs: hours - data to write to the RTC device (24 hour format)  
returns: 1 if successful, 0 if unsuccessful  

#### RTC_GetDay()
Function to read the current day of week (1-7) off the RTC Device  
returns: the day of week (1-7) or -1 if an error occurs  

#### RTC_SetDay(var day)
Function to set the day of week on the RTC device  
Inputs: day - data to write to the RTC device (1-7)  
returns: 1 if successful, 0 if unsuccessful  

#### RTC_GetDate()
Function to read the current day of month off the RTC Device  
returns: the day of month or -1 if an error occurs  

#### RTC_SetDate(var date)
Function to set the day of the month on the RTC device  
Inputs: date - data to write to the RTC device  
returns: 1 if successful, 0 if unsuccessful  

#### RTC_GetMonth()
Function to read the current month off the RTC Device  
returns: the month or -1 if an error occurs  

#### RTC_SetMonth(var month)
Function to set the month on the RTC device  
Inputs: month - data to write to the RTC device   
returns: 1 if successful, 0 if unsuccessful  

#### RTC_GetYear()
Function to read the current year off the RTC Device  
returns: the year (0-99) or -1 if an error occurs  

#### RTC_SetYear(var year)
Function to set the year on the RTC device  
Inputs: year - data to write to the RTC device   
returns: 1 if successful, 0 if unsuccessful  

#### RTC_GetTimeVar(var &hour, var &minute, var &second)
Function to read the current time off the RTC Device and to load it into variables  
inputs: &hour - address of the hour variable  
        &minute - address of the minute variable  
        &second - Address of the second variable  

#### RTC_GetDateVar(var &year, var &month, var &day)
Function to read the current date off the RTC Device and to load it into variables  
inputs: &year - address of the year variable  
        &month - address of the month variable  
        &day - Address of the day of the month variable  

#### RTC_SetTime(var hour, var minute, var second)
Function to write the current time to the RTC Device  
inputs: hour - hour variable to be writted  
        minute - minute variable to be writted  
        second - second variable to be writted  
returns: 1 if successful, 0 if unsuccessful   

#### RTC_SetAllDate(var year, var month, var day)
Function to write the current date to the RTC Device  
inputs: year - year variable to be writted  
        month - month variable to be writted  
        day- day of month variable to be writted  
returns: 1 if successful, 0 if unsuccessful   

#### RTC_to_sys()
Function to read time and date from RTC device and copy it to the Diablo16 internal system clock.  

#### sys_to_RTC()
Function to read time and date fromthe Diablo16 internal system clockand copy it to the  RTC device .  

#### RTC_RAM_writebytes(var offset, var nbytes, var &buf)
Function to write bytes into the ram addresses of the DS1307 chip.  
inputs: offset - offset location within memory valid range(0x00-0x38)  
        nbytes - number of bytes to write  
        &buf - address of array to write, bytes occupy lower byte of each word in the array  
returns: 1 if successful, 0 if unsuccessful  

#### RTC_RAM_writewords(var offset, var nwords, var &buf)
Function to write words into the ram addresses of the DS1307 chip.  
inputs: offset - offset location in bytes within memory valid range(0x00-0x38)  
        nwords - number of words to write  
        &buf - address of array to write  
returns: 1 if successful, 0 if unsuccessfull  

#### RTC_RAM_readbytes(var offset, var nbytes, var &buf)
Function to read bytes from the ram addresses of the DS1307 chip.  
inputs: offset - offset location within memory valid range(0x00-0x38)  
        nbytes - number of bytes to read  
        &buf - address of array to store read data, bytes occupy lower byte of each word in the array  
returns: 1 if successful, 0 if unsuccessful  

#### RTC_RAM_readwords(var offset, var nwords, var buf)
Function to read words from the ram addresses of the DS1307 chip.  
inputs: offset - offset location in bytes within memory valid range(0x00-0x38)  
        nwords - number of words to read  
        &buf - address of array to store read data  
returns: 1 if successful, 0 if unsuccessfull  

## AT24C32.lib
Library of functions for use with the AT24C32 data chip.  These chips are often found on DS1307 based module boards to provide additional storage.  When using this library a global variable AT24C32_i2c holds the I2C channel on which I2C communications will take place.  This removes the need to have this as an input variable to each of the functions.  the default value of AT24C32_i2c is 1.  

The AT24C32 is arranged in 256 pages each of 32 bytes.  In normal operation writes that would go over page boundaries would roll to the start of the page rather than the next page.  this driver guards against that by splitting writes if neccessary to ensure no roll over.  It does not currently check for overrun off the end of the available ram area so page rollovers could still occur in the final page.  


#### EEPROM_writebytes(var offset, var nbytes, var &buf)
Function to write bytes into the ram addresses of the AT24C32 chip.  
inputs: offset - offset location within memory valid range(0x000-0xFFF)  
        nbytes - number of bytes to write  
        &buf - address of array to write, bytes occupy lower byte of each word in the array  
returns: 1 if successful, 0 if unsuccessful  

#### EEPROM_writewords(var offset, var nwords, var &buf)
Function to write words into the ram addresses of the AT24C32 chip.  
inputs: offset - offset location in bytes within memory valid range(0x000-0xFFF)  
        nwords - number of words to write  
        &buf - address of array to write  
returns: 1 if successful, 0 if unsuccessful  

#### EEPROM_readbytes(var offset, var nbytes, var &buf)
Function to read bytes into the ram addresses of the AT24C32 chip.  
inputs: offset - offset location within memory valid range(0x000-0xFFF)  
        nbytes - number of bytes to read  
        &buf - address of array to read, bytes occupy lower byte of each word in the array  
returns: 1 if successful, 0 if unsuccessful  

#### EEPROM_readwords(var offset, var nwords, var &buf)
Function to read words into the ram addresses of the AT24C32 chip.  
inputs: offset - offset location in bytes within memory valid range(0x000-0xFFF)  
        nwords - number of words to read  
        &buf - address of array to read  
returns: 1 if successful, 0 if unsuccessful  
 

## ADS1115.lib
A library of functions to allow the use of a ADS111 based ADC expansion module with a Diablo16 based intelligent display device.  the library does not currently support the comparator functions or alert pin capabilities of the ADS1115 chip.  As the device has a selectable address, both the address and i2c channel are held in global variables ADS1115_Address and ADS1115_i2c.  The default values are 0x48 and 1 respectively.  

#### newconfig()
Function to generate a new configuration with default values, these default values are 250 samples per second, 4.096mv range and a single ended calculation on channel 0.  
returns: the config variable  

#### selectSingleChannel(var config, var channel)
Function to change the selected channel for the ADC  
inputs: config - the config as generated by newconfig to be edited  
        channel - the new channel to be used (0-3)  
returns: the new configuration or -1 if an error  

#### selectDiffChannel(var config, var ch1, var ch2)
Function to change the selected channels for differential use of the ADC  
inputs: config - the config (as generated by newconfig to be edited  
        ch1 - the new channel to be used (0-2)  
        ch2 - the second channel to be used (1 or 3)  
returns: the new configuration or -1 if an error  

#### selectSPS(var config, var SPS)
Function to change the sample rate for the ADC by specifying sample rate  
inputs: config - the config as generated by newconfig to be edited  
        SPS - the new SPS must be a valid selection (8, 16, 32, 64, 128, 250, 475, 860)  
returns: the new configuration or -1 if an error  

#### selectSPSINDEX(var config, var index)
Function to change the sample rate for the ADC by specifying index  
inputs: config - the config as generated by newconfig to be edited  
        index - the index(0-7) of the new SPS from the array (8, 16, 32, 64, 128, 250, 475, 860)  
returns: the new configuration or -1 if an error  

#### selectPGA(var config, var PGA)
Function to change the voltage range for the ADC by specifying new value in mv  
inputs: config - the config as generated by newconfig to be edited  
        PGA - the new PGA must be a valid selection (6144, 4096, 2048, 1024, 512, 256)  
returns: the new configuration or -1 if an error  

#### selectPGAINDEX(var config, var index)
Function to change the voltage range for the ADC by specifying index  
inputs: config - the config as generated by newconfig to be edited  
        index - the index (0-5) of the new PGA from the array (6144, 4096, 2048, 1024, 512, 256)  
returns: the new configuration or -1 if an error  

#### readADC(var conf)
Function to carryout a blocking single shot read of the ADC  
inputs: conf - a variable holding the configuration for sample rate, voltage range and channel selection.  
returns: the ADC value in the range -32768 to 32768  

#### startContinuousConversion(var conf)
Function to start a continuous asyncronous reading of the ADC and to return the first result  
inputs: conf - a variable holding the configuration for sample rate, voltage range and channel selection.  
returns: the ADC value in the range -32768 to 32768  

#### stopContinuousConversion()
Function to stop the continuous reading of the ADC  

#### getLastConversionResults()
Function to get the last read value of a continuous asyncronous reading of the ADC  
returns: the ADC value in the range -32768 to 32768  

#### calcvoltage(var result, var &voltage)
Function to convert an signed 16 bit integer ADC result into a float of the corresponding voltage in mllivolts.  This function assumes that the PGA and configuration has not been changed since the ADC result was obtained.  
Inputs: result - the ADC result to convert  
        &voltage - address of the 2 word array to hold the floaring point result  
    







