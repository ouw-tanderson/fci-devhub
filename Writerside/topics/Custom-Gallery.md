# Custom Gallery

**Description:**
This section provides a custom gallery layout for displaying images in a grid format.

## Instrunctions
- When interested in creating a custom gallery, use HTML block.
- Modifiy CSS styles to fit the design requirements.

**Example:**
```html
<section class="photo-gallery">
	<h2>Our Recent Laminate Projects</h2>
	<div class="gallery-grid">
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-1.jpg" alt="Close-up of laminate flooring showing realistic wood grain and texture." class="gallery-image lazyload">
			<p class="caption">Laminate flooring delivers the rich look of real wood with impressive accuracy. From natural grain patterns to authentic textures, it combines style with durability, making it a versatile and cost-effective choice for any space.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-2.jpg" alt="Close-up of laminate flooring showing realistic wood grain and texture." class="gallery-image lazyload">
			<p class="caption">Laminate flooring delivers the rich look of real wood with impressive accuracy. From natural grain patterns to authentic textures, it combines style with durability, making it a versatile and cost-effective choice for any space.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-3.jpg" alt="Professional installing laminate flooring with precision tools for seamless finish." class="gallery-image lazyload">
			<p class="caption">Proper installation is crucial for the longevity and performance of laminate flooring. With precision tools and expert technique, we ensure flawless seams, secure locking systems, and a smooth, professional finish—maximizing durability and beauty in every project.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-4.jpg" alt="Laminate flooring installed on stairs, providing a modern wood-look finish." class="gallery-image lazyload">
			<p class="caption">Laminate is a great way to refresh stairs with a modern, durable finish. It provides the look of real wood while offering added resistance to wear and tear. Our expertise ensures precise installation, creating seamless transitions and a polished, professional result.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-5.jpg" alt="Clean laminate floor surface, easy to maintain and resistant to stains." class="gallery-image lazyload">
			<p class="caption">Laminate flooring is designed for effortless maintenance—just a quick sweep or mop keeps it looking fresh. Its smooth, sealed surface resists stains and dirt, making it a hassle-free choice for busy homes and businesses.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-6.jpg" alt="Laminate flooring being installed over existing tile for a refreshed look." class="gallery-image lazyload">
			<p class="caption">Laminate flooring can be installed directly over existing tile, eliminating the need for messy and costly demolition. This makes it a convenient, budget-friendly option for refreshing spaces with minimal disruption. Our expert installation ensures a seamless fit, giving your floors a fresh, polished look without the hassle.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-7.jpg" alt="Floating laminate floor panels being clicked together without glue or nails." class="gallery-image lazyload">
			<p class="caption">Most laminate floors are installed as floating systems, meaning they don’t require glue or nails—just a secure, click-lock design. This makes installation quick and efficient, minimizing downtime while delivering a flawless, professional finish.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-8.jpg" alt="Laminate flooring in a home with children and pets, showing scratch resistance." class="gallery-image lazyload">
			<p class="caption">Laminate flooring is perfect for homes with kids and pets, thanks to its durability and scratch resistance. Its tough wear layer protects against spills, claws, and everyday wear, making it a practical and stylish choice for busy households.</p>
		</div>
		<div class="gallery-item">
			<img data-src="${asset_url_prefix}/img/upload/laminate-9.jpg" alt="Installer cutting laminate flooring outdoors to minimize dust during installation." class="gallery-image lazyload">
			<p class="caption">Laminate flooring installation is quick and hassle-free, thanks to its simple click-lock system. Any cutting or adjustments are done outside, keeping dust and mess away from your home. The result? A clean, efficient process and a beautifully finished floor without the disruption.</p>
		</div>
	</div>
</section>

<style>
	.photo-gallery {
		max-width: 1200px;
		margin: 2em auto;
		padding: 0 1em;
		text-align: center;
		}

	.gallery-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		gap: 1em;
		}

	.gallery-item {
		display: flex;
		flex-direction: column;
		align-items: center;
		}

	.gallery-item img {
		width: 100%;
		height: auto;
		border-radius: 8px;
		object-fit: cover;
		box-shadow: 0 2px 6px rgba(0,0,0,0.1);
		transition: transform 0.3s ease;
		}

	.gallery-item img:hover {
		transform: scale(1.02);
		}

	.caption {
		margin-top: 0.5em;
		font-size: 0.875rem;
		color: #333;
		text-align: left;
		}
</style>
```
