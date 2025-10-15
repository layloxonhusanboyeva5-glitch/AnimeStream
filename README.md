<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AniGalaxy - Your Anime Universe</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #6a11cb;
            --secondary: #2575fc;
            --dark: #1a1a2e;
            --darker: #16213e;
            --light: #f8f9fa;
            --gray: #6c757d;
            --success: #28a745;
            --warning: #ffc107;
            --danger: #dc3545;
        }

        body {
            background-color: var(--darker);
            color: var(--light);
            line-height: 1.6;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* Header Styles */
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            padding: 15px 0;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo i {
            font-size: 2rem;
            color: white;
        }

        .logo h1 {
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(to right, #fff, #e0e0ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .search-bar {
            display: flex;
            width: 50%;
        }

        .search-bar input {
            width: 100%;
            padding: 12px 20px;
            border: none;
            border-radius: 30px 0 0 30px;
            background: rgba(255, 255, 255, 0.9);
            font-size: 1rem;
            outline: none;
        }

        .search-bar button {
            padding: 0 20px;
            border: none;
            border-radius: 0 30px 30px 0;
            background: var(--dark);
            color: white;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .search-bar button:hover {
            background: var(--primary);
        }

        .user-actions {
            display: flex;
            gap: 15px;
        }

        .user-actions button {
            padding: 10px 20px;
            border: none;
            border-radius: 30px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .user-actions button:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), 
                        url('https://images.unsplash.com/photo-1531315630201-bb15abeb1653?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            padding: 80px 0;
            text-align: center;
            margin-bottom: 40px;
        }

        .hero h2 {
            font-size: 3rem;
            margin-bottom: 20px;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 30px;
            color: #e0e0ff;
        }

        .cta-button {
            display: inline-block;
            padding: 15px 30px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            text-decoration: none;
            border-radius: 30px;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(106, 17, 203, 0.4);
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(106, 17, 203, 0.6);
        }

        /* Categories Section */
        .categories {
            padding: 40px 0;
        }

        .section-title {
            font-size: 2rem;
            margin-bottom: 30px;
            text-align: center;
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            margin: 10px auto;
            border-radius: 2px;
        }

        .category-list {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 40px;
        }

        .category {
            padding: 12px 25px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .category:hover, .category.active {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            transform: translateY(-3px);
            box-shadow: 0 4px 10px rgba(106, 17, 203, 0.3);
        }

        /* Anime Grid */
        .anime-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 25px;
            margin-bottom: 50px;
        }

        .anime-card {
            background: var(--dark);
            border-radius: 10px;
            overflow: hidden;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .anime-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
        }

        .anime-img {
            width: 100%;
            height: 300px;
            object-fit: cover;
        }

        .anime-info {
            padding: 15px;
        }

        .anime-title {
            font-size: 1.2rem;
            margin-bottom: 10px;
            font-weight: 600;
        }

        .anime-meta {
            display: flex;
            justify-content: space-between;
            color: var(--gray);
            font-size: 0.9rem;
            margin-bottom: 10px;
        }

        .anime-desc {
            font-size: 0.9rem;
            color: #b0b0b0;
            margin-bottom: 15px;
            display: -webkit-box;
            -webkit-line-clamp: 3;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .watch-btn {
            display: block;
            width: 100%;
            padding: 10px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .watch-btn:hover {
            background: linear-gradient(135deg, var(--secondary), var(--primary));
        }

        /* Footer */
        footer {
            background: var(--dark);
            padding: 40px 0 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }

        .footer-column h3 {
            font-size: 1.3rem;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }

        .footer-column h3::after {
            content: '';
            position: absolute;
            left: 0;
            bottom: 0;
            width: 40px;
            height: 3px;
            background: linear-gradient(to right, var(--primary), var(--secondary));
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 10px;
        }

        .footer-links a {
            color: var(--gray);
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .footer-links a:hover {
            color: white;
            padding-left: 5px;
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            color: white;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            transform: translateY(-3px);
        }

        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--gray);
            font-size: 0.9rem;
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .search-bar {
                width: 40%;
            }
            
            .hero h2 {
                font-size: 2.5rem;
            }
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            .search-bar {
                width: 80%;
                order: 3;
            }
            
            .hero h2 {
                font-size: 2rem;
            }
            
            .anime-grid {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            }
        }

        @media (max-width: 576px) {
            .hero {
                padding: 60px 0;
            }
            
            .hero h2 {
                font-size: 1.8rem;
            }
            
            .category-list {
                gap: 10px;
            }
            
            .category {
                padding: 10px 20px;
                font-size: 0.9rem;
            }
            
            .anime-grid {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }
            
            .anime-img {
                height: 220px;
            }
        }
    </style>
</head>
<body>
        <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-rocket"></i>
                    <h1>AniGalaxy</h1>
                </div>
                <div class="search-bar">
                    <input type="text" placeholder="Search anime, e.g. 'vampire', 'slice of life'">
                    <button><i class="fas fa-search"></i></button>
                </div>
                <div class="user-actions">
                    <button id="signInBtn"><i class="fas fa-user"></i> Sign In</button>
                    <button id="favoritesBtn"><i class="fas fa-heart"></i> Favorites</button>
                </div>
            </div>
        </div>
    </header>

        <section class="hero">
        <div class="container">
            <h2>Explore the Anime Universe</h2>
            <p>Discover thousands of anime series and movies. From classic favorites to the latest releases, all in one place.</p>
            <a href="#" class="cta-button" id="startWatchingBtn">Start Watching Now</a>
        </div>
    </section>

        <section class="categories">
        <div class="container">
            <h2 class="section-title">Browse Categories</h2>
            <div class="category-list">
                <div class="category active">All</div>
                <div class="category">Action</div>
                <div class="category">Romance</div>
                <div class="category">Horror</div>
                <div class="category">Slice of Life</div>
                <div class="category">Fantasy</div>
                <div class="category">Adventure</div>
                <div class="category">Comedy</div>
                <div class="category">Drama</div>
                <div class="category">Sci-Fi</div>
            </div>

                        <div class="anime-grid">
                                <div class="anime-card">
                    <img src="https://images.unsplash.com/photo-1578662996442-48f60103fc96?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Anime 1" class="anime-img">
                    <div class="anime-info">
                        <h3 class="anime-title">Demon Slayer</h3>
                        <div class="anime-meta">
                            <span>TV Series</span>
                            <span>24 Episodes</span>
                        </div>
                        <p class="anime-desc">Tanjiro Kamado fights demons and seeks a cure for his sister who has been turned into a demon.</p>
                        <button class="watch-btn">Watch Now</button>
                    </div>
                </div>

                                <div class="anime-card">
                    <img src="https://images.unsplash.com/photo-1639322537228-f710d846310a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1336&q=80" alt="Anime 2" class="anime-img">
                    <div class="anime-info">
                        <h3 class="anime-title">Attack on Titan</h3>
                        <div class="anime-meta">
                            <span>TV Series</span>
                            <span>75 Episodes</span>
                        </div>
                        <p class="anime-desc">Humanity fights for survival against giant humanoid creatures known as Titans.</p>
                        <button class="watch-btn">Watch Now</button>
                    </div>
                </div>

                                <div class="anime-card">
                    <img src="https://images.unsplash.com/photo-1541562232579-512a21360020?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Anime 3" class="anime-img">
                    <div class="anime-info">
                        <h3 class="anime-title">My Hero Academia</h3>
                        <div class="anime-meta">
                            <span>TV Series</span>
                            <span>113 Episodes</span>
                        </div>
                        <p class="anime-desc">In a world of superpowers, a boy without powers strives to become a hero.</p>
                        <button class="watch-btn">Watch Now</button>
                    </div>
                </div>

                                <div class="anime-card">
                    <img src="https://images.unsplash.com/photo-1500462918059-b1a0cb512f1d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Anime 4" class="anime-img">
                    <div class="anime-info">
                        <h3 class="anime-title">One Piece</h3>
                        <div class="anime-meta">
                            <span>TV Series</span>
                            <span>1000+ Episodes</span>
                        </div>
                        <p class="anime-desc">Monkey D. Luffy and his crew search for the ultimate treasure to become the Pirate King.</p>
                        <button class="watch-btn">Watch Now</button>
                    </div>
                </div>

                                <div class="anime-card">
                    <img src="https://images.unsplash.com/photo-1578662996442-48f60103fc96?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1350&q=80" alt="Anime 5" class="anime-img">
                    <div class="anime-info">
                        <h3 class="anime-title">Naruto Shippuden</h3>
                        <div class="anime-meta">
                            <span>TV Series</span>
                            <span>500 Episodes</span>
                        </div>
                        <p class="anime-desc">Naruto Uzumaki continues his journey to become Hokage and protect the village.</p>
                        <button class="watch-btn">Watch Now</button>
                    </div>
                </div>

                                <div class="anime-card">
                    <img src="https://images.unsplash.com/photo-1639322537228-f710d846310a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1336&q=80" alt="Anime 6" class="anime-img">
                    <div class="anime-info">
                        <h3 class="anime-title">Death Note</h3>
                        <div class="anime-meta">
                            <span>TV Series</span>
                            <span>37 Episodes</span>
                        </div>
                        <p class="anime-desc">A high school student discovers a notebook that can kill anyone whose name is written in it.</p>
                        <button class="watch-btn">Watch Now</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

        <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>AniGalaxy</h3>
                    <p>Your ultimate destination for anime streaming. Explore thousands of series and movies in high quality.</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-facebook-f"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-discord"></i></a>
                    </div>
                </div>
                <div class="footer-column">
                    <h3>Browse</h3>
                    <ul class="footer-links">
                        <li><a href="#">Popular Anime</a></li>
                        <li><a href="#">New Releases</a></li>
                        <li><a href="#">Top Rated</a></li>
                        <li><a href="#">Upcoming</a></li>
                        <li><a href="#">Movies</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Support</h3>
                    <ul class="footer-links">
                        <li><a href="#">Help Center</a></li>
                        <li><a href="#">Contact Us</a></li>
                        <li><a href="#">FAQ</a></li>
                        <li><a href="#">Server Status</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Legal</h3>
                    <ul class="footer-links">
                        <li><a href="#">Terms of Service</a></li>
                        <li><a href="#">Privacy Policy</a></li>
                        <li><a href="#">Cookie Policy</a></li>
                        <li><a href="#">DMCA</a></li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2023 AniGalaxy. This is a prototype for educational purposes only.</p>
            </div>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Elementlarga oson murojaat qilish uchun ID larni ishlatamiz.
            const searchInput = document.querySelector('.search-bar input');
            const searchButton = document.querySelector('.search-bar button');
            const signInBtn = document.getElementById('signInBtn');
            const favoritesBtn = document.getElementById('favoritesBtn');
            const startWatchingBtn = document.getElementById('startWatchingBtn');
            const categories = document.querySelectorAll('.category');
            const watchButtons = document.querySelectorAll('.watch-btn');

            // --- 1. Qidiruv (Search) Funksiyasi ---
            const handleSearch = () => {
                const searchText = searchInput.value.trim();
                if (searchText !== '') {
                    alert(`Siz qidiruvni boshladingiz: "${searchText}" 🔎. Natijalar yuklanmoqda...`);
                    // Kelajakda: Bu yerda animelarni filtrlash logikasi bo'ladi.
                } else {
                    alert("Iltimos, qidiruv so'zini kiriting!");
                }
            };

            searchButton.addEventListener('click', handleSearch);
            searchInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    handleSearch();
                }
            });

            // --- 2. Yuqori o'ng burchakdagi tugmalar ---
            signInBtn.addEventListener('click', function() {
                alert("Sign In tugmasi bosildi. Kirish sahifasiga yo'naltirilmoqda.");
                // Kelajakda: window.location.href = 'login.html';
            });

            favoritesBtn.addEventListener('click', function() {
                alert("Sevimlilar ro'yxati 💖. Kirish qilingan bo'lsa, ro'yxat ko'rsatiladi.");
            });

            // --- 3. Hero bo'limi tugmasi ---
            startWatchingBtn.addEventListener('click', function(e) {
                e.preventDefault(); // Sahifaning yuqoriga qaytishini oldini oladi
                // Animelar ro'yxati (kategoriyalar) bo'limiga o'tkazish
                document.querySelector('.categories').scrollIntoView({ behavior: 'smooth' });
            });

            // --- 4. Kategoriya tugmalari funksiyasi ---
            categories.forEach(category => {
                category.addEventListener('click', function() {
                    categories.forEach(c => c.classList.remove('active'));
                    this.classList.add('active');
                    
                    const categoryName = this.textContent.trim();
                    alert(`Siz "${categoryName}" kategoriyasini tanladingiz. Animelar ro'yxati filtrlanmoqda...`);
                    // Kelajakda: Bu yerda animelar ro'yxatini filtrlaydigan / qayta yuklaydigan kod bo'ladi.
                });
            });

            // --- 5. Har bir Anime Cardidagi Watch Now tugmasi ---
            watchButtons.forEach(button => {
                button.addEventListener('click', function() {
                    // Qaysi anime ekanligini topish
                    const animeTitle = this.closest('.anime-card').querySelector('.anime-title').textContent;
                    alert(`" ${animeTitle} " hozir tomosha qilinadi! Video o'ynatuvchisi ochilmoqda...`);
                    // Kelajakda: window.location.href = `watch.html?title=${animeTitle}`;
                });
            });
        });
    </script>
</body>
</html>
