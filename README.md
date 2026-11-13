# EcoCar Onboarding Board – STM32F103

A 2-layer STM32F103 (LQFP48) development board designed in KiCad 10 as the onboarding project for the University of Alberta Eco Car Club. The design follows Phil's Lab's STM32 PCB tutorial and adds LEDs, buttons, a potentiometer, a buzzer and breakout headers.

## Features

- **MCU:** STM32F103 in LQFP48 (U1), with an external HSE crystal (Y1)
- **Power:** USB-C (J1) → AMS1117-3.3 LDO (U2) → 3.3 V, with a ferrite bead (FB1) filtering VDDA and a red power LED (D1)
- **USB:** Full-speed USB on PA11/PA12, with 5.1 kΩ CC pull-downs (R2, R3) so USB-C chargers supply 5 V
- **Programming:** SWD header (J2), BOOT0 switch (SW1)
- **User I/O:** 10 LEDs, 3 push buttons (SW2–SW4), 10 kΩ potentiometer (RV1) on the ADC, buzzer (BZ3), 4 PWM outputs
- **Headers:** UART (J4), I2C with 1.5 kΩ pull-ups (J3), SPI2 (J5), power out (J6: VBUS, 3.3 V, GND)
- **PCB:** 2 layers, GND pour on both layers

## Pin map (main signals)

| Function | Pin | Port |
|---|---|---|
| Potentiometer (ADC) | 10 | PA0 |
| BTN1 / BTN2 | 11 / 12 | PA1 / PA2 |
| BTN3 | 20 | PB2 |
| LED1 / LED2 | 14 / 15 | PA4 / PA5 |
| LED3 / LED6 | 29 / 30 | PA8 / PA9 |
| LED4 / LED5 | 38 / 41 | PA15 / PB5 |
| PWM1 / PWM2 | 16 / 17 | PA6 / PA7 |
| PWM3 / PWM4 | 18 / 19 | PB0 / PB1 |
| I2C (J3) | 21 / 22 | PB10 / PB11 |
| SPI2 CS / SCK / MISO / MOSI (J5) | 25 / 26 / 27 / 28 | PB12 / PB13 / PB14 / PB15 |
| UART (J4) | 42 / 43 | PB6 / PB7 |
| USB D− / D+ | 32 / 33 | PA11 / PA12 |
| SWDIO / SWCLK (J2) | 34 / 37 | PA13 / PA14 |
| Buzzer | 45 | PB8 |

See `Onboarding.kicad_sch` for the full schematic.

## Repository contents

| File | Description |
|---|---|
| `Onboarding.kicad_pro` / `.kicad_sch` / `.kicad_pcb` | KiCad project, schematic and board |
| `Onboarding-*.gbr`, `Onboarding-job.gbrjob` | Gerber files |
| `Onboarding-PTH.drl`, `Onboarding-NPTH.drl` | Drill files |
| `EcoOnboard_FW/` | Firmware |

## Design notes

- Minimum track width is 0.15 mm, and copper-to-board-edge clearance is 0.3 mm.
- BTN3 is on PB2 (BOOT1). That's safe as long as BOOT0 is low during normal boot.
- DRC shows no unconnected items. The remaining warnings are courtyard overlaps and silkscreen.

## Tools

KiCad 10.0
