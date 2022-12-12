# VFX_houdini

## Fit a random number between a Min and Max
```c
// Fit random number min and max 
  fit(rand($PT), 0, 1, 1.86, 2.85);
  @pscale = fit(rand(@id), 0, 1, chf("min"), chf("max"));

```

## Set Pscale with ramp controler
```c
@pscale = chramp("size", @P) * ch("mult");
```
