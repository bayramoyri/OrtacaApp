// Harita ve mekan verileri
let map;
let markers = {};
let places = [];
let currentRatingPlaceId = null;
let currentUserRating = 0;
let currentFilter = 'all';

// Kategori ikonları ve renkleri
const categoryConfig = {
    restaurant: { icon: '🍽️', color: '#FF6B6B', name: 'Restoran' },
    cafe: { icon: '☕', color: '#4ECDC4', name: 'Kahve Dükkanı' },
    hotel: { icon: '🏨', color: '#45B7D1', name: 'Otel' },
    gas: { icon: '⛽', color: '#FFA07A', name: 'Benzin İstasyonu' },
    jewelry: { icon: '💍', color: '#DDA0DD', name: 'Kuyumcu' },
    tourism: { icon: '📷', color: '#FFD700', name: 'Turistik Yer' }
};

// Ortaca koordinatları
const ORTACA_CENTER = [37.2500, 28.4500];
const ZOOM_LEVEL = 13;

// Sayfa yüklendiğinde
document.addEventListener('DOMContentLoaded', function() {
    initializeMap();
    loadPlaces();
    setupEventListeners();
    loadUserProfile();
});

// Haritayı başlat
function initializeMap() {
    map = L.map('map').setView(ORTACA_CENTER, ZOOM_LEVEL);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap contributors',
        maxZoom: 19
    }).addTo(map);

    // Harita tıklama
    map.on('click', closeDetailsPanel);
}

// Event Listener'ları ayarla
function setupEventListeners() {
    document.getElementById('addPlaceForm').addEventListener('submit', addNewPlace);
    document.getElementById('ratingForm').addEventListener('submit', submitRating);
}

// Örnek mekanları yükle
function loadPlaces() {
    places = [
        {
            id: 1,
            name: 'Ortaca Kebab Evi',
            category: 'restaurant',
            lat: 37.2510,
            lng: 28.4510,
            address: 'Cumhuriyet Caddesi No:45',
            phone: '0252 123 4567',
            website: 'www.ortacakebab.com',
            description: 'Geleneksel Türk mutfağı',
            rating: 4.5,
            reviews: [
                { author: 'Ahmet K.', rating: 5, comment: 'Çok lezzetli, hizmet harika!' },
                { author: 'Fatma T.', rating: 4, comment: 'Fiyatlar biraz yüksek ama kaliteli.' }
            ],
            featured: true
        },
        {
            id: 2,
            name: 'Kaya Kahve',
            category: 'cafe',
            lat: 37.2520,
            lng: 28.4520,
            address: 'Cumhuriyet Caddesi No:78',
            phone: '0252 234 5678',
            website: '',
            description: 'Rahat ortam, iyi kahve',
            rating: 4,
            reviews: [
                { author: 'Mehmet Y.', rating: 4, comment: 'Kahvesi iyidir, mekan temiz.' }
            ],
            featured: true
        },
        {
            id: 3,
            name: 'Grand Hotel Ortaca',
            category: 'hotel',
            lat: 37.2490,
            lng: 28.4490,
            address: 'Marmaris Yolu No:120',
            phone: '0252 345 6789',
            website: 'www.grandhotelortaca.com',
            description: '5 yıldızlı otel, modern tesisler',
            rating: 4.7,
            reviews: [
                { author: 'John D.', rating: 5, comment: 'Amazing hotel, great service!' }
            ],
            featured: true
        },
        {
            id: 4,
            name: 'BP Benzin İstasyonu',
            category: 'gas',
            lat: 37.2530,
            lng: 28.4530,
            address: 'Marmaris Yolu',
            phone: '0252 456 7890',
            website: '',
            description: '24 saat açık, tüm servisler mevcut',
            rating: 3.5,
            reviews: [],
            featured: false
        },
        {
            id: 5,
            name: 'Ege Kuyumculuk',
            category: 'jewelry',
            lat: 37.2500,
            lng: 28.4540,
            address: 'Liman Caddesi No:12',
            phone: '0252 567 8901',
            website: '',
            description: 'Altın, gümüş ve taş satışı',
            rating: 4.2,
            reviews: [],
            featured: false
        },
        {
            id: 6,
            name: 'Ortaca Muğla Kalesi',
            category: 'tourism',
            lat: 37.2470,
            lng: 28.4470,
            address: 'Eski Şehir Mahallesi',
            phone: '',
            website: '',
            description: 'Tarihi kale, harika manzara',
            rating: 4.8,
            reviews: [
                { author: 'Turist Ali', rating: 5, comment: 'Muğla\'nın en güzel yeri!' }
            ],
            featured: true
        }
    ];

    displayPlaces();
}

// Mekanları harita ve sidebar'da göster
function displayPlaces() {
    // Mevcut markerları temizle
    Object.values(markers).forEach(marker => map.removeLayer(marker));
    markers = {};

    // Öne çıkan mekanları sidebar'da göster
    displayFeaturedPlaces();

    // Filtrele ve göster
    const filteredPlaces = currentFilter === 'all' 
        ? places 
        : places.filter(p => p.category === currentFilter);

    filteredPlaces.forEach(place => {
        addPlaceMarker(place);
    });
}

// Öne çıkan mekanları göster
function displayFeaturedPlaces() {
    const featured = places.filter(p => p.featured);
    const container = document.getElementById('featuredPlaces');
    container.innerHTML = '';

    featured.forEach(place => {
        const div = document.createElement('div');
        div.className = 'featured-place';
        div.innerHTML = `
            <div class="featured-place-name">${place.name}</div>
            <div class="featured-place-rating">
                ${'⭐'.repeat(Math.floor(place.rating))} (${place.rating}/5)
            </div>
        `;
        div.onclick = () => showPlaceDetails(place.id);
        container.appendChild(div);
    });
}

// Markerı haritaya ekle
function addPlaceMarker(place) {
    const config = categoryConfig[place.category];
    
    const customIcon = L.divIcon({
        html: `<div style="background: ${config.color}; color: white; border-radius: 50%; width: 40px; height: 40px; display: flex; align-items: center; justify-content: center; font-size: 20px; border: 3px solid white; box-shadow: 0 2px 8px rgba(0,0,0,0.3);">${config.icon}</div>`,
        iconSize: [40, 40],
        iconAnchor: [20, 20],
        popupAnchor: [0, -20]
    });

    const marker = L.marker([place.lat, place.lng], { icon: customIcon })
        .addTo(map)
        .bindPopup(`
            <strong>${place.name}</strong><br>
            ${config.name}<br>
            ⭐ ${place.rating}/5
        `)
        .on('click', () => showPlaceDetails(place.id));

    markers[place.id] = marker;
}

// Mekan detaylarını göster
function showPlaceDetails(placeId) {
    const place = places.find(p => p.id === placeId);
    if (!place) return;

    const config = categoryConfig[place.category];
    const panel = document.getElementById('detailsPanel');
    const container = document.getElementById('placeDetails');

    let reviewsHTML = '';
    if (place.reviews && place.reviews.length > 0) {
        reviewsHTML = place.reviews.map(review => `
            <div class="review-item">
                <div class="review-rating">${'⭐'.repeat(review.rating)}</div>
                <div class="review-text">${review.comment}</div>
                <div class="review-author">- ${review.author}</div>
            </div>
        `).join('');
    } else {
        reviewsHTML = '<p style="color: #999; font-size: 12px;">Henüz yorum yok</p>';
    }

    container.innerHTML = `
        <div class="place-header">
            <div class="place-name">${place.name}</div>
            <span class="place-category" style="background: ${config.color}20; color: ${config.color};">${config.name}</span>
            <div class="place-rating">
                ${'⭐'.repeat(Math.floor(place.rating))} ${place.rating}/5
            </div>
            <div class="place-info">
                <i class="fas fa-map-marker-alt"></i>
                <span>${place.address}</span>
            </div>
            ${place.phone ? `
                <div class="place-info">
                    <i class="fas fa-phone"></i>
                    <span><a href="tel:${place.phone}">${place.phone}</a></span>
                </div>
            ` : ''}
            ${place.website ? `
                <div class="place-info">
                    <i class="fas fa-globe"></i>
                    <span><a href="https://${place.website}" target="_blank">${place.website}</a></span>
                </div>
            ` : ''}
        </div>

        <p>${place.description}</p>

        <button class="rating-btn" onclick="openRatingModal(${place.id})">
            <i class="fas fa-star"></i> Değerlendirme Yap
        </button>

        <div class="reviews-section">
            <h4>Yorumlar (${place.reviews ? place.reviews.length : 0})</h4>
            ${reviewsHTML}
        </div>
    `;

    panel.classList.remove('hidden');
    map.flyTo([place.lat, place.lng], 16);
}

// Detay panelini kapat
function closeDetailsPanel() {
    document.getElementById('detailsPanel').classList.add('hidden');
}

// Mekan ekle modal
function openAddPlaceModal() {
    document.getElementById('addPlaceModal').classList.add('show');
}

function closeAddPlaceModal() {
    document.getElementById('addPlaceModal').classList.remove('show');
    document.getElementById('addPlaceForm').reset();
}

// Yeni mekan ekle
function addNewPlace(e) {
    e.preventDefault();

    const newPlace = {
        id: places.length + 1,
        name: document.getElementById('placeName').value,
        category: document.getElementById('placeCategory').value,
        address: document.getElementById('placeAddress').value,
        phone: document.getElementById('placePhone').value,
        website: document.getElementById('placeWebsite').value,
        description: document.getElementById('placeDescription').value,
        lat: ORTACA_CENTER[0] + (Math.random() - 0.5) * 0.1,
        lng: ORTACA_CENTER[1] + (Math.random() - 0.5) * 0.1,
        rating: 0,
        reviews: [],
        featured: false
    };

    places.push(newPlace);
    displayPlaces();
    closeAddPlaceModal();
    alert('Mekan başarıyla eklendi!');
}

// Değerlendirme modal
function openRatingModal(placeId) {
    currentRatingPlaceId = placeId;
    currentUserRating = 0;
    document.getElementById('ratingModal').classList.add('show');
    updateStarDisplay();
}

function closeRatingModal() {
    document.getElementById('ratingModal').classList.remove('show');
}

function setRating(rating) {
    currentUserRating = rating;
    updateStarDisplay();
}

function updateStarDisplay() {
    const stars = document.querySelectorAll('.stars .star');
    const ratingText = document.getElementById('ratingText');
    
    stars.forEach((star, index) => {
        if (index < currentUserRating) {
            star.classList.add('active');
        } else {
            star.classList.remove('active');
        }
    });

    const ratings = ['', '1 Yıldız', '2 Yıldız', '3 Yıldız', '4 Yıldız', '5 Yıldız'];
    ratingText.textContent = ratings[currentUserRating] || 'Derecelendirme seçin';
}

// Değerlendirme gönder
function submitRating(e) {
    e.preventDefault();

    if (currentUserRating === 0) {
        alert('Lütfen yıldız seçin!');
        return;
    }

    const place = places.find(p => p.id === currentRatingPlaceId);
    const comment = document.getElementById('reviewComment').value;
    const username = localStorage.getItem('username') || 'Anonim';

    const review = {
        author: username,
        rating: currentUserRating,
        comment: comment || 'Yorum yapılmadı'
    };

    place.reviews.push(review);

    // Ortalama rating hesapla
    const totalRating = place.reviews.reduce((sum, r) => sum + r.rating, 0);
    place.rating = totalRating / place.reviews.length;

    closeRatingModal();
    showPlaceDetails(currentRatingPlaceId);
    alert('Değerlendirmeniz kaydedildi!');
}

// Kategori filtresi
function filterByCategory(category) {
    currentFilter = category;
    
    document.querySelectorAll('.category-btn').forEach(btn => {
        btn.classList.remove('active');
    });
    event.target.closest('.category-btn').classList.add('active');

    displayPlaces();
}

// Mekan ara
function searchPlace() {
    const searchTerm = document.getElementById('searchInput').value.toLowerCase();
    
    if (!searchTerm) {
        displayPlaces();
        return;
    }

    const results = places.filter(p => 
        p.name.toLowerCase().includes(searchTerm) ||
        p.address.toLowerCase().includes(searchTerm) ||
        p.description.toLowerCase().includes(searchTerm)
    );

    // Markerları temizle
    Object.values(markers).forEach(marker => map.removeLayer(marker));
    markers = {};

    // Sonuçları göster
    results.forEach(place => {
        addPlaceMarker(place);
    });

    if (results.length > 0) {
        showPlaceDetails(results[0].id);
    }
}

// Profil yönetimi
function toggleProfile() {
    const modal = document.getElementById('profileModal');
    if (modal.classList.contains('show')) {
        closeProfile();
    } else {
        openProfile();
    }
}

function openProfile() {
    const username = localStorage.getItem('username') || '';
    const modal = document.getElementById('profileModal');
    const content = document.getElementById('profileContent');

    if (username) {
        content.innerHTML = `
            <div class="profile-info">
                <p><strong>Kullanıcı Adı:</strong> ${username}</p>
                <p><strong>Üyelik Tarihi:</strong> ${new Date().toLocaleDateString('tr-TR')}</p>
            </div>
            <button class="rating-btn" onclick="logout()">Çıkış Yap</button>
        `;
    } else {
        const newUsername = prompt('Kullanıcı adınızı girin:');
        if (newUsername) {
            localStorage.setItem('username', newUsername);
            openProfile();
        }
        return;
    }

    modal.classList.add('show');
}

function closeProfile() {
    document.getElementById('profileModal').classList.remove('show');
}

function logout() {
    localStorage.removeItem('username');
    closeProfile();
    alert('Çıkış yaptınız!');
}

function loadUserProfile() {
    if (!localStorage.getItem('username')) {
        const newUsername = prompt('Hoşgeldiniz! Kullanıcı adınızı girin:');
        if (newUsername) {
            localStorage.setItem('username', newUsername);
        }
    }
}
