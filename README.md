## Control Charging on Apple Silicon Macs

### Compile smc-command

```sh
cd smc-command
make
```

### Disable or enable charging

```sh
# Disable charging
./smc -k CH0B -w 02

# Enable charging
./smc -k CH0B -w 00
```

The SMC keys used are `CH0B` and `CH0C`.
Changing any of these will change the other as well.

Values:

`00`: Charging enabled
`01`: Charging disabled

See the following link for more details.

https://github.com/davidwernhart/AlDente/issues/52#issuecomment-777627075
