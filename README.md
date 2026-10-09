# Fire & Gas Detection System (Raspberry Pi Pico)

A MicroPython project for the Raspberry Pi Pico that continuously monitors gas levels and fire presence, triggering an LED and buzzer alarm when a hazard is detected.

## How It Works

The Pico reads two sensors in a loop:

- **Gas sensor** (analog, ADC0 / GP26) — measures gas concentration as a 16-bit value (0–65535)
- **Fire sensor** (digital, GP16) — outputs a signal when fire/flame is detected

If the gas reading exceeds a set threshold, or the fire sensor triggers, the system turns on an LED and buzzer as an alarm. Otherwise, both stay off. Readings are printed every loop for monitoring/debugging.

## Hardware

| Component    | Pico Pin       |
|--------------|----------------|
| LED          | GP15 (output)  |
| Buzzer       | GP14 (output)  |
| Fire sensor  | GP16 (input)   |
| Gas sensor   | GP26 / ADC0    |

## Requirements

- Raspberry Pi Pico (or Pico W)
- MicroPython firmware installed
- Gas sensor (e.g. MQ-2) wired to an analog pin
- Flame/fire sensor module wired to a digital pin
- LED + buzzer for alarm output

## Usage

1. Flash MicroPython onto your Pico if it isn't already.
2. Copy `Robotics_RP_Pico.py` onto the Pico (e.g. as `main.py` so it runs on boot).
3. Wire up the components as described above.
4. Power the board — it will continuously print sensor readings and sound the alarm when a hazard is detected.

## Configuration

- `gas_threshold` — the ADC value above which gas is considered dangerous (default: `20000`). This should be calibrated based on your specific sensor and environment.
- `time.sleep(0.2)` — polling interval between readings (200 ms).

## Example Output

```
Gas level: 4521 | Fire sensor: 0
Gas level: 4488 | Fire sensor: 0
Gas level: 21300 | Fire sensor: 0
```

## Notes

This is a basic prototype for learning/hobby purposes and has not been tested for real-world safety-critical use. Always calibrate sensors and test thoroughly before relying on this for actual hazard detection.

## License

MIT
