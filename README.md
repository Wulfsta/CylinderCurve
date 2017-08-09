# Cylinder Curve

This is a tiny SageMath script I wrote sometime in my freshman year of undergrad that 
draws some waves. It turns out that these waves are just the Jacobi elliptic sine or elliptic 
cosine, depending on whether the x-axis or y-axis is the semimajor axis of the ellipse on the 
xy-plane. 

This script was prompted by my desire to make a headphone pad (in the style of Audeze LCD-2s) 
that had an elliptic cutout for the ear.

## Raw:

Here is the raw text, for those not working in a Jupyter notebook:

```sage
# Summary: A simple approximation of the curve resulting from cutting an elliptic cylinder at some
# angle (cut), and rolling it across a plane so that the cut traces a curve.
#
# Author: Luke V

a = 1          # x radius length
b = 1          # y radius length
cut = pi / 4   # angle of plane

theta = var('theta')
phi = var('phi')
diffx = diff(a * cos(theta), theta)
diffy = diff(b * sin(theta), theta)
func = (diffx^2 + diffy^2)^(1 / 2)

def getnumerical(i):
    return numerical_integral(func, 0, i)[0]

parametric_plot((getnumerical, b * tan(cut) * sin(phi)), (phi, 3 * pi / 2, 7 * pi / 2), aspect_ratio=1)
```
