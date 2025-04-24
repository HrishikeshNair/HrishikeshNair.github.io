---
layout: default
title: Photography
permalink: /photography/
---

<h1 style="text-align: center;">Photography</h1>
<p class="subheading" style="text-align: center;">Mostly taken on my phone, all random and some occasionally interesting. Click on them to find out more.</p>

<!-- Main photo grid -->
<div class="photo-grid">


		<!-- 1 -->
		<div class="photo-item" data-title="Monsoon in Wayanad" data-description="By the Karapuzha Reservoir on a July afternoon.<br><i>Pixel 7 Pro, unedited</i>">
		  <img src="/images/photo1.jpg" alt="Photo 1" />
		  <div class="photo-caption">Monsoon in Wayanad</div>
		</div>

		<!-- 2 -->
		<div class="photo-item" data-title="The God's Arrival" data-description="Krishna bows in namaskaram before he begins his act in the tale of Rukmini Swayamvaram.<br><i>Pixel 7 Pro, colors slightly muted</i>">
		  <img src="/images/photo2.jpg" alt="Photo 2" />
		  <div class="photo-caption">The God's Arrival</div>
		</div>

		<!-- 3 -->
		<div class="photo-item" data-title="Station Blur" data-description="Train to catch on a rainy evening.<br><i>Pixel 7 Pro, action pan</i>">
		  <img src="/images/photo3.jpg" alt="Photo 3" />
		  <div class="photo-caption">Station Blur</div>
		</div>

		<!-- 4 -->
		<div class="photo-item" data-title="Another Bangalore Sunset" data-description="Captured on one of those brief moments you forget you're in a city.<br><i>Pixel 7 Pro, unedited</i>">
		  <img src="/images/photo4.jpg" alt="Photo 4" />
		  <div class="photo-caption">Another Bangalore Sunset</div>
		</div>

		<!-- 5 -->
		<div class="photo-item" data-title="Night at Naru" data-description="Naru Noodle Bar. Ramen was great, skip the matcha ice cream.<br><i>Pixel 7 Pro, unedited</i>">
		  <img src="/images/photo5.jpg" alt="Photo 5" />
		  <div class="photo-caption">Night at Naru</div>
		</div>

		<!-- 6 -->
		<div class="photo-item" data-title="Evening Sway" data-description="Hanging bridge at golden hour on the Kariangode river.<br><i>Pixel 7 Pro, slightly saturated</i>">
		  <img src="/images/photo6.jpg" alt="Photo 6" />
		  <div class="photo-caption">Evening Sway</div>
		</div>

		<!-- 7 -->
		<div class="photo-item" data-title="Crisp Formation" data-description="Aarogya Aahara used to be great before it got so crowded :( (Plain dosa gang ftw)<br><i>Pixel 7 Pro, unedited</i>">
		  <img src="/images/photo7.jpg" alt="Photo 7" />
		  <div class="photo-caption">Crisp Formation</div>
		</div>
		
		
		
</div>

<!-- Lightbox Modal (hidden by default) -->
<div id="photo-modal" class="photo-modal">
  <span class="close-btn">&times;</span>
  <img class="modal-image" src="" alt="Full View" />
  <div class="modal-caption">
    <h2 class="modal-title"></h2>
    <p class="modal-description"></p>
  </div>
  <div class="modal-nav">
    <span class="prev">&#10094;</span>
    <span class="next">&#10095;</span>
  </div>
</div>

<!-- ===== Lightbox Functionality ===== -->
<script>
  const modal = document.getElementById("photo-modal");
  const modalImg = modal.querySelector(".modal-image");
  const modalTitle = modal.querySelector(".modal-title");
  const modalDesc = modal.querySelector(".modal-description");
  const closeBtn = modal.querySelector(".close-btn");
  const prevBtn = modal.querySelector(".prev");
  const nextBtn = modal.querySelector(".next");
  const photoItems = Array.from(document.querySelectorAll(".photo-item"));

  let currentIndex = 0;

  function openModal(index) {
    const item = photoItems[index];
    modal.classList.add("active");
    modalImg.src = item.querySelector("img").src;
    modalTitle.textContent = item.dataset.title || "";
    modalDesc.innerHTML = item.dataset.description || ""; // ← innerHTML for <br> and <i>
    currentIndex = index;
  }

  function closeModal() {
    modal.classList.remove("active");
  }

  function showNext() {
    currentIndex = (currentIndex + 1) % photoItems.length;
    openModal(currentIndex);
  }

  function showPrev() {
    currentIndex = (currentIndex - 1 + photoItems.length) % photoItems.length;
    openModal(currentIndex);
  }

  // Attach click listeners to each photo
  photoItems.forEach((item, index) => {
    item.addEventListener("click", () => openModal(index));
  });

  // Navigation and close
  closeBtn.addEventListener("click", closeModal);
  nextBtn.addEventListener("click", showNext);
  prevBtn.addEventListener("click", showPrev);

  // Keyboard support
  window.addEventListener("keydown", (e) => {
    if (!modal.classList.contains("active")) return;
    if (e.key === "ArrowRight") showNext();
    if (e.key === "ArrowLeft") showPrev();
    if (e.key === "Escape") closeModal();
  });
  
  
  <!-- Back to Top Button -->
<button id="backToTop" title="Back to Top">&#8679;</button>

  
</script>
<!-- Scroll-to-Top Behavior -->
<script>
  const backToTopBtn = document.getElementById("backToTop");

  window.addEventListener("scroll", () => {
    backToTopBtn.style.display = window.scrollY > 300 ? "block" : "none";
  });

  backToTopBtn.addEventListener("click", () => {
    window.scrollTo({ top: 0, behavior: "smooth" });
  });
</script>
