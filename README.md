# Ideamaker Profiles for Stock Marlin and Original Prusa Firmware 


### Firmware
* [SKR Bear Firmware](https://github.com/codiac2600/SKR-Bear-Marlin)
* [Prusa Firmware](https://github.com/prusa3d/Prusa-Firmware)

## How To
* [Profile Import Video](https://youtu.be/xpCn3DiZKgA)

Stock Marlin Setup:
* Step 1: Load Printer Profile (ie. SKR Bear Printer)
* Step 2: Set your esteps in Printer Type > Advanced - Step-E per MM
	* Stock - 280 | BMG - 830 | Pulleybox/LDO Geared - 980 | Hemera - 800
* Step 3: Confirm that Printer type > Advanced - Omit RaiseTouch Specific Gcode is enabled
* Step 4: Confirm that Printer type > Advanced - Relative Extrusion is enabled
* Step 5: Load Profiles (ie. SKR CFPETG)

Stock Prusa Setup:
* Step 1: Load Printer Profile (ie. SKR Bear Printer)
* Step 2: Set your esteps in Printer Type > Advanced - Step-E per MM
	* Stock - 280 | BMG - 830 | Pulleybox/LDO Geared - 980
* Step 3: Confirm that Printer type > Advanced - Change GCode E Length by multiplying filament flowrate is enabled
* Step 4: Confirm that Printer type > Advanced - Omit RaiseTouch Specific Gcode is enabled
* Step 5: Confirm that Printer type > Advanced - Relative Extrusion is enabled
* Step 6: Load Profiles (ie. SKR CFPETG)


## Start Gcode 

### Stock Marlin ABL

```gcode
G90 ; Absolute Positioning
M83 ; extruder relative mode
M140 S{temperature_heatbed} ; set bed temp
M104 S150 ; set extruder temp
M190 S{temperature_heatbed} ; wait for bed temp
G28 ; Home all axes
G29 ; Level Bed
G1 X0 Z0.6 Y-3.0 F3000.0 ;
M104 S{temperature_extruder1} ; set extruder
M109 S{temperature_extruder1} ; wait for extruder temp
M900 K0.05; Linear advance setting
G92 E0.0
G1 Z0.2 X100.0 E30.0 F1000.0 ; intro line
G92 E0.0
```

### Stock Marlin UBL

```gcode
G90 ; Absolute
M83 ; extruder relative mode
G28 ; Home all axes
G29 L1 ; Load UBL Slot 1
M140 S{temperature_heatbed} ; set bed temp
M190 S{temperature_heatbed} ; wait for bed temp
G29 J2; 4 point mesh tilt
G1 X0 Z0.6 Y-3.0 F3000.0
M104 S{temperature_extruder1} ; set extruder temp
M109 S{temperature_extruder1} ; wait for extruder temp
M900 K0.05; Linear advance setting
G92 E0.0
G1 Z0.2 X100.0 E30.0 F1000.0 ; intro line
G92 E0.0
```

### Stock Prusa Firmware

```gcode
G90 ; Absolute Positioning
M83 ; extruder relative mode
M140 S{temperature_heatbed} ; set bed temp
M104 S150 ; set extruder temp
M190 S{temperature_heatbed} ; wait for bed temp
G28 W ; home all without mesh bed level
G80 ; mesh bed leveling set 3x3, 5x5, or 7x7 in settings menu
G1 Y-3.0 Z0.6 F1000.0 ; go outside print area for purge
M104 S{temperature_extruder1} ; set extruder
M109 S{temperature_extruder1} ; wait for extruder temp
M900 K30; Linear advance setting LA1.5 value K0.05
G92 E0.0
G1 Z0.2 X100.0 E30.0 F1000.0 ; intro line
G92 E0.0
M221 S95 ; Filament Flowrate
```
## Layer Change Gcode

```gcode
G92 E0.0
```



