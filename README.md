# Genesis-
<html>
<head>
    <title>Premium NFT Gallery</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.0/gsap.min.js"></script>
    <style>
        :root {
            --primary-color: #A67C00;
            --primary-hover: #8B6914;
            --accent-gold: #FFD700;
            --background-dark: #0A0B0E;
            --card-bg: #141519;
            --text-light: #FFFFFF;
            --text-gold: #D4AF37;
            --premium-gradient: linear-gradient(135deg, #B8860B, #FFD700);
            --card-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
            --glass-effect: rgba(255, 255, 255, 0.05);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--background-dark);
            color: var(--text-light);
            background-image: 
                radial-gradient(circle at 20% 20%, rgba(255, 215, 0, 0.05) 0%, transparent 40%),
                radial-gradient(circle at 80% 80%, rgba(255, 215, 0, 0.05) 0%, transparent 40%);
            overflow-x: hidden;
            padding: 80px 20px 20px;
        }

        .header {
            padding: 20px;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(20px);
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            z-index: 1000;
            border-bottom: 1px solid rgba(255, 215, 0, 0.1);
        }

        .header-content {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8em;
            font-weight: 800;
            background: var(--premium-gradient);
            -webkit-background-clip: text;
            color: transparent;
            letter-spacing: 1px;
        }

        .connect-wallet {
            padding: 10px 20px;
            background: var(--premium-gradient);
            border: none;
            border-radius: 25px;
            color: var(--background-dark);
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .connect-wallet:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255, 215, 0, 0.2);
        }

        .gallery-container-card {
            max-width: 1400px;
            margin: 0 auto;
            background: rgba(20, 21, 25, 0.7);
            border-radius: 30px;
            border: 1px solid rgba(255, 215, 0, 0.1);
            backdrop-filter: blur(20px);
            padding: 40px 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }

        .gallery-container-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 1px;
            background: linear-gradient(90deg, transparent, var(--accent-gold), transparent);
        }

        .gallery-title {
            text-align: center;
            margin-bottom: 30px;
            font-size: 1em;
            background: var(--premium-gradient);
            -webkit-background-clip: text;
            color: transparent;
            position: relative;
            display: inline-block;
            left: 50%;
            transform: translateX(-50%);
        }

        .gallery-container {
            height: 600px;
            position: relative;
            overflow: hidden;
        }

        .carousel-wrapper {
            display: flex;
            gap: 30px;
            position: absolute;
            transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            padding: 20px;
        }

        .artwork-card {
            min-width: 350px;
            height: 520px;
            background: var(--card-bg);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: var(--card-shadow);
            transition: all 0.4s ease;
            border: 1px solid rgba(255, 215, 0, 0.1);
            cursor: pointer;
            position: relative;
        }

        .artwork-card::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                45deg,
                transparent,
                rgba(255, 215, 0, 0.1),
                transparent
            );
            transform: rotate(45deg);
            transition: all 0.6s ease;
            opacity: 0;
        }

        .artwork-card:hover::after {
            opacity: 1;
        }

        .artwork-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 15px 40px rgba(255, 215, 0, 0.1);
        }

        .artwork-image {
            position: relative;
            width: 100%;
            height: 280px;
            overflow: hidden;
        }

        .artwork-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .artwork-card:hover .artwork-image img {
            transform: scale(1.05);
        }

        .premium-badge {
            position: absolute;
            top: 20px;
            right: 20px;
            background: var(--premium-gradient);
            padding: 8px 16px;
            border-radius: 25px;
            font-size: 0.9em;
            font-weight: bold;
            color: var(--background-dark);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }

        .price-tag {
            position: absolute;
            bottom: 20px;
            left: 20px;
            background: rgba(0, 0, 0, 0.8);
            padding: 10px 20px;
            border-radius: 15px;
            color: var(--text-gold);
            font-weight: bold;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 215, 0, 0.2);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .artwork-info {
            padding: 25px;
            background: linear-gradient(to bottom, rgba(20, 21, 25, 0.8), rgba(10, 11, 14, 0.9));
        }

        .artwork-title {
            font-size: 1.4em;
            color: var(--text-gold);
            margin-bottom: 10px;
            font-weight: bold;
        }

        .artwork-collection {
            color: rgba(255, 255, 255, 0.7);
            font-size: 0.9em;
            margin-bottom: 15px;
        }

        .artwork-creator {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 15px;
        }

        .creator-avatar {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background: var(--premium-gradient);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8em;
            color: var(--background-dark);
        }

        .action-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .action-btn {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 12px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .buy-btn {
            background: var(--premium-gradient);
            color: var(--background-dark);
        }

        .view-btn {
            background: var(--glass-effect);
            color: var(--text-light);
            border: 1px solid rgba(255, 215, 0, 0.2);
        }

        .action-btn:hover {
            transform: translateY(-2px);
        }

        .carousel-nav {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
            z-index: 100;
        }

        .nav-btn {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid var(--text-gold);
            color: var(--text-gold);
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .nav-btn:hover {
            background: var(--premium-gradient);
            color: var(--background-dark);
            transform: scale(1.1);
        }

        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(10px);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 2000;
        }

        .modal-content {
            background: var(--card-bg);
            width: 90%;
            max-width: 1000px;
            border-radius: 20px;
            padding: 30px;
            position: relative;
            border: 1px solid rgba(255, 215, 0, 0.2);
        }

        .modal-close {
            position: absolute;
            top: 20px;
            right: 20px;
            background: none;
            border: none;
            color: var(--text-light);
            font-size: 24px;
            cursor: pointer;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }

        .modal-close:hover {
            background: rgba(255, 255, 255, 0.1);
        }

        .modal-details {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        .modal-image {
            width: 100%;
            height: 400px;
            border-radius: 15px;
            overflow: hidden;
            position: relative;
        }

        .modal-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .modal-info {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-top: 20px;
        }

        .stat-item {
            background: rgba(255, 255, 255, 0.05);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .stat-item:hover {
            background: rgba(255, 215, 0, 0.1);
        }

        .stat-label {
            color: var(--text-gold);
            font-size: 0.9em;
            margin-bottom: 5px;
        }

        .stat-value {
            font-size: 1.2em;
            font-weight: bold;
        }

        @media (max-width: 1024px) {
            .gallery-container {
                height: 550px;
            }

            .artwork-card {
                min-width: 300px;
                height: 480px;
            }

            .artwork-image {
                height: 240px;
            }
        }

        @media (max-width: 768px) {
            .gallery-container {
                height: 500px;
            }

            .artwork-card {
                min-width: 260px;
                height: 440px;
            }

            .artwork-image {
                height: 200px;
            }

            .modal-details {
                grid-template-columns: 1fr;
            }

            .modal-image {
                height: 300px;
            }

            .gallery-title {
                font-size: 1.6em;
            }
        }

        @media (max-width: 480px) {
            .gallery-container {
                height: 460px;
            }

            .artwork-card {
                min-width: 220px;
                height: 400px;
            }

            .artwork-image {
                height: 180px;
            }

            .artwork-info {
                padding: 15px;
            }

            .artwork-title {
                font-size: 1.2em;
            }

            .action-buttons {
                flex-direction: column;
            }

            .nav-btn {
                width: 35px;
                height: 35px;
            }
        }
    </style>
</head>
<body>
    <header class="header">
        <div class="header-content">
            <div class="logo">GENESIS</div>
            <button class="connect-wallet">
                <i class="fas fa-wallet"></i>
                Connect
            </button>
        </div>
    </header>

    <div class="gallery-container-card">
        <h1 class="gallery-title"> NFT Collection</h1>
        <div class="gallery-container">
            <div class="carousel-wrapper">
                <!-- NFT Cards will be dynamically inserted here -->
            </div>
            <div class="carousel-nav">
                <button class="nav-btn prev-btn"><i class="fas fa-chevron-left"></i></button>
                <button class="nav-btn next-btn"><i class="fas fa-chevron-right"></i></button>
            </div>
        </div>
    </div>

    <div class="modal">
        <div class="modal-content">
            <button class="modal-close"><i class="fas fa-times"></i></button>
            <div class="modal-details">
                <!-- Modal content will be dynamically inserted here -->
            </div>
        </div>
    </div>

    <script>
        const nftData = [
            {
                id: 1,
                title: "Divine Harmony #001",
                collection: "Genesis Collection",
                price: "12.5 ETH",
                image: "https://i.ibb.co/yFNbRqF/Whats-App-Image-2024-10-20-at-09-16-07-510389dd.jpg",
                badge: "Genesis Edition",
                creator: "CryptoMaster",
                creatorInitial: "CM",
                views: "1.2K",
                likes: "856",
                created: "2024-03-15"
            },
            {
                id: 2,
                title: "Ethereal Dreams #002",
                collection: "Platinum Series",
                price: "8.8 ETH",
                image: "https://i.ibb.co/7vkRDZv/Whats-App-Image-2024-10-20-at-09-16-08-0798f91f.jpg",
                badge: "Platinum",
                creator: "ArtVision",
                creatorInitial: "AV",
                views: "987",
                likes: "654",
                created: "2024-03-16"
            },
            {
                id: 3,
                title: "Quantum Legacy #003",
                collection: "Elite Collection",
                price: "15.2 ETH",
                image: "https://i.ibb.co/k8zNj9j/a-captivating-and-dreamlike-scene-of-a-dali-esque-swof-qz-GQu-Ks-Sj-h-EVGflw-q-Em-M-hmr-Rcm-FUZb-GUc.jpg",
                badge: "Ultra Rare",
                creator: "QuantumArt",
                creatorInitial: "QA",
                views: "2.1K",
                likes: "1.5K",
                created: "2024-03-17"
            },
            {
                id: 4,
                title: "Celestial Vision #004",
                collection: "Masterpiece Series",
                price: "18.5 ETH",
                image: "https://i.ibb.co/k51wwwg/an-awe-inspiring-scene-of-mythical-beasts-roaming-E6-Ugt4-g-TAO4r-Pl-Gpra-e-Q-t0tr-Egk6-Sf2r8k-Tr2-I.jpg",
                badge: "Masterpiece",
                creator: "StardustStudio",
                creatorInitial: "SS",
                views: "1.8K",
                likes: "1.2K",
                created: "2024-03-18"
            },
            {
                id: 5,
                title: "Digital Royalty #005",
                collection: "Crown Collection",
                price: "21.0 ETH",
                image: "https://i.ibb.co/YBXK5Mg/a-striking-3d-illustration-of-a-t-shirt-hanging-on-h1-AIHpnz-TRK-8e-SADc-LFJw-l-Hs-Od-YYj-Sp-Wg6xv-U.jpg",
                badge: "Royal Edition",
                creator: "CrownMaster",
                creatorInitial: "CM",
                views: "2.5K",
                likes: "1.8K",
                created: "2024-03-19"
            }
        ];

        function createNFTCard(nft) {
            return `
                <div class="artwork-card" data-id="${nft.id}">
                    <div class="artwork-image">
                        <div class="premium-badge">${nft.badge}</div>
                        <div class="price-tag">
                            <i class="fab fa-ethereum"></i>
                            ${nft.price}
                        </div>
                        <img src="${nft.image}" alt="${nft.title}">
                    </div>
                    <div class="artwork-info">
                        <h3 class="artwork-title">${nft.title}</h3>
                        <p class="artwork-collection">${nft.collection}</p>
                        <div class="artwork-creator">
                            <div class="creator-avatar">${nft.creatorInitial}</div>
                            <span>By ${nft.creator}</span>
                        </div>
                        <div class="action-buttons">
                            <button class="action-btn buy-btn">
                                <i class="fas fa-shopping-cart"></i>
                                Purchase Now
                            </button>
                            <button class="action-btn view-btn">
                                <i class="fas fa-eye"></i>
                                View Details
                            </button>
                        </div>
                    </div>
                </div>
            `;
        }

        function createModalContent(nft) {
            return `
                <div class="modal-image">
                    <img src="${nft.image}" alt="${nft.title}">
                    <div class="premium-badge">${nft.badge}</div>
                </div>
                <div class="modal-info">
                    <h2 class="artwork-title">${nft.title}</h2>
                    <p class="artwork-collection">${nft.collection}</p>
                    <div class="artwork-creator">
                        <div class="creator-avatar">${nft.creatorInitial}</div>
                        <span>Created by ${nft.creator}</span>
                    </div>
                    <div class="stats-grid">
                        <div class="stat-item">
                            <div class="stat-label">Current Price</div>
                            <div class="stat-value">
                                <i class="fab fa-ethereum"></i> ${nft.price}
                            </div>
                        </div>
                        <div class="stat-item">
                            <div class="stat-label">Views</div>
                            <div class="stat-value">
                                <i class="fas fa-eye"></i> ${nft.views}
                            </div>
                        </div>
                        <div class="stat-item">
                            <div class="stat-label">Likes</div>
                            <div class="stat-value">
                                <i class="fas fa-heart"></i> ${nft.likes}
                            </div>
                        </div>
                        <div class="stat-item">
                            <div class="stat-label">Created</div>
                            <div class="stat-value">
                                <i class="fas fa-calendar"></i> ${new Date(nft.created).toLocaleDateString()}
                            </div>
                        </div>
                    </div>
                    <div class="action-buttons">
                        <button class="action-btn buy-btn">
                            <i class="fas fa-shopping-cart"></i>
                            Purchase Now
                        </button>
                        <button class="action-btn view-btn">
                            <i class="far fa-heart"></i>
                            Add to Favorites
                        </button>
                    </div>
                </div>
            `;
        }

        class NFTGallery {
            constructor() {
                this.currentIndex = 0;
                this.wrapper = document.querySelector('.carousel-wrapper');
                this.cards = [];
                this.modal = document.querySelector('.modal');
                this.isAnimating = false;
                this.touchStartX = 0;
                this.initializeGallery();
                this.setupEventListeners();
                this.updateResponsiveDisplay();
            }

            initializeGallery() {
                this.wrapper.innerHTML = nftData.map(nft => createNFTCard(nft)).join('');
                this.cards = document.querySelectorAll('.artwork-card');
                this.updateCarousel();
            }

            setupEventListeners() {
                document.querySelector('.prev-btn').addEventListener('click', () => this.navigate(-1));
                document.querySelector('.next-btn').addEventListener('click', () => this.navigate(1));

                this.cards.forEach(card => {
                    card.addEventListener('click', () => this.openModal(card.dataset.id));
                });

                document.querySelector('.modal-close').addEventListener('click', () => this.closeModal());

                document.addEventListener('keydown', (e) => {
                    if (e.key === 'ArrowLeft') this.navigate(-1);
                    if (e.key === 'ArrowRight') this.navigate(1);
                    if (e.key === 'Escape') this.closeModal();
                });

                this.wrapper.addEventListener('touchstart', (e) => {
                    this.touchStartX = e.changedTouches[0].screenX;
                });

                this.wrapper.addEventListener('touchend', (e) => {
                    const touchEndX = e.changedTouches[0].screenX;
                    const diff = this.touchStartX - touchEndX;
                    
                    if (Math.abs(diff) > 50) {
                        this.navigate(diff > 0 ? 1 : -1);
                    }
                });

                window.addEventListener('resize', () => {
                    this.updateResponsiveDisplay();
                });
            }

            updateResponsiveDisplay() {
                const viewportWidth = window.innerWidth;
                if (viewportWidth <= 480) {
                    this.cardsPerView = 1;
                } else if (viewportWidth <= 768) {
                    this.cardsPerView = 2;
                } else if (viewportWidth <= 1024) {
                    this.cardsPerView = 3;
                } else {
                    this.cardsPerView = 3;
                }
                this.updateCarousel();
            }

            navigate(direction) {
                if (this.isAnimating) return;
                
                const maxIndex = nftData.length - this.cardsPerView;
                const newIndex = this.currentIndex + direction;
                
                if (newIndex < 0 || newIndex > maxIndex) {
                    this.bounce(direction);
                    return;
                }

                this.currentIndex = newIndex;
                this.updateCarousel();
            }

            bounce(direction) {
                this.isAnimating = true;
                const currentX = -this.currentIndex * this.getCardWidth();
                
                gsap.to(this.wrapper, {
                    x: currentX + (direction * 30),
                    duration: 0.2,
                    ease: "power2.out",
                    onComplete: () => {
                        gsap.to(this.wrapper, {
                            x: currentX,
                            duration: 0.2,
                            ease: "power2.in",
                            onComplete: () => {
                                this.isAnimating = false;
                            }
                        });
                    }
                });
            }

            getCardWidth() {
                const card = this.cards[0];
                return card.offsetWidth + parseInt(window.getComputedStyle(card).marginRight);
            }

            updateCarousel() {
                const offset = -this.currentIndex * this.getCardWidth();
                gsap.to(this.wrapper, {
                    x: offset,
                    duration: 0.5,
                    ease: "power2.out"
                });
            }

            openModal(id) {
                const nft = nftData.find(item => item.id === parseInt(id));
                document.querySelector('.modal-details').innerHTML = createModalContent(nft);
                
                gsap.fromTo(this.modal, 
                    { 
                        opacity: 0,
                        scale: 0.9
                    }, 
                    { 
                        opacity: 1,
                        scale: 1,
                        duration: 0.3,
                        ease: "power2.out",
                        display: 'flex'
                    }
                );
            }

            closeModal() {
                gsap.to(this.modal, {
                    opacity: 0,
                    scale: 0.9,
                    duration: 0.3,
                    ease: "power2.in",
                    onComplete: () => {
                        this.modal.style.display = 'none';
                    }
                });
            }
        }

        // Initialize gallery when the page loads
        window.addEventListener('load', () => {
            new NFTGallery();
            
            // Add smooth scroll animation to connect wallet button
            document.querySelector('.connect-wallet').addEventListener('click', () => {
                gsap.to(this, {
                    duration: 0.5,
                    ease: "power2.out",
                    onStart: () => {
                        alert('Wallet connection feature would be implemented here');
                    }
                });
            });
        });
    </script>
</body>
