---
layout: default
title: Photo Wall
nav_order: 6  # 设置导航顺序
---

# Photo Wall

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Photo Wall</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: #333;
        }
        
        header {
            background-color: #2c3e50;
            color: white;
            padding: 20px 0;
            text-align: center;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .filter-container {
            margin: 20px 0;
            text-align: center;
        }
        
        .filter-container select {
            padding: 8px 15px;
            border-radius: 20px;
            border: 1px solid #ddd;
            background-color: white;
            font-size: 16px;
            cursor: pointer;
        }
        
        .carousel {
            position: relative;
            height: 400px;
            overflow: hidden;
            margin-bottom: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        
        .carousel-inner {
            display: flex;
            transition: transform 0.5s ease;
            height: 100%;
        }
        
        .carousel-item {
            min-width: 100%;
            height: 100%;
        }
        
        .carousel-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .carousel-control {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background-color: rgba(0, 0, 0, 0.5);
            color: white;
            border: none;
            padding: 15px;
            cursor: pointer;
            font-size: 20px;
            z-index: 10;
            border-radius: 50%;
        }
        
        .carousel-control.prev {
            left: 10px;
        }
        
        .carousel-control.next {
            right: 10px;
        }
        
        .photo-wall {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .photo-item {
            position: relative;
            overflow: hidden;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
            cursor: pointer;
        }
        
        .photo-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .photo-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            display: block;
        }
        
        .photo-caption {
            padding: 10px;
            background-color: white;
            text-align: center;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            z-index: 100;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            max-width: 80%;
            max-height: 80%;
        }
        
        .modal-content img {
            max-width: 100%;
            max-height: 80vh;
            object-fit: contain;
        }
        
        .close-modal {
            position: absolute;
            top: 20px;
            right: 30px;
            color: white;
            font-size: 30px;
            cursor: pointer;
        }
        
        .modal-nav {
            position: absolute;
            top: 50%;
            width: 100%;
            display: flex;
            justify-content: space-between;
            padding: 0 20px;
        }
        
        .modal-nav button {
            background: none;
            border: none;
            color: white;
            font-size: 30px;
            cursor: pointer;
        }
        
        footer {
            background-color: #2c3e50;
            color: white;
            text-align: center;
            padding: 20px 0;
            margin-top: 40px;
        }
        
        @media (max-width: 768px) {
            .photo-wall {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            }
            
            .carousel {
                height: 300px;
            }
        }
        
        @media (max-width: 480px) {
            .photo-wall {
                grid-template-columns: 1fr;
            }
            
            .carousel {
                height: 250px;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Photo Wall</h1>
    </header>
    
    <div class="container">
        <div class="filter-container">
            <select id="category-filter">
                <option value="all">All Photos</option>
                <option value="research">Research</option>
                <option value="conference">Conferences</option>
                <option value="fieldwork">Fieldwork</option>
                <option value="team">Team Activities</option>
            </select>
        </div>
        
        <div class="carousel">
            <div class="carousel-inner" id="carousel-inner">
                <div class="carousel-item">
                    <img src="https://source.unsplash.com/random/1200x400/?laboratory" alt="Laboratory">
                </div>
                <div class="carousel-item">
                    <img src="https://source.unsplash.com/random/1200x400/?conference" alt="Conference">
                </div>
                <div class="carousel-item">
                    <img src="https://source.unsplash.com/random/1200x400/?team" alt="Team Activity">
                </div>
            </div>
            <button class="carousel-control prev" onclick="moveCarousel(-1)">❮</button>
            <button class="carousel-control next" onclick="moveCarousel(1)">❯</button>
        </div>
        
        <div class="photo-wall" id="photo-wall">
            <!-- Photos will be dynamically generated by JavaScript -->
        </div>
    </div>
    
    <div class="modal" id="photo-modal">
        <span class="close-modal" onclick="closeModal()">&times;</span>
        <div class="modal-content">
            <img id="modal-img" src="" alt="Enlarged Photo">
        </div>
        <div class="modal-nav">
            <button onclick="showPrevPhoto()">❮</button>
            <button onclick="showNextPhoto()">❯</button>
        </div>
    </div>
    
    <footer>
        <p>© 2023 Photo Wall | Design and Development</p>
    </footer>
    
    <script>
        // Photo data
        const photos = [
            {
                id: 1,
                src: "C:\Users\Leo\Documents\GitHub\Leo-1924.github.io\photo_wall\DSC06533.JPG",
                caption: "Group Photo",
                category: "team"
            },
            {
                id: 2,
                src: "C:\Users\Leo\Documents\GitHub\Leo-1924.github.io\photo_wall\DSC06548.JPG",
                caption: "Group Photo2",
                category: "team"
            },
 
        ];
        
        // Current slide index for carousel
        let currentSlide = 0;
        let slideInterval;
        
        // Current photo index for modal
        let currentPhotoIndex = 0;
        let currentPhotos = [];
        
        // Initialize the page
        document.addEventListener('DOMContentLoaded', function() {
            renderPhotoWall('all');
            setupCarousel();
        });
        
        // Render the photo wall
        function renderPhotoWall(category) {
            const photoWall = document.getElementById('photo-wall');
            photoWall.innerHTML = '';
            
            const filteredPhotos = category === 'all' 
                ? photos 
                : photos.filter(photo => photo.category === category);
            
            filteredPhotos.forEach(photo => {
                const photoItem = document.createElement('div');
                photoItem.className = 'photo-item';
                photoItem.innerHTML = `
                    <img src="${photo.src}" alt="${photo.caption}">
                    <div class="photo-caption">${photo.caption}</div>
                `;
                
                photoItem.addEventListener('click', () => {
                    openModal(photo, filteredPhotos.indexOf(photo), filteredPhotos);
                });
                
                photoWall.appendChild(photoItem);
            });
        }
        
        // Set up the carousel
        function setupCarousel() {
            const carouselInner = document.getElementById('carousel-inner');
            const carouselItems = carouselInner.querySelectorAll('.carousel-item');
            
            // Set up automatic carousel
            slideInterval = setInterval(() => {
                moveCarousel(1);
            }, 5000);
            
            // Pause carousel on hover
            carouselInner.addEventListener('mouseenter', () => {
                clearInterval(slideInterval);
            });
            
            // Resume carousel on leave
            carouselInner.addEventListener('mouseleave', () => {
                slideInterval = setInterval(() => {
                    moveCarousel(1);
                }, 5000);
            });
        }
        
        // Move the carousel
        function moveCarousel(direction) {
            const carouselInner = document.getElementById('carousel-inner');
            const carouselItems = carouselInner.querySelectorAll('.carousel-item');
            const itemCount = carouselItems.length;
            
            currentSlide = (currentSlide + direction + itemCount) % itemCount;
            carouselInner.style.transform = `translateX(-${currentSlide * 100}%)`;
        }
        
        // Filter photos
        document.getElementById('category-filter').addEventListener('change', function() {
            renderPhotoWall(this.value);
        });
        
        // Open the modal
        function openModal(photo, index, allPhotos) {
            const modal = document.getElementById('photo-modal');
            const modalImg = document.getElementById('modal-img');
            
            modal.style.display = 'flex';
            modalImg.src = photo.src;
            
            currentPhotoIndex = index;
            currentPhotos = allPhotos;
            
            // Prevent background scrolling
            document.body.style.overflow = 'hidden';
        }
        
        // Close the modal
        function closeModal() {
            const modal = document.getElementById('photo-modal');
            modal.style.display = 'none';
            
            // Restore background scrolling
            document.body.style.overflow = 'auto';
        }
        
        // Show the previous photo
        function showPrevPhoto() {
            currentPhotoIndex = (currentPhotoIndex - 1 + currentPhotos.length) % currentPhotos.length;
            updateModalImage();
        }
        
        // Show the next photo
        function showNextPhoto() {
            currentPhotoIndex = (currentPhotoIndex + 1) % currentPhotos.length;
            updateModalImage();
        }
        
        // Update the image in the modal
        function updateModalImage() {
            const modalImg = document.getElementById('modal-img');
            modalImg.src = currentPhotos[currentPhotoIndex].src;
        }
        
        // Close modal when clicking outside
        document.getElementById('photo-modal').addEventListener('click', function(e) {
            if (e.target === this) {
                closeModal();
            }
        });
        
        // Keyboard controls for modal
        document.addEventListener('keydown', function(e) {
            if (document.getElementById('photo-modal').style.display === 'flex') {
                if (e.key === 'Escape') {
                    closeModal();
                } else if (e.key === 'ArrowLeft') {
                    showPrevPhoto();
                } else if (e.key === 'ArrowRight') {
                    showNextPhoto();
                }
            }
        });
    </script>
</body>
</html>