# Stellar Catalogue for Montu Python /mnṯw ꜥꜣpp(y)/
## Astronomical ephemerides for the ancient world

These are the tools to create the stellar catalogue for [`MontuPython`](https://github.com/seap-udea/MontuPython).

<p align="center"><img src="https://github.com/seap-udea/MontuCatalogue/blob/main/map-allstars-colors.png?raw=true" alt="Logo""/></p>

The catalogue of `MontuPython` is an improved and slightly extended version of the incredible work of David Nash, who during almost a decade has created and released his version of the [HYG database](http://www.astronexus.com/hyg).  This catalogue has been adapted by Prof. Jorge I. Zuluaga (Universidad de Antioquia, Colombia).

The `MontuCatalogue` is based on HYG but several improvements and adaptations has been done for making the catalogue useful for the purposes of the package.

These are the columns included in `MontuCatalogue`:

- **`MN`**: `MontuCatalogue` index.

- **`HD`**: Number in the HD catalogue. Null value is 0.

- **`HR`**: Number in the HR catalogue. Null value is 0.

- **`HIP`**: Number in the HR catalogue. Null value is 0.

- **`Gl`**: Gliese catalogue designation. Null value is 'NaN'.

- **`Name`**: Name of the star. According to availability the name is asignated in this order: Proper name, Bayer name, Flamsteed name, HD designation, HR  designation, HIP designation, HYG designation

- **`OtherDesignations`**: All available designations for the star.

- **`ProperName`**: Proper name in the IAU database. Null value is 'NaN'.

- **`Bayer`**: Bayer designation as a greek letter [number] and constellation abbreviature. Null value is 'NaN'.

- **`Flamsteed`**: Bayer designation as a number and constellation abbreviature. Null value is 'NaN'.

- **`Constellation`**: Constellation abreviature. 

- **`RAJ2000`**: Right ascension at J2000.0 epoch in **degrees**. Not null value.

- **`DecJ2000`**: Right ascension at J2000.0 epoch in **degrees**. Not null value.

- **`pmRA`**: Proper motion in right ascension in **mas/year**. Null value is 0.

- **`pmDec`**: Proper motion in declination in **mas/year**. Null value is 0.

- **`RadVel`**: Radial velocity in **km/s**. Null value is 0.

- **`Distance`**: Distance in **parsecs**. Null value is 0. 

- **`Vmag`**: Visual magnitude (either in band V or G). Not null values.

- **`Vmag_min`**: Minimum brightness in visual magnitude for variable star. Null value is NaN.

- **`Vmag_max`**: Maximum brightness in visual magnitude for variable star. Null value is NaN.

- **`B-V`**: Color index. Null value is 0.

- **`SpType`**: Spectral type. Null value is NaN.

- **`Luminosity`**: Bolometric luminosity in solar units. Null value is 0.

- **`XJ2000`, `YJ2000`, `ZJ2000`**: Cartesian coordinates with respect to the Sun and in the J2000 reference frame. All values in **parsecs**.

- **`VXJ2000`, `VYJ2000`, `VZJ2000`**: Cartesian components of the velocity with respect to the Sun and in the J2000 reference frame. All values in **parsec/year**.

- **`Primary`**: HYG number of the primary star when the star is multiple. By default the primary of all stars are the HYG number of the same star.

- **`MultipleID`**: Gliese ID of the most bright component of the binary/multiple system to which the star belongs.

- **`IsMultiple`**: Is the star in a multiple system.

- **`IsVariable`**: Is the star variable.

To downloa the catalogue use the link to the raw file: https://raw.githubusercontent.com/seap-udea/MontuCatalogue/main/catalogues/montu_stellar_catalogue.csv.

You may load the catalogue using:

```python
import pandas as pd
montu_cat = pd.read_csv('montu_stellar_catalogue.csv')
```

and obtain some interesting statistics on its content:

```python
print("Catalogue completeness:")
cat = montu_cat
nstars = len(cat)
columns = cat.columns
for col in columns:
    ncomplete = (~(cat[col].isnull())).sum()
    print(f"\t{col}: {ncomplete}/{nstars} ({ncomplete/nstars*100:.1f}%)")

cond_pn = (~montu_cat.ProperName.isnull())
print("Number of stars with proper name: ",cond_pn.sum())
cond_by = (~montu_cat.Bayer.isnull())
print("Number of stars with Bayer name: ",cond_by.sum())
cond_fm = (~montu_cat.Flamsteed.isnull())
print("Number of stars with Flamsteed name: ",cond_fm.sum())
cond_all = (cond_pn)&(cond_by)&(cond_fm)
print("Number of proper, Bayer and Flamsteed: ",cond_all.sum())

cond = (montu_cat.Vmag<=6.5)
nvis = len(np.unique(montu_cat.loc[cond,'HD']))
print("Number of naked eye stars: ",nvis)
```

Here are the statistics for the latest version of the catalogue which is based in `HYG 3.7`:

```
Catalogue completeness:
	MN: 119626/119626 (100.0%)
	HD: 119626/119626 (100.0%)
	HR: 119626/119626 (100.0%)
	HIP: 119626/119626 (100.0%)
	Gl: 3801/119626 (3.2%)
	Name: 119626/119626 (100.0%)
	OtherDesignations: 119626/119626 (100.0%)
	ProperName: 367/119626 (0.3%)
	Bayer: 1537/119626 (1.3%)
	Flamsteed: 2737/119626 (2.3%)
	Constellation: 119625/119626 (100.0%)
	RAJ2000: 119626/119626 (100.0%)
	DecJ2000: 119626/119626 (100.0%)
	pmRA: 119626/119626 (100.0%)
	pmDec: 119626/119626 (100.0%)
	RadVel: 119626/119626 (100.0%)
	Distance: 119626/119626 (100.0%)
	Vmag: 119626/119626 (100.0%)
	Vmag_min: 16991/119626 (14.2%)
	Vmag_max: 16991/119626 (14.2%)
	B-V: 119626/119626 (100.0%)
	SpType: 116578/119626 (97.5%)
	Luminosity: 119626/119626 (100.0%)
	XJ2000: 119626/119626 (100.0%)
	YJ2000: 119626/119626 (100.0%)
	ZJ2000: 119626/119626 (100.0%)
	VXJ2000: 119626/119626 (100.0%)
	VYJ2000: 119626/119626 (100.0%)
	VZJ2000: 119626/119626 (100.0%)
	Primary: 119626/119626 (100.0%)
	MultipleID: 1086/119626 (0.9%)
	IsMultiple: 119626/119626 (100.0%)
	IsVariable: 119626/119626 (100.0%)
Number of stars with proper name:  367
Number of stars with Bayer name:  1537
Number of stars with Flamsteed name:  2737
Number of proper, Bayer and Flamsteed:  263
Number of naked eye stars:  8896
```

## `MontuCatalogue` in `MontuPython`

As pointed out before, `MontuCatalogue` has been developed along with the astronomical package `MontuPython`. You may load the complete star catalogue of `MontuCatalogue`  using:

```python
import montu as mn
allstars = montu.Stars()
```

The data of the catalogue is in the attribute `allstars.data` which correspond to a `pandas dataframe`.

Once loaded you can filter the stars:

```python
aldebaran = allstars.get_stars(ProperName='Aldebaran')
stars = allstars.get_stars(Vmag=[-2,6.5])
print(f"There is {stars.number} visible to the naked eye in the catalogue")
hyades = stars.get_stars_around(center=[aldebaran.data.RAJ2000,aldebaran.data.DecJ2000],radius=5.5,Vmag=[-1,5])
```

You may precess the coordinates of the stars using:

```python
mtime = mn.Time('1000-01-01 00:00:00')
stars.where_in_space(at=mtime)
```

------------

This package has been designed and written by Jorge I. Zuluaga (C) 2023