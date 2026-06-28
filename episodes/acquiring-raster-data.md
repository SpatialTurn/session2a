---
title: "Exercises: Acquiring Raster Data using Imagery Databases"
teaching: 40
exercises: 15
---

:::::::::::::::::::::::::::::::::::::: questions

- Where can I find scanned historical maps for use in GIS?
- What is CORONA satellite imagery and how do I download it?
- How do I acquire Sentinel-2 multispectral imagery?
- What is a digital elevation model (DEM) and where do I get one?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand the difference between georeferenced and non-georeferenced raster data
- Download a scanned historical map from a public repository
- Search for and download CORONA imagery from the CAST website and USGS EarthExplorer
- Download Sentinel-2 imagery from the Copernicus Browser
- Download SRTM elevation data from USGS EarthExplorer

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Raster data — scanned maps, aerial photographs, satellite imagery, elevation models — forms the visual backbone of many GIS projects. Some raster files come **georeferenced** (positioned in real-world coordinates and ready to use), while others, like scanned paper maps, are **non-georeferenced** and must be aligned manually before they can overlay with other data layers.

This session covers four types of raster data, moving from historical sources to modern satellite products.

---

## 1. Scanned Historical Maps

Several public and academic websites host scanned paper maps that are free to download. These are typically non-georeferenced — you will need to georeference them before using them in QGIS.

::::::::::::::::::::::::::::::::::::: callout

### Useful Map Repositories

- [Perry-Castañeda Library Map Collection](https://legacy.lib.utexas.edu/maps/) — University of Texas; thousands of scanned maps organized by region
- [National Library of Australia Trove](https://trove.nla.gov.au/) — Australian maps, photographs, and archival material
- [Old Maps Online](https://www.oldmapsonline.org/) — aggregates historical maps from libraries worldwide

::::::::::::::::::::::::::::::::::::::::::::::::

### Walkthrough: Perry-Castañeda Library

1. Go to [https://legacy.lib.utexas.edu/maps/](https://legacy.lib.utexas.edu/maps/)
2. Scroll down and click **Historical**
3. Browse by topic or region until you find a useful map — large military topographic series often include index maps to help locate a specific area
4. Right-click the map image and select **Save Image As**, then save it to your project folder

---

## 2. CORONA Satellite Imagery

During the Cold War the United States operated a series of classified reconnaissance satellites. The [CORONA program (1960–1972)](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-declassified-data-declassified-satellite-imagery-1) produced over 860,000 black-and-white images — the first high-resolution (up to ~2 m) stereo photographs of the Earth's surface. The imagery was declassified in 1995.

The highest-resolution images come from the **KH-4B** series (1967–1972), captured on panoramic film strips each covering roughly 8.6 × 117 km. High-resolution scans are available from USGS EarthExplorer at no cost (at up to 3600 dpi), or for $30 per frame for scenes that have not yet been scanned.

Since declassification, CORONA imagery has been widely used to study historical landscapes, identify archaeological sites, trace old land tenure boundaries, and document features lost to urbanization or agricultural expansion.

### Option A: Pre-Georeferenced Imagery from CAST

The [CORONA Atlas at the University of Arkansas CAST](https://corona.cast.uark.edu/) provides a subset of CORONA scenes that have already been georeferenced — ready to use directly in QGIS.

1. Go to [https://corona.cast.uark.edu/](https://corona.cast.uark.edu/) and click **Explore Atlas**
2. Red rectangles on the map show available missions — zoom in to your area of interest
3. Use the slider tool at the bottom of the screen to compare CORONA and modern imagery side by side
4. Adjust transparency with the slider next to **Corona Imagery** to see how features have changed
5. Expand the **Corona Imagery** layer with the **(+)** button to see individual images

::::::::::::::::::::::::::::::::::::: callout

### Tip
As you zoom in, fewer missions will be listed — this is normal, since each scene covers a specific footprint.

::::::::::::::::::::::::::::::::::::::::::::::::

6. Toggle images on and off to find the best one, then click the blue download button **(V)** next to it
7. Click **Download GeoTiff** — these are large files, so the download may take a few minutes
8. Move the downloaded file to a dedicated folder (e.g., `CORONA/`) in your GIS project directory

#### Loading the image in QGIS

1. Open QGIS and click the **Open Data Source Manager** button on the toolbar
2. Select the **Raster** tab, click **Browse**, and navigate to your CORONA GeoTIFF
3. Click **Open → Add → Close**

:::::::::::::::::::::::::::::::::::: challenge

### Exercise 1: Download from CAST

Download a CORONA image of your area of interest (or a famous landmark) from the CAST website. Load it into QGIS and explore the scene.

::::::::::::::::::::::::::::::::::::::::::::::::

### Option B: Full Archive from USGS EarthExplorer

The CAST atlas covers a limited area. For global coverage, use the complete CORONA archive on [USGS EarthExplorer](https://earthexplorer.usgs.gov/).

::::::::::::::::::::::::::::::::::::: callout

### Before You Begin
Make sure you are logged in to your EarthExplorer account. If you do not have one, create a free account at [https://earthexplorer.usgs.gov/](https://earthexplorer.usgs.gov/).

::::::::::::::::::::::::::::::::::::::::::::::::

#### Step 1: Define Your Search Area

- In the map window, navigate to your area of interest
- Click corners on the map to draw a search polygon, or zoom in and click **Use Map** in the Search Criteria pane
- Your search area will appear as a semi-transparent red polygon

#### Step 2: Select the Dataset

- Click the **Data Sets** tab
- Expand **Declassified Data** → select **Declass 1 (1996)**

#### Step 3: Filter for High-Quality Imagery

- Click the **Additional Criteria** tab
- Expand **Camera Resolution** and select **Stereo High** (this limits results to the best KH-4B imagery)
- Optionally, expand **Download Availability** and select **Yes** to show only pre-scanned images (leave blank to see all coverage, including frames available for $30)

#### Step 4: Review and Download

- Click **Results** to see available scenes
- Use the **Footprint** and **Image Overlay** icons to preview coverage on the map
- Click **Show Metadata and Browse** (the paper icon) to check cloud cover and image clarity
- When you have chosen a scene, click the **Download Options** button (disk icon with green arrow) and select **Download**

#### Step 5: Extract the Files

- Move the downloaded `.tgz` file to your project folder
- Extract with **7-Zip → Extract Here** to get a `.tar` file
- Extract the `.tar` file again — this produces four `.tif` files (the panoramic strip split into segments labeled a, b, c, and d)

::::::::::::::::::::::::::::::::::::: callout

### Note
Raw CORONA imagery from EarthExplorer is **not georeferenced**. You will need to georeference it in QGIS before it can be overlaid with other spatial data.

::::::::::::::::::::::::::::::::::::::::::::::::

---

## 3. Sentinel-2 Multispectral Imagery

The [Sentinel-2 satellite program](https://www.copernicus.eu/en), launched in 2015 by the European Space Agency as part of the EU's Copernicus programme, provides free, high-resolution multispectral imagery across 13 spectral bands. Two satellites (2A and 2B) image the entire land surface approximately every 5 days at 10 m resolution in the visible bands.

Sentinel-2 imagery is especially useful for land cover classification, vegetation health monitoring (NDVI), and environmental change detection.

### Searching and Downloading from the Copernicus Browser

::::::::::::::::::::::::::::::::::::: callout

### Before You Begin
Make sure you have a Copernicus Data Space account. Register for free at [https://identity.dataspace.copernicus.eu/](https://identity.dataspace.copernicus.eu/).

::::::::::::::::::::::::::::::::::::::::::::::::

1. Log in and navigate to the [Copernicus Browser](https://browser.dataspace.copernicus.eu/)
2. Zoom to your area of interest in the map pane

With the **Visualize** tab active, set your search criteria:

- **Date or date range** — select a date or click "show latest data"
- **Cloud cover** — use the slider to set a maximum (e.g., 10%)
- **Satellite** — select **Sentinel-2**
- **Band combination** — choose a preset such as True Color, NDVI, or Land Cover Classes

Click **Find products for current view** to open the **Search** tab with matching scenes. Each scene corresponds to a green square on the map.

#### Previewing and Downloading

- Click the **i button** on a scene to view metadata, or the **crosshairs icon** to zoom to it
- Click **Visualize** below a thumbnail to explore band combinations interactively
- To download, click the **Download** button on the right side of a listing — the file is a `.SAFE.ZIP` archive that can be extracted and imported into QGIS

:::::::::::::::::::::::::::::::::::: challenge

### Exercise 2: Download Sentinel-2 Imagery

1. Search for a recent, low-cloud-cover Sentinel-2 scene over your area of interest
2. Preview it using the True Color and NDVI band combinations
3. Download the scene

::::::::::::::::::::::::::::::::::::::::::::::::

---

## 4. SRTM Digital Elevation Models

The [Shuttle Radar Topography Mission (SRTM)](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-digital-elevation-shuttle-radar-topography-mission-srtm-1) was a joint international project in 2000 that used radar from the Space Shuttle *Endeavour* to produce one of the most accurate near-global elevation datasets. The most recent release, **SRTM 1 Arc-Second Global (V3, 2014)**, has ~30 m resolution and is divided into 1° × 1° tiles available as free GeoTIFF downloads.

When loaded into QGIS, raw DEM files appear as grayscale images where each pixel's shade represents the elevation of that 30 × 30 m area. From this data you can generate hillshade, slope, aspect, and contour layers — we will do exactly that in the next session.

### Downloading from EarthExplorer

The process follows the same EarthExplorer interface used for CORONA above.

#### Step 1: Define Your Search Area

- Navigate to your area of interest and draw a search polygon or click **Use Map**

#### Step 2: Select the Dataset

- Click the **Data Sets** tab
- Expand **Digital Elevation** → **SRTM** → select **SRTM 1 Arc-Second Global**

#### Step 3: Download

- Click **Results** to see available tiles
- Use the **Footprint** icon to preview coverage
- Click **Download Options** and download the **GeoTIFF** format
- Save the file to your project folder

The downloaded GeoTIFF is already georeferenced and ready to load into QGIS.

:::::::::::::::::::::::::::::::::::: challenge

### Exercise 3: Download an SRTM Tile

1. Using EarthExplorer, download an SRTM tile covering the same area you used for Sentinel-2
2. Load the GeoTIFF into QGIS — you should see a grayscale elevation image

::::::::::::::::::::::::::::::::::::::::::::::::

---

:::::::::::::::::::::::::::::::::::::: keypoints

- Scanned historical maps are widely available online but usually require georeferencing before use in a GIS.
- CORONA imagery (1960–1972) provides high-resolution historical views and is free from CAST (georeferenced) or EarthExplorer (raw).
- Sentinel-2 provides free, 10 m resolution multispectral imagery with a ~5-day revisit cycle.
- SRTM DEM tiles provide 30 m elevation data that can be used for terrain analysis in the next session.

::::::::::::::::::::::::::::::::::::::::::::::::
