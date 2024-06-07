<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Page</title>
    <style>
        /* CSS code goes here */
        /* General styles for the container and product layout */
        .container {
            max-width: 1000px;
            margin: auto;
            padding: 20px;
        }

        .product-layout {
            display: flex;
            align-items: flex-start;
            flex-wrap: wrap;
        }

        /* Carousel styles */
        .carousel {
            flex: 1;
            position: relative;
            height: auto;
            margin-right: 20px;
            margin-bottom: 100px;
        }

        .carousel img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            display: none;
        }

        .carousel img.active {
            display: block;
        }

        .carousel-controls {
            position: absolute;
            top: 50%;
            width: 100%;
            display: flex;
            justify-content: space-between;
            transform: translateY(-50%);
        }

        .carousel-controls button {
            background-color: rgba(0, 0, 0, 0.5);
            border: none;
            color: white;
            padding: 10px;
            cursor: pointer;
        }

        /* Product details styles */
        .product-details {
            flex: 1;
            display: flex;
            flex-direction: column;
            margin-top: 50px; /* Adjust this margin if needed */
        }

        .product-details h1, .product-details h2, .product-details h3 {
            margin: 0; /* Removes the margin */
            padding: 0; /* Ensures no padding */
        }

        .product-details h3 {
            margin-top: 20px;
            margin-bottom: 0px;
            padding: 0; /* Ensures no padding */
        }

        .about-title {
            margin-top: 20px;
            margin-bottom: 0;
            font-size: 1.5em;
        }

        .description {
            margin-top: 10px;
            line-height: 1.6; /* Increase line spacing */
        }

        .price {
            font-size: 24px; /* Adjust the font size as needed */
            color: #333; /* Adjust the color as needed */
            margin-top: 20px; /* Add some space above the price */
            margin-bottom: 20px; /* Add some space below the price */
        }

        .add-to-cart {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 15px;
            font-size: 16px;
            cursor: pointer;
            margin-top: 20px; /* Adjust the margin as needed */
            width: fit-content;
        }

        .product-type {
            margin-top: 10px; /* Add space between product name and product type */
        }

        .product-color {
            margin-top: 10px; /* Add space between product type and product color */
        }

        /* Responsive design for smaller screens */
        @media (max-width: 600px) {
            .carousel {
                flex: none;
                width: 100%;
                margin-right: 0;
                margin-bottom: 20px;
            }

            .product-details {
                margin-top: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="product-layout">
            <div class="carousel">
                <img src="https://live.staticflickr.com/65535/53774947256_9d72688b79_z.jpg" alt="Image 1" class="active">
                <img src="https://live.staticflickr.com/65535/53775364755_825ff08d74_z.jpg" alt="Image 2">
                <div class="carousel-controls">
                    <button id="prev">Previous</button>
                    <button id="next">Next</button>
                </div>
            </div>
            <div class="product-details">
                <h1>Paracord Wristband</h1>
                <h2 class="product-type">Slim</h2>
                <h3 class="product-color">Black & Green</h3>
                <h3 class="about-title">About this product</h3>
                <p class="description">
                    This is a detailed description of the product. It highlights the key features, specifications, and benefits
                    of the product. This product is designed to meet all your needs and exceed your expectations with its
                    high-quality materials and innovative design.
                </p>
                <p class="price">$99.99</p>
                <button class="add-to-cart">Add to Cart</button>
            </div>
        </div>
    </div>

    <script>
        let slideIndex = 0;
        const slides = document.querySelectorAll(".carousel img");
        const prevButton = document.getElementById("prev");
        const nextButton = document.getElementById("next");
        let autoSlideTimeout;

        function showSlide(index) {
            slides.forEach((slide, i) => {
                slide.classList.remove("active");
                if (i === index) {
                    slide.classList.add("active");
                }
            });
        }

        function changeSlide(n) {
            slideIndex += n;
            if (slideIndex >= slides.length) {
                slideIndex = 0;
            } else if (slideIndex < 0) {
                slideIndex = slides.length - 1;
            }
            showSlide(slideIndex);
        }

        function autoSlideShow() {
            if (window.innerWidth <= 768) {
                slideIndex++;
                if (slideIndex >= slides.length) {
                    slideIndex = 
                    0;
                }
                showSlide(slideIndex);
                autoSlideTimeout = setTimeout(autoSlideShow, 3000); // Change image every 3 seconds
            }
        }

        prevButton.addEventListener("click", () => changeSlide(-1));
        nextButton.addEventListener("click", () => changeSlide(1));

        // Initialize the slideshow
        showSlide(slideIndex);

        // Start automatic slideshow if on mobile
        if (window.innerWidth <= 768) {
            autoSlideShow();
        }

        // Adjust slideshow behavior on window resize
        window.onresize = function() {
            clearTimeout(autoSlideTimeout); // Clear the previous timeout to prevent multiple intervals
            if (window.innerWidth <= 768) {
                autoSlideShow();
            }
        };
    </script>
</body>
</html>
