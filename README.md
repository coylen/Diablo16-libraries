# Diablo16-libraries

A selection of Libraries to aid in the use of chips and modules which use I2C communications and Diablo16 based intelligent display boards from 4D systems.

# i2c.lib

A library of helper functions to bridge between the basic internal I2C functions in the Diablo16 chip and the higher level communications neccessary to interoperate with I2C based modules.  All commands come in two forms one with the i2c channel 1,2 or 3 as a variable and a second individual command for each of the three channels, the value x in the prototype function being replaces with the i2c channel number.

## I2C_is_ready(var i2c, var addr), I2Cx_is_ready(var addr)
Function which tests an individual address to check for response, to indicate the device is attached and ready.
inputs: addr - address of the I2C device to be tested
return: 1 if responsive, 0 if not responsive

## I2C_scan(var i2c, var &devices), I2Cx_scan(var &devices)
Function to scan the bus and return a list of all devices active on the bus.
inputs: &devices - address of array to hold the detected devices
output: devices - an array of the detected devices
return: number of detected dvices

## I2C_readbytes(var i2c, var addr, var nbytes, var &buf), I2Cx_readbytes(var addr, var nbytes, var &buf)
Function to read a defined number of bytes from an I2C device.
inputs: addr - address of the device
        nbytes - number of bytes to read
        &buf - address of array to return the read bytes
output: buf - an array of the returned bytes with each byte occupying the lower byte of each word of the array
return: 1 if successful, 0 if unsuccessful

## I2C_writebytes(var i2c, var addr, var nbytes, var &buf), I2Cx_writebytes(var addr, var nbytes, var &buf)
Function to write a defined number of bytes to an I2C device.
inputs: addr - address of the device
        nbytes - number of bytes to write
        &buf - address of array to write, bytes occupy lower byte of each word in the array.
return: 1 if successful, 0 if unsuccessful

## I2C_readbytes_mem(var i2c, var addr, var memaddr, var nbytes, var &buf), 
## I2Cx_readbytes_mem(var addr, var memaddr, var nbytes, var &buf)
Function to read a defined number of bytes from a specified memory address on an I2C device.
inputs: addr - address of the device
        memaddr - register within the i2c device (8bits)
        nbytes - number of bytes to read
        &buf - address of array to return the read bytes
output: buf - an array of the returned bytes with each byte occupying the lower byte of each word of the array
return: 1 if successful, 0 if unsuccessful

## I2C_writebytes_mem(var i2c, var addr, var memaddr, var nbytes, var buf),
## I2Cx_writebytes_mem(var addr, var memaddr, var nbytes, var buf)
Function to write a defined number of bytes to specified register on an I2C device.
inputs: addr - address of the device
        memaddr - register within the i2c device (8bits)
        nbytes - number of bytes to write
        &buf - address of array to write, bytes occupy lower byte of each word in the array.
return: 1 if successful, 0 if unsuccessful

## I2C_readwords(var i2c, var addr, var nwords, var &buf), I2Cx_readwords(var addr, var nwords, var &buf)
Function to read a defined number of words from an I2C device.
inputs: addr - address of the device
        nbytes - number of words to read
        &buf - address of array to return the read words
output: buf - an array of the returned words
return: 1 if successful, 0 if unsuccessful

## I2C_writewords(var i2c, var addr, var nwords, var &buf), I2Cx_writewords(var addr, var nwords, var &buf)
Function to write a defined number of words from an I2C device.
inputs: addr - address of the device
        nbytes - number of words to write
        &buf - address of array of words to write
return: 1 if successful, 0 if unsuccessful

## I2C_readwords_mem(var i2c, var addr, var memaddr, var nwords, var &buf),
## I2Cx_readwords_mem(var addr, var memaddr, var nwords, var &buf)
Function to read a defined number of words from a specified memory address on an I2C device.
inputs: addr - address of the device
        memaddr - register within the i2c device (8bits)
        nbytes - number of words to read
        &buf - address of array to return the read words
output: buf - an array of the returned words
return: 1 if successful, 0 if unsuccessful

## I2C_writewords_mem(var i2c, var addr, var memaddr, var nwords, var &buf),
## I2Cx_writewords_mem(var addr, var memaddr, var nwords, var &buf)
Function to wriet a defined number of words from a specified memory address on an I2C device.
inputs: addr - address of the device
        memaddr - register within the i2c device (8bits)
        nbytes - number of words to write
        &buf - address of array of words to write
return: 1 if successful, 0 if unsuccessful

## I2C_readbytes_mem16(var addr, var memaddr, var nbytes, var &buf)
## I2C_writebytes_mem16(var addr, var memaddr, var nbytes, var &buf)
## I2C_readwords_mem16(var addr, var memaddr, var nbytes, var &buf)
## I2C_writewords_mem16(var addr, var memaddr, var nbytes, var &buf)
As per previous function descriptions but with a 16bit register address


# DS1307.lib
Library of functions for use with the DS1307 Real time clock chip.  When using this library a global variable DS1307_Address holds the I2C channel on which I2C communications will take place.  This removes the need to have this as an input variable to each of the functions.  the default value of DS1307_Address is 1.

## bcd_to_int(var bcd)
## int_to_bcd(var intvalue)
Internal helper functions to translate binary coded decimal to integer and vice versa

## RTC_GetSeconds()





