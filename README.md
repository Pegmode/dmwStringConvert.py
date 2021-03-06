# dmwStringConvertTools
Python script to convert wavetable sample strings into .dmw files for use in Deflemask

## Usage
##### Convert sample string to .dmw
Run dmwStringConvert.py and ensure that there is a text file containing wavetable sample stings separated by newlines (enter key). Ensure that the variables under `#USER VARIABLES` are set correctly. **PLEASE ENSURE YOU SET THE HEX FLAG TO FALSE IF YOUR DATA IS IN DECIMAL**
##### Format LSDJ wavetables 
Dump wavetable samples from Little Sound DJ (LSDJ) .sav into INTPATH then run LSDJSavDataForm.py 


## TODO
- add program args instead of source code user variables
- change base selection from bool to int and simplify code

## .dmw Reverse Engineered format

Dispite the .dmf format specifications having been released by Delek, the .dmw specifications have not. These are the reverse engineered specifications. 

Please note that there are 2 different types of .dmw formats found refered here as "old style" and "new style". If byte 4 is 0xFF, Deflemask seems to not treat the value as the bit depth. Under this situation byte 5 seems to determine the size of each sample entry but it is not fully understood yet. The rest of the format continues like normal but with a modified sample data entry size.

```
"Old style" (Included in examples)
4 Bytes: Number of samples in Wavetable
1 Byte: Bit depth
for number of samples in wavetable
  1 Byte: wavetable data


"New Style" (Generated by modern Deflemask)
4 Bytes: Number of samples in Wavetable
2 Bytes: 0xFF,0x00
1 Byte: Bit depth
for number of samples in wavetable
  4 Bytes: wavetable data
```
