# Scale Ratio Control  

A custom control for MapLibre that enables users to:  
- Display the scale ratio (e.g., `1:15000`) based on the current zoom level.  
- Set the zoom level by inputting a scale ratio.  

The scale ratio is calculated using the **latitude at the center of the map view** and an **optional DPI value (default: 96)**.  

---

## Features  

- Seamlessly integrates with MapLibre.  
- Customizable DPI settings for screen or print environments.
- Lightweight and easy to use.  

---

## Demo  

Demo coming soon on GitHub Pages.  

---

## Installation  

### via npm  

(to be added)

### via CDN  

(to be added)

---

## Usage  

### 1. Import the control  

```javascript  
import { ScaleRatioControl } from 'scale-ratio-control';  
```  

### 2. Include the CSS file in your HTML  

For projects using a bundler (e.g., Webpack):  
```javascript  
import 'scale-ratio-control/dist/ScaleRatioControl.css';  
```  

For direct use in the browser:  
(to be added)

### 3. Add the control to your map  

```javascript  
const control = new ScaleRatioControl(map);  
map.addControl(control, 'top-left');  
```  

---

## API Reference  

### `ScaleRatioControl`  

A MapLibre control for handling scale ratios.  

#### Constructor  

```javascript  
new ScaleRatioControl(map, dpi = 96);  
```  

**Parameters**:  
- `map` (required): The MapLibre map instance.  
- `dpi` (optional): Dots Per Inch (DPI) value for the environment. This can represent the DPI of a screen (default: 96) or a printer for paper outputs.  


**Example Usage**:  
```javascript  
const scaleRatioControl = new ScaleRatioControl(map); 
map.addControl(scaleRatioControl, 'top-right');  
```  

## Advanced Usage: Utility Functions

This package also exports two utility functions that can be used independently of the `ScaleRatioControl`. These functions allow you to calculate the zoom level from a scale ratio or derive the scale ratio from a zoom level and latitude.

### `getZoomLevelFromScaleRatio`

Calculates the zoom level based on a given scale ratio, latitude, and DPI.

**Parameters:**
- `scaleRatio` (number, required): The scale ratio (e.g., `1:x`, where `x` is the ratio).
- `latitude` (number, required): The latitude in degrees.
- `dpi` (number, optional): Screen or paper DPI (default: 96).

**Returns:**
- The zoom level as a number.

**Example:**
```javascript
import { getZoomLevelFromScaleRatio } from 'scale-ratio-control';

const zoomLevel = getZoomLevelFromScaleRatio(15000, 35.6895); // Scale ratio 1:15000, latitude 35.6895° (e.g., Tokyo)
console.log(zoomLevel); // Outputs the calculated zoom level
```

---

### `getScaleRatio`

Calculates the scale ratio (`1:x`) based on the zoom level, latitude, and DPI.

**Parameters:**
- `zoomLevel` (number, required): The zoom level of the map.
- `latitude` (number, required): The latitude in degrees.
- `dpi` (number, optional): Screen or paper DPI (default: 96).

**Returns:**
- The scale ratio as a number.

**Example:**
```javascript
import { getScaleRatio } from 'scale-ratio-control';

const scaleRatio = getScaleRatio(15, 35.6895); // Zoom level 15, latitude 35.6895° (e.g., Tokyo)
console.log(scaleRatio); // Outputs the scale ratio
```


---

## License  

This project is licensed under the [MIT License](./LICENSE).