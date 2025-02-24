<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Krayn Movie Site</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #121212;
            color: white;
            text-align: center;
        }
        header {
            background-color: #1f1f1f;
            padding: 20px;
            font-size: 24px;
        }
        .search-container {
            margin: 20px;
        }
        .search-container input {
            padding: 10px;
            width: 300px;
            border-radius: 5px;
            border: none;
        }
        .movie-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            padding: 20px;
        }
        .movie {
            width: 200px;
            margin: 10px;
            background-color: #222;
            padding: 10px;
            border-radius: 10px;
            cursor: pointer;
        }
        .movie img {
            width: 100%;
            border-radius: 5px;
        }
        .movie h3 {
            margin: 10px 0;
        }
        .movie p {
            font-size: 14px;
            color: #ccc;
        }
    </style>
</head>
<body>
    <header>Krayn Movies</header>
    <div class="search-container">
        <input type="text" id="searchInput" placeholder="Search for movies..." oninput="filterMovies()">
    </div>
    <div class="movie-container" id="movieContainer">
        <!-- Movies will be dynamically loaded here -->
    </div>

    <script>
        // Mock data for movies (you can replace this with data from a backend API)
        const movies = [
            {
                title: "Movie Title 1",
                description: "A great action movie.",
                image: "https://via.placeholder.com/200",
                genre: "Action"
            },
            {
                title: "Movie Title 2",
                description: "A thrilling adventure movie.",
                image: "https://via.placeholder.com/200",
                genre: "Adventure"
            },
            {
                title: "Movie Title 3",
                description: "A romantic comedy movie.",
                image: "https://via.placeholder.com/200",
                genre: "Comedy"
            },
            {
                title: "Movie Title 4",
                description: "A scary horror movie.",
                image: "https://via.placeholder.com/200",
                genre: "Horror"
            }
        ];

        // Function to display movies
        function displayMovies(filteredMovies) {
            const movieContainer = document.getElementById("movieContainer");
            movieContainer.innerHTML = ""; // Clear previous results

            filteredMovies.forEach(movie => {
                const movieElement = document.createElement("div");
                movieElement.classList.add("movie");
                movieElement.innerHTML = `
                    <img src="${movie.image}" alt="${movie.title}">
                    <h3>${movie.title}</h3>
                    <p>${movie.description}</p>
                    <p><strong>Genre:</strong> ${movie.genre}</p>
                `;
                movieContainer.appendChild(movieElement);
            });
        }

        // Function to filter movies based on search input
        function filterMovies() {
            const searchInput = document.getElementById("searchInput").value.toLowerCase();
            const filteredMovies = movies.filter(movie =>
                movie.title.toLowerCase().includes(searchInput) ||
                movie.genre.toLowerCase().includes(searchInput)
            );
            displayMovies(filteredMovies);
        }

        // Initial display of all movies
        displayMovies(movies);
    </script>
</body>
</html>