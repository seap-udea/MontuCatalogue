# Stellar Catalogue for Montu Python /mnṯw ꜥꜣpp(y)/
## Astronomical ephemerides for the ancient world

This is the tools to create the stellar catalogue for [`MontuPython`](https://github.com/seap-udea/MontuPython).

The catalogue of `MontuPython` is an improved and slightly extended version of the incredible work of David Nash, who during almost a decade has created and released his version of the [HYG databas](http://www.astronexus.com/hyg).

The `MontuCatalogue` is based on HYG but several improvements and adaptations has been done for making the catalogue useful for the purposes of the package.

These are the columns included in `MontuCatalogue`:

- *`MN`*: `MontuCatalogue` index.

- *`HD`*: Number in the HD catalogue. Null value is 0.

- *`HR`*: Number in the HR catalogue. Null value is 0.

- *`HIP`*: Number in the HR catalogue. Null value is 0.

- *`Gl`*: Gliese catalogue designation. Null value is 'NaN'.

- *`Name`*: Name of the star. According to availability the name is asignated in this order: Proper name, Bayer name, Flamsteed name, HD designation, HR  designation, HIP designation, HYG designation

- *`OtherDesignations`*: All available designations for the star.

- *`ProperName`*: Proper name in the IAU database. Null value is 'NaN'.

- *`Bayer`*: Bayer designation as a greek letter [number] and constellation abbreviature. Null value is 'NaN'.

- *`Flamsteed`*: Bayer designation as a number and constellation abbreviature. Null value is 'NaN'.

- *`Constellation`*: Constellation abreviature. 

- *`RAJ2000`*: Right ascension at J2000.0 epoch in **degrees**. Not null value.

- *`DecJ2000`*: Right ascension at J2000.0 epoch in **degrees**. Not null value.

- *`pmRA`*: Proper motion in right ascension in **mas/year**. Null value is 0.

- *`pmDec`*: Proper motion in declination in **mas/year**. Null value is 0.

- *`RadVel`*: Radial velocity in **km/s**. Null value is 0.

- *`Distance`*: Distance in **parsecs**. Null value is 0. 

- *`Vmag`*: Visual magnitude (either in band V or G). Not null values.

- *`Vmag_min`*: Minimum brightness in visual magnitude for variable star. Null value is NaN.

- *`Vmag_max`*: Maximum brightness in visual magnitude for variable star. Null value is NaN.

- *`B-V`*: Color index. Null value is 0.

- *`SpType`*: Spectral type. Null value is NaN.

- *`Luminosity`*: Bolometric luminosity in solar units. Null value is 0.

- *`XJ2000`, `YJ2000`, `ZJ2000`*: Cartesian coordinates with respect to the Sun and in the J2000 reference frame. All values in **parsecs**.

- *`VXJ2000`, `VYJ2000`, `VZJ2000`*: Cartesian components of the velocity with respect to the Sun and in the J2000 reference frame. All values in **parsec/year**.

- *`Primary`*: HYG number of the primary star when the star is multiple. By default the primary of all stars are the HYG number of the same star.

- *`MultipleID`*: Gliese ID of the most bright component of the binary/multiple system to which the star belongs.

- *`IsMultiple`*: Is the star in a multiple system.

- *`IsVariable`*: Is the star variable.