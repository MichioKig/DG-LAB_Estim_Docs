# DG-LAB Estim - Docs

Based on [Official documentation](https://github.com/DG-LAB-OPENSOURCE/DG-LAB-OPENSOURCE) for BLE.

## Community

More info can be found at https://github.com/buttplugio/stpihkal/issues/91

Examples:
- https://github.com/rezreal/coyote
- https://rezreal.github.io/coyote/web-bluetooth-example

## BLE services

### Generic Access
```00001800-0000-1000-8000-00805f9b34fb```

|                    Name                    |  ID  |                  UID                   | Size | R | W | N |
|------------------------------------------- |-----:|:---------------------------------------|-----:|:-:|:-:|:-:|
| Device Name                                |      | `00002a00-0000-1000-8000-00805f9b34fb` |      | x | x |   |
| Appearance                                 |      | `00002a01-0000-1000-8000-00805f9b34fb` |      | x |   |   |
| Peripheral Preferred Connection Parameters |      | `00002a04-0000-1000-8000-00805f9b34fb` |      | x |   |   |
| Central Address Resolution                 |      | `00002aa6-0000-1000-8000-00805f9b34fb` |      | x |   |   |

- https://gist.github.com/sam016/4abe921b5a9ee27f67b3686910293026
- https://btprodspecificationrefs.blob.core.windows.net/assigned-values/16-bit%20UUID%20Numbers%20Document.pdf

### Generic Attribute
```00001801-0000-1000-8000-00805f9b34fb```

### DG-Lab EStim Info `180a`
```955a180a-0fe2-f5aa-a094-84b8d4f3e8ad```

|                    Name                    |  ID  |                  UID                   | Size | R | W | N |
|------------------------------------------- |-----:|:---------------------------------------|-----:|:-:|:-:|:-:|
| Battery Level (0-100)                      | 1500 | `955a1500-0fe2-f5aa-a094-84b8d4f3e8ad` |    1 | x |   | x |
| Firmware version?                          | 1501 | `955a1501-0fe2-f5aa-a094-84b8d4f3e8ad` |    2 | x |   |   |
| BT MAC                                     | 1502 | `955a1502-0fe2-f5aa-a094-84b8d4f3e8ad` |    6 | x |   |   |

- Battery level >84 is considered full

### DG-Lab EStim Config `180b`
```955a180b-0fe2-f5aa-a094-84b8d4f3e8ad```

|                    Name                    |  ID  |                  UID                   | Size | R | W | N |
|:------------------------------------------ |-----:|:---------------------------------------|-----:|:-:|:-:|:-:|
|                                            | 1503 | `955a1503-0fe2-f5aa-a094-84b8d4f3e8ad` |    3 | x | x |   |
| PWM_AB2 / A+B Intensity                    | 1504 | `955a1504-0fe2-f5aa-a094-84b8d4f3e8ad` |    3 | x | x | x |
| PWM_A34 / A waveform data                  | 1505 | `955a1505-0fe2-f5aa-a094-84b8d4f3e8ad` |    3 | x | x |   |
| PWM_B34 / B waveform data                  | 1506 | `955a1506-0fe2-f5aa-a094-84b8d4f3e8ad` |    3 | x | x |   |
| Power characteristic                       | 1507 | `955a1507-0fe2-f5aa-a094-84b8d4f3e8ad` |    3 | x | x |   |
|                                            | 1508 | `955a1508-0fe2-f5aa-a094-84b8d4f3e8ad` |    4 | x |   | x |
|                                            | 1509 | `955a1509-0fe2-f5aa-a094-84b8d4f3e8ad` |    4 | x | x |   |

```
Frequency = X + Y
X = ((Frequency / 1000)^ 0.5) * 15
Y = Frequency-X
```

### PWM_AB2 (`1504`)
| Size |    Name    |
|-----:|:-----------|
|   11 | A Strength |
|   11 | B Strength |
|    2 | Reserved   |

### PWM_A34 (`1505`)
| Size |    Name    |
|-----:|:-----------|
|    5 | Ax         |
|   10 | Ay         |
|    5 | Az         |
|    4 | Reserved   |

### PWM_B34 (`1506`)
| Size |    Name    |
|-----:|:-----------|
|    5 | Bx         |
|   10 | By         |
|    5 | Bz         |
|    4 | Reserved   |

### Power Characteristic (`1507`)
| Size |    Name    |
|-----:|:-----------|
|    8 | Power step |
|   11 | Max power  |
|    5 | Reserved   |

### Unknown `180c`
```955a180c-0fe2-f5aa-a094-84b8d4f3e8ad```

|                    Name                    |  ID  |                  UID                   | Size | R | W | N |
|:------------------------------------------ |-----:|:---------------------------------------|-----:|:-:|:-:|:-:|
|                                            | 150a | `955a150a-0fe2-f5aa-a094-84b8d4f3e8ad` |    2 | x | x |   |
|                                            | 150b | `955a150b-0fe2-f5aa-a094-84b8d4f3e8ad` |    8 | x |   | x |
|                                            | 150c | `955a150c-0fe2-f5aa-a094-84b8d4f3e8ad` |    7 | x | x |   |

Never used by the app.

### Firmware Upgrade
```8e400001-f315-4f60-9fb8-838830daea50```

|                    Name                    |  ID  |                  UID                   | Size | R | W | N |
|:------------------------------------------ |-----:|:---------------------------------------|-----:|:-:|:-:|:-:|
|                                            |      | `8e400001-f315-4f60-9fb8-838830daea50` |      |   | x | x |

Probably BFU (Buttonless Firmware Upgrade)
 - https://github.com/NordicSemiconductor/IOS-Pods-DFU-Library/issues/317
 - https://devzone.nordicsemi.com/f/nordic-q-a/17580/implementing-buttonless-dfu-w-sdk12
 - `nRF52832`
