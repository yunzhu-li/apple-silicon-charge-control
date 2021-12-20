## Control Charging on Apple Silicon MacBooks

### Compile smc-command

```sh
cd smc-command
make
```

### Disable or enable charging

```sh
# Disable charging
sudo ./smc -k CH0B -w 02

# Enable charging
sudo ./smc -k CH0B -w 00
```

The SMC keys used are `CH0B` and `CH0C`.
Changing any of these will change the other as well.

Values:

`00`: Charging enabled
`01`: Charging disabled

See the following link for more details.

https://github.com/davidwernhart/AlDente/issues/52#issuecomment-777627075

### Discharge battery when connected to external power

Changing the value of key `CH0J` can cause the system to draw power from the
battery even when external power is connected. Please note that if external
display is used with the lid closed ("clamshell mode"), display will turn off
and you will need to wake up the computer again.

```sh
# Disconnect external power
sudo ./smc -k CH0J -w 20

# Reconnect external power
sudo ./smc -k CH0J -w 00
```
