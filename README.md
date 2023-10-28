////// Q 21
<!DOCTYPE html>
<html>
<head>
    <title>Background Color Toggle</title>
</head>
<body>
    <button id="toggleButton">Toggle Background Color</button>

    <script>
        const button = document.getElementById("toggleButton");
        let isBackgroundColorChanged = false;

        button.addEventListener("click", function() {
            const body = document.body;

            if (isBackgroundColorChanged) {
                // If the background color is changed, reset it to the default.
                body.style.backgroundColor = "";
            } else {
                // Change the background color to a new color (e.g., light blue).
                body.style.backgroundColor = "lightblue";
            }

            // Toggle the state of the background color.
            isBackgroundColorChanged = !isBackgroundColorChanged;
        });
    </script>
</body>
</html>

\\\\\\\\\ Q22
HTML:
html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
  <div class="slider">
    <div class="slide">
      <img src="image1.jpg" alt="Image 1">
    </div>
    <div class="slide">
      <img src="image2.jpg" alt="Image 2">
    </div>
    <div class="slide">
      <img src="image3.jpg" alt="Image 3">
    </div>
  </div>
  <button class="prev" onclick="changeSlide(-1)">Previous</button>
  <button class="next" onclick="changeSlide(1)">Next</button>

  <script src="script.js"></script>
</body>
</html>


CSS (styles.css):
css
body {
  text-align: center;
}

.slider {
  display: flex;
  overflow: hidden;
  max-width: 600px;
  margin: 0 auto;
}

.slide {
  flex: 0 0 100%;
  transition: transform 0.5s;
}

img {
  width: 100%;
}

button {
  margin: 10px;
  padding: 10px 20px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}


JavaScript (script.js):
javascript
let currentSlide = 0;
const slides = document.querySelectorAll('.slide');
const totalSlides = slides.length;

function showSlide(slideIndex) {
  if (slideIndex >= totalSlides) {
    currentSlide = 0;
  } else if (slideIndex < 0) {
    currentSlide = totalSlides - 1;
  }

  slides.forEach((slide, index) => {
    slide.style.transform = `translateX(${100 * (index - currentSlide)}%)`;
  });
}

function changeSlide(step) {
  currentSlide += step;
  showSlide(currentSlide);
}

showSlide(currentSlide);

//////// Q 23
<!DOCTYPE html>
<html>
<head>
    <title>Background Color Toggle</title>
</head>
<body>
    <button id="toggleButton">Toggle Background Color</button>

    <script>
        const button = document.getElementById("toggleButton");
        let isBackgroundColorChanged = false;

        button.addEventListener("click", function() {
            const body = document.body;

            if (isBackgroundColorChanged) {
                // If the background color is changed, reset it to the default.
                body.style.backgroundColor = "";
            } else {
                // Change the background color to a new color (e.g., light blue).
                body.style.backgroundColor = "lightblue";
            }

            // Toggle the state of the background color.
            isBackgroundColorChanged = !isBackgroundColorChanged;
        });
    </script>
</body>
</html>

////////// Q 24
import React, { useState, useEffect } from 'react';

function BookList() {
  const [books, setBooks] = useState([]);

  useEffect(() => {
    // Fetch data from the Google Books API
    fetch('https://www.googleapis.com/books/v1/volumes?q=javascript')
      .then((response) => response.json())
      .then((data) => {
        // Extract the array of books from the API response
        const bookData = data.items || [];
        setBooks(bookData);
      })
      .catch((error) => console.error('Error fetching data:', error));
  }, []);

  return (
    <div>
      <h1>Book List</h1>
      <ul>
        {books.map((book, index) => (
          <li key={index}>{book.volumeInfo.title}</li>
        ))}
      </ul>
    </div>
  );
}

export default BookList;

///////// Q 24 APP.JS
Q 24 app.js 
import React from 'react';
import './App.css';
import BookList from './BookList';

function App() {
  return (
    <div className="App">
      <BookList />
    </div>
  );
}

export default App;


