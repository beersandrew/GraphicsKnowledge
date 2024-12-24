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
