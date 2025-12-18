# ocean-config-for-rcm3-dev

### Contents:
- `notebooks/setup/regional-mom6-forced-by-access-om2-SEAus_domain.ipynb` is the notebook used to generate the horizontal and vertical grids, bathymetry file, and initial and lateral boundary condition files
- `notebooks/analysis/plot-surface-fields.ipynb` basic script to look at outputs
- `rundir/tiny-ocean-rcm3-dev/` is the model run directory
- `input/tiny-ocean-rcm3-dev/` is the model input directory. Since the test case is small/short, I've uploaded the whole thing

### Files of interest
- `input/tiny-ocean-rcm3-dev/hgrid.nc` is the horizontal grid
- `input/tiny-ocean-rcm3-dev/ocean_mask.nc` is the land/sea mask
- `input/tiny-ocean-rcm3-dev/access-rom3-ESMFmesh.nc` is the ESMF mesh generated from `hgrid.nc` and `ocean_mask.nc` using [this script](https://github.com/COSIMA/om3-scripts/blob/39c7c7b2c8f21bbe798f1b5e8073951f7353ae90/mesh_generation/generate_mesh.py)
- `input/tiny-ocean-rcm3-dev/access-rom3-nomask-ESMFmesh.nc` is the ESMF mesh generated from `hgrid.nc` 

### About the model config
- Tiny!! Nominal resolution 0.1°, domain size 1° x 1° 
- latitude_extent = [-47, -46]
- longitude_extent = [141.5, 142.5]
- date_range = ["2013-01-01", "2013-01-31"]
- Runs on a single CPU
- Note that the way that 'regional_mom6.py' grid generation works is that a 1°-wide domain at 0.1° resolution will give you 10 grid points in x (`NIGLOBAL = 10`), but the number of points in y (`NJGLOBAL`) will be set to give the same resolution (in km), on average, as the x direction, i.e., `NIGLOBAL` will only equal `NJGLOBAL` near the equator. For our domain which is centered on 46.5 S, `NJGLOBAL = 15`
