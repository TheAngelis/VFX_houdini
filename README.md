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

## Creating a geometry using VEX
```c
//First we need to create the points and use then to positioning this points like placeholders,
//waiting to receive the vertex conections. To create the vertex and stores on each points (ptnum) we need a primitive.

int pnt0 = addpoint(0, {0,0,0});
int pnt1 = addpoint(0, {1,0,0});
int pnt2 = addpoint(0, {1,1,0});
int pnt3 = addpoint(0, {0,1,0});

int prim0 = addprim(0, "poly");

int vertex0 = addvertex(0, prim0, pnt0);
int vertex1 = addvertex(0, prim0, pnt1);
int vertex2 = addvertex(0, prim0, pnt2);
int vertex3 = addvertex(0, prim0, pnt3);
```

## Floor to use on Seed
```c
floor($F/10)=10; // 10 frames 
floor($F/fit(rand($F),5,100,5,25)) // rand values
```

## Point Normal away
```c
vector a = set(0,0,0);
@N = normalize(a+@P);
```

## Animate along curve
```c
vector pos = primuv(1, "P", 0, ch('U'));
@P=pos;
vector nrm= primuv(1, "N", 0, ch('U'));
@N=-nrm;
```
