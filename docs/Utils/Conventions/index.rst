Conventions
===============

Euler Angles
~~~~~~~~~~~~

“Euler angles are a mean of representing the spatial orientation of any
system of coordinates of the space as a composition of three rotations
from a reference system of coordinates.”

-  the first rotation is denoted by phi and is around the z axis
-  the second rotation is called theta and is around the new y-axis.
-  the third rotation is denoted by psi and is around the new z axis

The three rotations may be expressed as a single 3x3 matrix called Euler
matrix

.. raw:: html

   <pre>
   r11 = cos(psi)cos(theta)cos(phi) - sin(psi)sin(phi)
   r12 = cos(psi)cos(theta)sin(phi) + sin(psi)cos(phi)
   r13 = -cos(psi)*sin(theta)

   r21 = -sin(psi)cos(theta)cos(phi) - cos(psi)sin(phi)
   r22 = -sin(psi)cos(theta)sin(phi) + cos(psi)cos(phi)
   r23 = sin(psi)*sin(theta)

   r31 = sin(theta)cos(phi)
   r32 = sin(theta)sin(phi)
   r33 = cos(theta)

   where the first index refers to rows and the second to columns </pre>

Apositive rotation implies a clockwise rotation of the OBJECT or a
anti-clockwise rotation of the system of coordinates

Euler angles in Xmipp complies with the 3DEM standard (see
http://www.ebi.ac.uk/pdbe/docs/3dem/test_image/3DEM_compliance for
details)

Filenames
~~~~~~~~~~~~

In general, Xmipp can manage any Filename you can think of. However,
there are some ideas that could help you to organize your data, and
which might tell you more about the file only by its name. We could
divide files in several classes:

.. raw:: html

   <table>

.. raw:: html

   <tr>

.. raw:: html

   <th>

Data type

.. raw:: html

   </th>

.. raw:: html

   <th>

Suggested extension

.. raw:: html

   </th>

.. raw:: html

   <th>

Suggested filenames

.. raw:: html

   </th>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

Images

.. raw:: html

   </td>

.. raw:: html

   <td>

.xmp

.. raw:: html

   </td>

.. raw:: html

   <td>

g1ta000001.xmp

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

Volumes

.. raw:: html

   </td>

.. raw:: html

   <td>

.vol or .xmp

.. raw:: html

   </td>

.. raw:: html

   <td>

art000001.vol, wbp000001.vol, sirt000001.vol

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

Selection Files

.. raw:: html

   </td>

.. raw:: html

   <td>

.sel

.. raw:: html

   </td>

.. raw:: html

   <td>

g1t.sel

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   <tr>

.. raw:: html

   <td>

Document Files

.. raw:: html

   </td>

.. raw:: html

   <td>

.doc

.. raw:: html

   </td>

.. raw:: html

   <td>

angles.doc

.. raw:: html

   </td>

.. raw:: html

   </tr>

.. raw:: html

   </table>

The class [[FileName]] assumes a filename structure as in
g1ta000001.xmp, ie, a filename root (g1ta), a number (000001) and an
extension (xmp) (“.”); although it can also manage names as g1ta00001 or
g1ta00001.xmp.bak. To mantain compatibility with Spider it is required
that image numbers start at 1, and if possible that all images have got
correlative numbers, but these last conditions are not compulsory within
Xmipp, it’s just for compatibility with Spider.

Notice also that Spider requires all data files (volumes, images,
document files, …) to have the same extension. You might prefer this
other convention if you don’t want to make copies of the files, or to
have to rename the files before entering in Spider. 
Logical access
~~~~~~~~~~~~

The basic multidimensional classes implemented in this library admit two
kinds of access: physical and logical. The physical positions are those
indexes of the pixel inside the C matrix. Just an example, suppose we
have a 65x65 image, then the physical indexes range from 0 to 64, being
I[0][0] (if this could be written) the first pixel stored. However, we
might be interested in writing procedures in a more mathematical fashion
trying to access negative indexes (or even fractional onesSee
[[ImageOver]]) This conception is very useful when you want to represent
a discretized plane whose origin is at the center of the image, for
instance. So, you can express in a simpler way your algorithms without
having to make a by hand translation from the logical positions to the
physical ones.

Suppose now that we are interested to have the logical origin at the
center of the image 65x65, ie, at physical position [32][32]. This would
mean that the physical position [0][0] is now at logical position
(-32,-32), and the logical indexes range now from -32 to 32.

This logical index defintion is done by means of the starting indexes of
matrices (see matrix2D) where you can define which logical position is
occupying the first physical pixel, ie,

.. raw:: html

   <pre>
   I().startingY()`-32; 
   I().startingX()`-32; 
   </pre>

From now on you can start to access to logical positions even with
negative indexes. The usual way of establishing loops inside this
logical images is by using the starting and finishing information of its
axes

.. raw:: html

   <pre>  
       Image I(65,65);
       I().init_random();
       float sum=0;
       for (int i=STARTINGY(I()); i<=FINISHINGY(I()); i++)
           for (int j=STARTINGX(I()); j<=FINISHINGX(I()); j++) {
                  sum += I(i,j);
               // sum += IMGPIXEL(i,j);
           }
   </pre>

Although the previous example has been used using the class Image, the
logical access rely on the classes matrix1D, matrix2D, and matrix3D, and
all the concepts explained for images are extensible for vectors and
volumes. The related functions are STARTINGX, STARTINGY, STARTINGZ,
FINISHINGX, FINISHINGY, FINISHINGZ, IMGPIXEL, DIRECT_IMGPIXEL, VOLVOXEL,
DIRECT_VOLVOXEL, VEC_ELEM, MAT_ELEM, VOL_ELEM, DIRECT_VEC_ELEM,
DIRECT_MAT_ELEM, DIRECT_VOL_ELEM

Pay attention to the index order when pointing to a pixel, first you
have to give the most outer coordinate (which is the less varying one in
the actual implementation), and then increase the coordinate. For
volumes the usual way of making a loop is

.. raw:: html

   <pre>
       Volume V(65,65,65);
       V().init_random();
       float sum=0;
       for (int k=STARTINGZ(V()); k<=FINISHINGZ(V()); k++)
          for (int i=STARTINGY(I()); i<=FINISHINGY(I()); i++)
              for (int j=STARTINGX(I()); j<=FINISHINGX(I()); j++) {
                  sum +=V(k,i,j);
           }
   </pre>

Notice that if you don’t modify the origin of the multidimensional array
then the physical and logical accesses are the same. 

Image center
~~~~~~~~~~~~

There is a special case for the logical access when the origin is set
just at the center of the image, volume or vector. There are several
definitions of center of the image, the one used here is the physical
position ((int)ydim/2, (int)xdim/2). This is the same convention used in
Spider and has been chosen to mantain compatibility with that package.
Remember that in C (int) takes the integer part of the number, for
example, for 2.3 and 2.8 the integer part is 2, while for -2.3 and -2.8
the integer part is -2.

This means that for images with an even dimension, the center will be
“displaced” in that direction. Let’s have a look on the following two
diagrams of cell indexes.
