import os
import zipfile
import urllib.request

# --- 1. Folder Setup ---
folder_name = "dibyans_dibya_travels"
images_folder = f"{folder_name}/images"
os.makedirs(images_folder, exist_ok=True)

# --- 2. Download Images ---
images = {
    "hero.jpg": "https://images.unsplash.com/photo-1501594907352-04cda38ebc29?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80",
    "everest.jpg": "https://upload.wikimedia.org/wikipedia/commons/9/9c/Mount_Everest_as_seen_from_Drukair2_PLW_edit.jpg",
    "pokhara.jpg": "https://upload.wikimedia.org/wikipedia/commons/2/28/Phewa_Lake_Pokhara_Nepal.jpg",
    "kathmandu.jpg": "https://upload.wikimedia.org/wikipedia/commons/f/fc/Kathmandu_Valley_from_Swayambhunath.jpg"
}

for fname, url in images.items():
    print(f"Downloading {fname} ...")
    urllib.request.urlretrieve(url, os.path.join(images_folder, fname))

# --- 3. index.html ---
index_html = f"""<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dibyans & Dibya Travels | Explore Nepal</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
<header>
<h1 class="logo">Dibyans & Dibya Travels</h1>
<nav>
<ul>
<li><a href="#home">Home</a></li>
<li><a href="#destinations">Destinations</a></li>
<li><a href="#tours">Tours</a></li>
<li><a href="#about">About Us</a></li>
<li><a href="#contact">Contact</a></li>
</ul>
</nav>
</header>

<section id="home" class="hero" style="background:url('images/hero.jpg') center/cover no-repeat;">
<div class="hero-text">
<h2>Journey Beyond the Clouds, Discover Nepal</h2>
<p>From the peaks to the plains — adventure, culture, and serenity await.</p>
<a href="#tours" class="btn">Plan Your Journey</a>
</div>
</section>

<section id="destinations" class="destinations">
<h2>Top Destinations</h2>
<div class="destination-grid">
<div class="card">
<img src="images/everest.jpg" alt="Everest Base Camp">
<h3>Everest Base Camp</h3>
<p>Experience the ultimate trekking adventure to the world’s tallest peak.</p>
</div>
<div class="card">
<img src="images/pokhara.jpg" alt="Pokhara">
<h3>Pokhara</h3>
<p>Relax by serene lakes and witness breathtaking Himalayan sunrises.</p>
</div>
<div class="card">
<img src="images/kathmandu.jpg" alt="Kathmandu Valley">
<h3>Kathmandu Valley</h3>
<p>Explore the vibrant heart of Nepal — temples, culture, and history.</p>
</div>
</div>
</section>

<section id="tours" class="tours">
<h2>Featured Tours</h2>
<div class="tour-grid">
<div class="card">
<h3>Annapurna Circuit Trek</h3>
<p>10 days | Moderate | $850</p>
<a href="#" class="btn">Book Now</a>
</div>
<div class="card">
<h3>Kathmandu Heritage Tour</h3>
<p>3 days | Easy | $250</p>
<a href="#" class="btn">Book Now</a>
</div>
<div class="card">
<h3>Chitwan Jungle Safari</h3>
<p>5 days | Relaxed | $400</p>
<a href="#" class="btn">Book Now</a>
</div>
</div>
</section>

<section id="about" class="about">
<h2>About Us</h2>
<p>Founded by Dibyans and Dibya, two passionate explorers from Nepal, we bring authentic experiences to travelers seeking adventure, serenity, and culture. Whether you’re trekking the Himalayas or meditating by a lake, we make every journey unforgettable.</p>
</section>

<section id="contact" class="contact">
<h2>Contact Us</h2>
<form>
<input type="text" placeholder="Your Name" required>
<input type="email" placeholder="Your Email" required>
<textarea placeholder="Your Message" rows="5" required></textarea>
<button type="submit" class="btn">Send Message</button>
</form>
<div class="info">
<p><strong>Address:</strong> Thamel, Kathmandu, Nepal</p>
<p><strong>Phone:</strong> +977 9860821344</p>
<p><strong>Email:</strong> info@dibyanstravels.com</p>
</div>
</section>

<footer>
<p>© 2025 Dibyans & Dibya Travels | All Rights Reserved</p>
</footer>
</body>
</html>
"""

with open(f"{folder_name}/index.html", "w", encoding="utf-8") as f:
    f.write(index_html)

# --- 4. style.css ---
style_css = """*{margin:0;padding:0;box-sizing:border-box;font-family:'Poppins',sans-serif;}
body{color:#333;line-height:1.6;background:#fff;}
header{background:#004a5c;color:white;display:flex;justify-content:space-between;align-items:center;padding:15px 30px;}
.logo{font-size:1.5em;font-weight:bold;}
nav ul{list-style:none;display:flex;}
nav li{margin:0 15px;}
nav a{color:white;text-decoration:none;transition:.3s;}
nav a:hover{color:#ffd700;}
.hero{color:white;height:100vh;background-position:center;display:flex;align-items:center;justify-content:center;text-align:center;background-size:cover;}
.hero-text h2{font-size:3em;margin-bottom:10px;}
.hero-text p{font-size:1.2em;margin-bottom:20px;}
.btn{display:inline-block;margin-top:15px;background:#ffd700;color:#004a5c;padding:10px 20px;border-radius:5px;text-decoration:none;font-weight:bold;}
.btn:hover{background:#ffa500;}
section{padding:60px 20px;text-align:center;}
.destinations .destination-grid,.tours .tour-grid{display:flex;flex-wrap:wrap;justify-content:center;gap:20px;}
.card{background:#f5f5f5;border-radius:10px;padding:20px;width:300px;box-shadow:0 2px 8px rgba(0,0,0,0.1);transition:transform .3s;}
.card:hover{transform:translateY(-5px);}
.card img{width:100%;border-radius:10px;margin-bottom:15px;}
.contact form{display:flex;flex-direction:column;max-width:500px;margin:0 auto 30px;}
.contact input,.contact textarea{margin:10px 0;padding:10px;border:1px solid #ccc;border-radius:5px;}
footer{background:#004a5c;color:white;text-align:center;padding:20px 0;}
@media(max-width:768px){.destination-grid,.tour-grid{flex-direction:column;align-items:center;}nav ul{flex-direction:column;}}"""

with open(f"{folder_name}/style.css", "w", encoding="utf-8") as f:
    f.write(style_css)

# --- 5. Create ZIP ---
zip_filename = f"{folder_name}.zip"
with zipfile.ZipFile(zip_filename, "w") as zipf:
    for root, dirs, files in os.walk(folder_name):
        for file in files:
            zipf.write(os.path.join(root, file),
                       os.path.relpath(os.path.join(root, file), folder_name))

print(f"Website ZIP created successfully: {zip_filename}")
