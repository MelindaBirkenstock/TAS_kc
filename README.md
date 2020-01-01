### Two-Axis Sculpt Keycaps

#### Renders:
![TAS_profile_3x6_render](https://i.imgur.com/PeOQRxq.jpg)
![TAS_profile_ergo_render](https://i.imgur.com/4sUnMbP.jpg)

#### Production:
* The recommended method for 3D printing these keycaps is stereolithography (SLA), selective laser sintering is also a valid method but results in more grainy texture and less consistent dimensions. Filament deposition printing (FDM) can also be used but keycap stem fitment may be compromised, more discussion on this in the design notes section

* The keycaps can be printed individually, or as a 'layout' (a grid of keycaps)

    * Individual keycap models in STL format for 3D printing are in `./keycaps/stl`. Layouts in STL format are in `./layouts/stl`

    * I had the prototypes made by [3D Hubs](https://www.3dhubs.com/) by uploading the `./layouts/sldprt/TAS_profile_layout_4x6.sldprt` and having two copies of this layout made to fill a 4x6 split keyboard

    * A layout of keycaps can be made in Solidworks using the `mx_stem_grid_6x6.sldprt` file and mating individual keycaps to the MX stems in an assembly file, some examples of this are in `./layouts/sldasm`
        * **Note**: the MX stem grid should be supressed before either converting the assembly to a STL/OBJ/SLDPRT, otherwise the stem grid will be printed along with the keycaps
        * This is also useful when visualizing the layout before production

----

#### Design notes:

* The keycaps are directly modelled in Solidworks, parametric modelling would be a more precise approach

* The base set of TAS-profile keycaps consists of 3 rows and 4 columns
    * The C0 column has only 1 axis of sculpt (x axis), like a typical set of sculpted SA-profile keycaps
    * Columns C1-C3 are sculpted in two axes (x and y axes), scooping up towards the outer/C3 column, and down towards the home/R1 row


![3x4_base_set](https://i.imgur.com/Z8LcRNy.jpg)

* 3x5, 3x6, 4x5, 4x6... etc. layouts can be made by mirroring the caps with the "C0" column as the mirror axis

![3x6_set](https://i.imgur.com/JYcfV5o.jpg)

* The bottom row (R3) leaves room for customization, depending on the keyboard they will be used on
* The bottom row I decided to use consists of keycaps from the home/R1 row, as is typical with SA-profile keycaps along with a 1.25 unit thumb key as seen on keyboards like the [Corne](https://github.com/foostan/crkbd)

![4x6_set](https://i.imgur.com/R5IEBWT.jpg)

* The stem slot is sized as pictured below:
    * Initially, I sized the stem slot width to 1.20mm
    * The prototypes I had SLS 3D printed from nylon had a moderately snug fit for most of the keycaps, however, due to manufacturing inconsistenscies, some keycaps were loose on the stem
    * I have reduced the stem slot width from 1.20mm to 1.17mm to ensure a good fit when printed with SLS or SLA with resin printing
        * **Note**: This sizing may be too tight for FDM 3D printing, I have read that some users size the stem slot width ranging from 1.25mm to 1.35mm
        * However, I have also read that it is possible to soak the inside of the stem slot with acetone and 'mold' the keycap's slot to a Cherry MX stem

![mx_stem_dimensions](https://i.imgur.com/NWxlgH6.jpg)

* Each keycap uses the same Solidworks part for the Cherry-MX compatible stem: `mx_stem.sldprt`
    * One of the boss extrude lengths is set to the height of the MX switch stem
    * The other boss extrude length needs to be altered to meet the top surface of the keycap, as the keycaps have differing heights (plane center height)

* The geometry of the keycap is defined using the following parameters:
    1) Base square side length
    2) Top plane center height
    3) Top square side length
    4) Vertex length (2+ vertices need to be defined)
    5) Sculpt depth
    6) Vertex tapered fillet radii

![parameters_legend](https://i.imgur.com/j88IV1n.jpg)

![tapered_fillet_radii_legend](https://i.imgur.com/MzEyFwI.jpg)

* Some parameters are held constant for the keycaps, these are the parameter values I used for my set:
    * Base square side length = 18.50mm
    * Top square side length = 12.50mm
        * **Note**: This is true for 1 unit (square) keycaps, 1.25+ unit sized keycaps have a rectangular top/bottom "square" and these parameters need to be multiplied by a factor depending on the size
            * e.g.: 1.25 unit keycaps have dimensions  18.50mm x 1.25(18.50mm) for the base rectangle side length and 12.50mm x 1.25(12.50mm) for the top rectangle side length
    * Sculpt depth = 0.80mm
    * Vertex tapered fillet radius 1 = 2.00mm
    * Vertex tapered fillet radius 2 = 0.50mm

----

### To-do:
* Add another row for number keys (50% - 60% layouts)

----
###### Models were created in Solidworks, then exported as STL. Feel free to use/modify/redistribute.
