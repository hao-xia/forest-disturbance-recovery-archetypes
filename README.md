# Forest Disturbance-Recovery Archetypes

This repository provides GeoTIFF datasets used to map and characterize forest disturbance and recovery dynamics in Kaihua County, Zhejiang Province, China. The datasets were derived from dense Landsat time series using the LandTrendr algorithm (https://emapr.github.io/LT-GEE/index.html) and were used to compare forest disturbance-recovery archetypes inside and outside protected areas.

The repository supports a trajectory-based interpretation of forest change. Instead of describing forest dynamics only as binary loss or gain, the datasets summarize when disturbance and recovery occurred, how strong these changes were, how long they lasted, and how rapidly they unfolded. These trajectory metrics were further integrated into disturbance-recovery archetypes that represent recurring forest change pathways.

## Repository Structure

```text
data/
  geotiff/
    disturbance/
      disturbance.tif
    recovery/
      recovery.tif
    archetypes/
      Archetype_cluster_map.tif
```

## Dataset Description

### `data/geotiff/disturbance/disturbance.tif`

This GeoTIFF contains LandTrendr-derived forest disturbance metrics for baseline forest pixels.

| Band | Metric | Description |
|---|---|---|
| yod | Disturbance year | Year when the dominant disturbance segment started |
| mag | Disturbance magnitude | Spectral magnitude of the dominant disturbance event |
| dur | Disturbance duration | Duration of the dominant disturbance segment, in years |
| rate | Disturbance rate | Disturbance magnitude divided by disturbance duration |

Disturbance was identified as the dominant negative change segment in the fitted Landsat spectral trajectory.

### `data/geotiff/recovery/recovery.tif`

This GeoTIFF contains LandTrendr-derived forest recovery metrics for baseline forest pixels.

| Band | Metric | Description |
|---|---|---|
| yod | Recovery year | Year when the dominant recovery segment started |
| mag | Recovery magnitude | Spectral magnitude of the dominant recovery event |
| dur | Recovery duration | Duration of the dominant recovery segment, in years |
| rate | Recovery rate | Recovery magnitude divided by recovery duration |

Recovery was identified as the dominant positive change segment in the fitted Landsat spectral trajectory.

### `data/geotiff/archetypes/Archetype_cluster_map.tif`

This GeoTIFF contains the final disturbance-recovery archetype classification.

| Value | Archetype | Description |
|---|---|---|
| 0 | Stable forest | Baseline forest pixels with no detected dominant disturbance or recovery signal during the study period. |
| 1 | Intense recovery | Recovery-dominated trajectory with high recovery magnitude and rapid canopy regrowth, with little or no evident dominant disturbance signal. |
| 2 | Legacy disturbance | Disturbance-dominated trajectory with a detected disturbance event but no evident subsequent recovery signal. |
| 3 | Moderate turnover | Coupled disturbance-recovery trajectory with both disturbance and recovery signals, generally showing moderate disturbance and gradual recovery. |
| 4 | Moderate recovery | Recovery-dominated trajectory with moderate recovery magnitude and intermediate recovery duration. |
| 5 | Persistent recovery | Recovery-dominated trajectory characterized by early recovery onset, long recovery duration, and gradual sustained regrowth. |
| 6 | Intense turnover | Coupled disturbance-recovery trajectory with high disturbance magnitude followed by strong and relatively rapid recovery. |

The archetypes were identified by clustering disturbance and recovery trajectory metrics. They summarize recurring combinations of disturbance and recovery timing, magnitude, duration, and rate.


## Important Notes

- The datasets represent spectral disturbance and recovery derived from Landsat time series.
- Disturbance and recovery metrics should be interpreted as remote-sensing trajectory indicators, not direct measurements of biomass, forest structure, or biodiversity.
- Archetype classes summarize recurring trajectory patterns and should not be interpreted as universal ecological categories.
- Users should check projection, resolution, NoData values, and band order before analysis.

## Citation

If you use these datasets, please cite the associated manuscript:

Xia, H., Yuan, S., Yang, L., Mei, Z., and Huang, Y. An Integrated Trajectory-Based Framework for Characterizing Forest Disturbance-Recovery Archetypes Across Protection Contexts: Implications for Forest Conservation. Under Review.

## Contact

Dr. Hao Xia  
Earth and Society Research Hub (ESRAH), University of Hamburg  
Email: xiahaoland@gmail.com / hao.xia@uni-hamburg.de
