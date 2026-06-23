---
title: "Digital Elevation Models from SRTM"
teaching: 25
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- What is Sentinel-2 imagery and how do I download it?
- What is a digital elevation model (DEM)?
- How do I download SRTM elevation data from EarthExplorer?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Search for and download Sentinel-2 multispectral imagery from the Copernicus Browser
- Understand what SRTM DEM data represents
- Download SRTM elevation tiles from USGS EarthExplorer

::::::::::::::::::::::::::::::::::::::::::::::::

## Sentinel-2 Multispectral Imagery

The [Sentinel-2 satellite program](https://www.copernicus.eu/en), launched in 2015 by the European Space Agency (ESA) as part of the EU's Copernicus Earth observation programme, provides free, high-resolution multispectral imagery across 13 spectral bands. Two satellites (2A and 2B) image the Earth's entire land surface approximately every 5 days at a resolution of 10 m in the visible bands — a significant improvement over the 15 m resolution of earlier free Landsat data.

Sentinel-2 imagery is especially useful for land cover classification, vegetation health monitoring (NDVI), environmental change detection, and heritage landscape analysis. Its combination of high spectral resolution (many band combinations), high temporal resolution (frequent revisits), and open access makes it one of the most valuable datasets for social science research involving human-environment interactions.

---

### Navigating the Copernicus Browser

::::::::::::::::::::::::::::::::::::: callout

### Before You Begin
Make sure you have a Copernicus Data Space account. If you do not have one, register for free at [https://identity.dataspace.copernicus.eu/](https://identity.dataspace.copernicus.eu/).

::::::::::::::::::::::::::::::::::::::::::::::::

1. Log in and navigate to the [Copernicus Browser](https://browser.dataspace.copernicus.eu/)
2. Use the map pane to zoom to your area of interest

---

### Searching for Imagery

With the **Visualize** tab active in the left pane, set your search criteria from top to bottom:

- **Date or date range** — select a specific date or click "show latest data." Days with available imagery are highlighted in blue.
- **Cloud cover** — use the slider to set a maximum (e.g., 10%)
- **Satellite** — select **Sentinel-2**
- **Band combination** — choose from preset layers such as True Color, NDVI, or Land Cover Classes

Once your criteria are set, click **Find products for current view**. This opens the **Search** tab and lists available scenes. Each scene corresponds to a green square on the map that highlights when you hover over the listing.

### Previewing Scenes

- Click the **i button** on a listed scene (or click its green square on the map) to view detailed metadata
- Click the **crosshairs icon** to zoom to a scene on the map
- Click **Visualize** below a scene's thumbnail to explore different band combinations interactively
- To adjust your search, click **Go to search** at the top of the pane, update your filters, and click **Search** again

### Downloading

- Click the **Download** button on the right side of a scene listing
- The file size is shown above the button — downloads may take time depending on your connection
- The downloaded file is a `.SAFE.ZIP` archive — extract it and import the contents into QGIS for visualization

:::::::::::::::::::::::::::::::::::: challenge

### Exercise 1: Download Sentinel-2 Imagery

1. Log in to the Copernicus Browser
2. Navigate to an area of interest and search for a recent, low-cloud-cover Sentinel-2 scene
3. Preview it using the True Color and NDVI band combinations
4. Download the scene

::::::::::::::::::::::::::::::::::::::::::::::::

---

## SRTM Digital Elevation Models

The [Shuttle Radar Topography Mission (SRTM)](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-digital-elevation-shuttle-radar-topography-mission-srtm-1) was a joint international project in 2000 that used radar data collected from the Space Shuttle *Endeavour* to produce one of the most accurate near-global digital elevation datasets of the Earth's land surface.

The most recent release, **SRTM 1 Arc-Second Global (V3, 2014)**, has a ground resolution of approximately 30 m per pixel and an absolute vertical accuracy of about 16 m. The dataset is divided into individual 1° × 1° tiles available for free download as GeoTIFF files.

When first imported into QGIS, raw DEM files appear as grayscale images — each pixel's shade represents the elevation of that 30 × 30 m area. From this raw data you can generate hillshade models, slope and aspect maps, elevation classes, and contour lines. We will practice several of these techniques in **Session 3a**.

---

### Downloading SRTM Data from EarthExplorer

The download process is similar to the CORONA workflow from the previous page, using the same EarthExplorer interface.

::::::::::::::::::::::::::::::::::::: callout

### Before You Begin
Make sure you are logged in to your [USGS EarthExplorer](https://earthexplorer.usgs.gov/) account.

::::::::::::::::::::::::::::::::::::::::::::::::

#### Step 1: Define Your Search Area

- Navigate to your area of interest in the map window
- Draw a search polygon or zoom in and click **Use Map**

#### Step 2: Select the Dataset

- Click the **Data Sets** tab
- Expand **Digital Elevation** → expand **SRTM**
- Select **SRTM 1 Arc-Second Global**

#### Step 3: Review and Download

- Click **Results** to see the available DEM tiles covering your area
- Use the **Footprint** and **Image Overlay** icons to preview tile coverage
- Click **Download Options** (disk icon with green arrow) and download the **GeoTIFF** format
- Save the file to your project folder

The downloaded GeoTIFF is already georeferenced and ready to load directly into QGIS.

:::::::::::::::::::::::::::::::::::: challenge

### Exercise 2: Download an SRTM Tile

1. Log in to EarthExplorer and navigate to the same area you used for Sentinel-2
2. Search for and download an SRTM 1 Arc-Second tile covering that area
3. Load the GeoTIFF into QGIS — you should see a grayscale elevation image

::::::::::::::::::::::::::::::::::::::::::::::::

---

:::::::::::::::::::::::::::::::::::::: keypoints

- Sentinel-2 provides free, high-resolution multispectral imagery with a ~5-day revisit cycle, useful for land cover and vegetation analysis.
- SRTM DEM tiles provide 30 m resolution elevation data that can be used to generate hillshade, slope, contour, and other terrain visualizations.
- Both Sentinel-2 and SRTM data are georeferenced and can be loaded directly into QGIS.

::::::::::::::::::::::::::::::::::::::::::::::::
