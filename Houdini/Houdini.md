# Houdini

## Matt Estela Intro

- Point VOPs are similar to shader node systems
- VEX is the technical underpinning of VOP systems
- If it can be keyframed, it can be houdini'd
- layering and merging effects can be powerful (hologram man example)

## Joy of VEX

### Day 1
- @Cd = @P, Color at this point equals the position vector at this point
- @Cd = @N, Color at this point equals the normal vector at this point
- float foo = @P.x * 6; @Cd = sin(foo);, assign local variables with a type identifier, access components with . syntax
- foo = float(@ptnum) / @numpt; add an attribute that's stored with the geo that casts it's identifier int to a float and divides it by the total number of points

### Day 2

- length(@P)
- distance(@P, {1, 0, 3})

```
vector pos = @P * chv('fancyscale');
vector center = chv('center');
float d = distance(pos, center);
d *= ch('scale');
@Cd = (sin(d) + 1) * 0.5;
```
- channel names must be unique
- fit is used for reframing to a range fit(value, incomingMin, incomingMax, desiredMin, desiredMax)

#### Exercises
- sin waves going towards the center -> add, away -> subtract
- speed of sin waves changes by scaling time
- blue on black ? multiply everything by blue
- yellow on green ? 
```
float sinFactor = fit(sin(d - @Time * 10), -1, 1, 0, 1);
@Cd = (1 - sinFactor) * {1, 1, 0} + sinFactor * {0, 1, 0};
```
- Y position instead of color? @P.y = ...

### Day 3

- more clamp and fit examples
- making sin fit on 3d objects -> add normal to points
- adding sin before / after / in between fit / clamp changes where the waves start and end

