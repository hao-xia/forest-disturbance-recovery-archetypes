# Forest Disturbance-Recovery Archetypes

This repository provides GeoTIFF datasets used to map and characterize forest disturbance and recovery dynamics in Kaihua County, Zhejiang Province, China. The datasets were derived from dense Landsat time series using the LandTrendr algorithm and were used to compare forest disturbance-recovery pathways inside and outside protected areas.

The repository supports a trajectory-based interpretation of forest change. Instead of describing forest dynamics only as binary loss or gain, the datasets summarize when disturbance and recovery occurred, how strong these changes were, how long they lasted, and how rapidly they unfolded. These trajectory metrics were further integrated into disturbance-recovery archetypes that represent recurring forest change pathways.

## Study Area

Kaihua County is located in the subtropical forest region of eastern China. The county contains extensive forest cover, multiple protected areas, and important mid-subtropical evergreen broad-leaved forest ecosystems. These conditions make it a suitable landscape for examining long-term forest disturbance, recovery, and protected-area associated patterns.

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
| 1 | Disturbance year | Year when the dominant disturbance segment started |
| 2 | Disturbance magnitude | Spectral magnitude of the dominant disturbance event |
| 3 | Disturbance duration | Duration of the dominant disturbance segment, in years |
| 4 | Disturbance rate | Disturbance magnitude divided by disturbance duration |

Disturbance was identified as the dominant negative change segment in the fitted Landsat spectral trajectory.

### `data/geotiff/recovery/recovery.tif`

This GeoTIFF contains LandTrendr-derived forest recovery metrics for baseline forest pixels.

| Band | Metric | Description |
|---|---|---|
| 1 | Recovery year | Year when the dominant recovery segment started |
| 2 | Recovery magnitude | Spectral magnitude of the dominant recovery event |
| 3 | Recovery duration | Duration of the dominant recovery segment, in years |
| 4 | Recovery rate | Recovery magnitude divided by recovery duration |

Recovery was identified as the dominant positive change segment in the fitted Landsat spectral trajectory.

### `data/geotiff/archetypes/Archetype_cluster_map.tif`

This GeoTIFF contains the final disturbance-recovery archetype classification.

| Value | Class |
|---|---|
| 0 | Stable forest |
| 1 | Intense recovery |
| 2 | Legacy disturbance |
| 3 | Moderate turnover |
| 4 | Moderate recovery |
| 5 | Persistent recovery |
| 6 | Intense turnover |

The archetypes were identified by clustering disturbance and recovery trajectory metrics. They summarize recurring combinations of disturbance and recovery timing, magnitude, duration, and rate.

## Conceptual Workflow

The datasets were produced using four main steps:

1. **Baseline forest masking**  
   A baseline forest mask was used to restrict the analysis to pixels classified as forest at the beginning of the monitoring period.

2. **Trajectory segmentation**  
   Dense Landsat time series were analyzed with LandTrendr to fit annual spectral trajectories and identify disturbance and recovery segments.

3. **Metric extraction**  
   For each forest pixel, the dominant disturbance and recovery segments were summarized using year, magnitude, duration, and rate.

4. **Archetype classification**  
   Disturbance and recovery metrics were integrated through clustering to identify recurring disturbance-recovery archetypes.

## Suggested Uses

These datasets can be used to:

- map the timing and intensity of forest disturbance and recovery;
- compare forest change inside and outside protected areas;
- identify recovery-dominated, disturbance-dominated, and turnover pathways;
- support forest restoration prioritization;
- support protected-area monitoring and adaptive forest management;
- examine spatial patterns of forest disturbance-recovery dynamics.

## Important Notes

- The datasets represent spectral disturbance and recovery derived from Landsat time series.
- Disturbance and recovery metrics should be interpreted as remote-sensing trajectory indicators, not direct measurements of biomass, forest structure, or biodiversity.
- Archetype classes summarize recurring trajectory patterns and should not be interpreted as universal ecological categories.
- Users should check projection, resolution, NoData values, and band order before analysis.
- Each GeoTIFF file is smaller than 100 MB and can be stored in a standard GitHub repository without Git LFS.

## Citation

If you use these datasets, please cite the associated manuscript:

Xia, H., Yuan, S., Yang, L., Mei, Z., and Huang, Y. An Integrated Trajectory-Based Framework for Characterizing Forest Disturbance-Recovery Archetypes Across Protection Contexts: Implications for Forest Conservation.

## Contact

Hao Xia  
University of Hamburg  
Email: xiahaoland@gmail.com
