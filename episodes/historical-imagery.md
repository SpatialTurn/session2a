---
title: "Acquiring Raster Data using Imagery Databases"
teaching: 25
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- Where can I find scanned historical maps for use in GIS?
- What is CORONA satellite imagery and why is it valuable?
- How do I search for and download CORONA imagery?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand the difference between georeferenced and non-georeferenced raster data
- Download a scanned historical map from a public repository
- Search for and download CORONA imagery from the CAST website and USGS EarthExplorer

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Raster data — scanned maps, aerial photographs, satellite imagery, elevation models — forms the visual backbone of many GIS projects. Some raster files come **georeferenced** (positioned in real-world coordinates and ready to use), while others, like scanned paper maps, are **non-georeferenced** and must be aligned manually before they can overlay with other data layers.

This session introduces two categories of historical raster data: scanned maps from online repositories and declassified CORONA spy satellite imagery.

---

## Downloading Scanned Historical Maps

Several public and academic websites host scanned paper maps that are free to download. These are typically non-georeferenced images — you will need to georeference them before using them in QGIS.

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

## CORONA Satellite Imagery

During the Cold War the United States operated a series of classified reconnaissance satellites. The [CORONA program (1960–1972)](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-declassified-data-declassified-satellite-imagery-1) produced over 860,000 black-and-white images — the first high-resolution (up to ~2 m) stereo photographs of the Earth's surface. The imagery was declassified in 1995.

The highest-resolution images come from the **KH-4B** series (1967–1972), captured on panoramic film strips each covering roughly 8.6 × 117 km. High-resolution scans are available from USGS EarthExplorer at no cost (at up to 3600 dpi), or for $30 per frame for scenes that have not yet been scanned.

Since declassification, CORONA imagery has been widely used to study historical landscapes, identify archaeological sites, trace old land tenure boundaries, and document features lost to urbanization or agricultural expansion.

---

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

---

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

:::::::::::::::::::::::::::::::::::::: keypoints

- Scanned historical maps are widely available online but usually require georeferencing before use in a GIS.
- CORONA imagery (1960–1972) provides high-resolution historical views of the Earth's surface and is free to download.
- The CAST website offers pre-georeferenced CORONA scenes for quick use; EarthExplorer hosts the complete global archive.

::::::::::::::::::::::::::::::::::::::::::::::::
