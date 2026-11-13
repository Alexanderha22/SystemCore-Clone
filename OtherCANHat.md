Other can hats can be used by modifying the config_no_fd.txt and ./systemcore-can-nofd-setup/diy-can-setup.sh This is how the NO FD PLUS config was created.

Check the manufactures website to get the configuration settings for the can header and replace the last section with the new information. Keep note of the spi address. The new example config here uses 1.1 and 1.2

Before

```         
dtparam=spi=on
dtoverlay=mcp2515-can0,oscillator=16000000,interrupt=24,spimaxfrequency=10000000
dtoverlay=mcp2515-can1,oscillator-16000000,interrupt=25,spimaxfrequency=10000000
```

After

```         
dtparam=spi=on
dtoverlay=i2c0
dtoverlay=spi1-3cs
dtoverlay=mcp2515,spi1-1,oscillator=16000000,interrupt=22
dtoverlay=mcp2515,spi1-2,oscillator=16000000,interrupt=13
```

Replace the spi addresses in diy-can-setup.sh to match the config

Before

```         
setup_bus spi0.0  can_s0 
setup_bus spi0.1  can_s1
setup_bus ""      can_s2   
setup_bus ""      can_s3
setup_bus ""      can_s4
```

After

```         
setup_bus spi1.1  can_s0
setup_bus spi1.2  can_s1
setup_bus ""      can_s2
setup_bus ""      can_s3
setup_bus ""      can_s4
```
