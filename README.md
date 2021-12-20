## Control Charging on Apple Silicon MacBooks

### Compile smc-command

```sh
cd smc-command
make
```

### Disable or enable charging

```sh
# Disable charging
sudo ./smc -k CH0C -w 01

# Enable charging
sudo ./smc -k CH0C -w 00
```

The SMC keys used is `CH0C`. Values:

- `00`: Charging enabled
- `01`: Charging disabled

See the following link for more details.

https://github.com/davidwernhart/AlDente/issues/52#issuecomment-777627075

### Discharge battery when connected to external power

Changing the value of key `CH0I` can cause the system to draw power from the
battery even when external power is connected. Please note that if external
display is used with the lid closed ("clamshell mode"), display will turn off
and you will need to wake up the computer again.

```sh
# Disconnect external power
sudo ./smc -k CH0I -w 01

# Reconnect external power
sudo ./smc -k CH0I -w 00
```
