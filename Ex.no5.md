# Ex05 Image Carousel
## Date:07-05-25

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
# Carousel.jsx
```
import React, { useState } from 'react';
import './index.css';

const Carousel = ({ images }) => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const goToPrevious = () => {
    setCurrentIndex((prev) => (prev === 0 ? images.length - 1 : prev - 1));
  };

  const goToNext = () => {
    setCurrentIndex((prev) => (prev === images.length - 1 ? 0 : prev + 1));
  };

  return (
    <div className="carousel">
      <h2 className="app-container">Image Carousel</h2>
      <h1 className="app-container">Shrikrishna V</h1>
      <div>
      <button onClick={goToPrevious} className="nav left">&#10094;</button>
      <img src={images[currentIndex]} alt="carousel-slide" />
      <button onClick={goToNext} className="nav right">&#10095;</button>
      <div className="indicators">
        {images.map((_, idx) => (
          <span
            key={idx}
            className={idx === currentIndex ? 'dot active' : 'dot'}
            onClick={() => setCurrentIndex(idx)}
          ></span>
        ))}
        </div>
      </div>
    </div>
  );
};

export default Carousel;
```
# index.css
```
body {
    margin: 0;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f5f5f5;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  
  .app-container {
    text-align: center;
  }
  
  .carousel {
    position: relative;
    width: 900px;
    height: 600px;
    margin: auto;
    overflow: hidden;
    border-radius: 12px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.3);
  }
  
  .carousel img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
  
  .nav {
    position: absolute;
    top: 50%;
    font-size: 30px;
    color: white;
    background-color: rgba(0,0,0,0.5);
    border: none;
    padding: 10px;
    cursor: pointer;
    transform: translateY(-50%);
    z-index: 10;
    border-radius: 50%;
  }
  
  .left {
    left: 10px;
  }
  
  .right {
    right: 10px;
  }
  
  .indicators {
    position: absolute;
    bottom: 10px;
    width: 100%;
    text-align: center;
  }
  
  .dot {
    display: inline-block;
    width: 12px;
    height: 12px;
    margin: 0 5px;
    background-color: rgba(255,255,255,0.6);
    border-radius: 50%;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .dot.active {
    background-color: white;
  }
```
# App.jsx
```
import React from "react";

import "./index.css";

import ben10 from "./assets/ben10.jpg";
import chhota from "./assets/chhota.jpg";
import shin from "./assets/shin.jpg";
import Carousel from "./carousel";

const App = () => {
  const images = [ben10, chhota, shin];

  return (
    <div>
      <Carousel images={images}/>
      {/* <Carousel images={images}/> */}
    </div>
  );
};

export default App;

```
## OUTPUT


## RESULT
The program for creating Image Carousel using React is executed successfully.
