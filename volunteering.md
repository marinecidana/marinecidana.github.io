---
layout: default
title: Volunteering
permalink: /volunteering/
---

<div class="volunteer-entry">
  <div class="volunteer-text">
    <span class="volunteer-date">August 2020 – July 2023</span>
    <h2>Girl Up Romania</h2>
    <p>
      I spent three years holding various positions in my home country’s first youth-led gender equality and women’s rights group, Girl Up Romania. Founded in 2018 by activist Sofia Scarlat as a local team of the United Nations Foundation’s global Girl Up initiative, it mobilizes young Romanians to fight gender-based discrimination, violence, and institutional inequality.
    </p>
    <p>
      During my first year, I was a student volunteer, and was further elected as Vice-President and then Campaign Coordinator in the following two years. Some of my most notable contributions include conducting an AIDS prevention campaign, raising awareness about the Roma Slavery in Romania, and collecting donations and solidarity letters for victims of domestic violence.
    </p>
    <p>
      I have experience organizing a wide variety of events, including fundraising, educational, artistic, and protests, and have demonstrated leadership abilities by coordinating teams ranging from 30 local members to 100+ nationwide ambassadors. Moreover, I have developed public speaking skills by representing the group in conferences, talk-shows, and podcasts.
    </p>
  </div>

  <div class="volunteer-gallery-col">
    <div class="photo-grid-square" onclick="openGallery('girlup', 0)" title="Click to open photos">
      <img src="{{ '/assets/img/girlup1.jpg' | relative_url }}" onerror="this.src='https://placehold.co/400x400/ccccff/333?text=Girl+Up+1'" alt="Girl Up photo 1">
      <img src="{{ '/assets/img/girlup2.JPG' | relative_url }}" onerror="this.src='https://placehold.co/400x400/b8b8f0/333?text=Girl+Up+2'" alt="Girl Up photo 2">
      <img src="{{ '/assets/img/girlup3.JPG' | relative_url }}" onerror="this.src='https://placehold.co/400x400/d8d8fa/333?text=Girl+Up+3'" alt="Girl Up photo 3">
      <img src="{{ '/assets/img/girlup4.jpg' | relative_url }}" onerror="this.src='https://placehold.co/400x400/b0b0f5/333?text=Girl+Up+4'" alt="Girl Up photo 4">
      <div class="grid-overlay">🔍 View 4 Photos</div>
    </div>
  </div>
</div>

<div class="volunteer-entry">
  <div class="volunteer-text">
    <span class="volunteer-date">August 2023 – July 2025</span>
    <h2>UNICEF Student Team Tilburg</h2>
    <p>
      I spent two years in the UNICEF Student Team Tilburg, an international, student-run volunteer organization meant to promote children’s rights and share UNICEF’s values. This group operates under the supervision of the UNICEF Nederland office, which supports a nationwide network of university student teams and organises multiple trainings and networking events throughout the academic year.
    </p>
    <p>
      I started as a Student Volunteer and was further promoted to Treasurer, which pushed me to develop accounting and finance related skills, managing the organisation’s funds. Furthermore, I created and chaired the Advocacy Committee, which consisted of 10-15 students. Under my supervision, the members wrote articles detailing cases of children’s rights violations around the globe and encouraged Tilburg University students to stay informed and take action when possible.
    </p>
    <p>
      After carefully reviewing each article, I published the final result on the team’s social media platforms, spreading awareness about the importance of preserving children’s access to safety and education.
    </p>
  </div>

  <div class="volunteer-gallery-col">
    <div class="photo-grid-square" onclick="openGallery('unicef', 0)" title="Click to open photos">
      <img src="{{ '/assets/img/unicef1.jpg' | relative_url }}" onerror="this.src='https://placehold.co/400x400/ccccff/333?text=UNICEF+1'" alt="UNICEF photo 1">
      <img src="{{ '/assets/img/unicef2.jpg' | relative_url }}" onerror="this.src='https://placehold.co/400x400/b8b8f0/333?text=UNICEF+2'" alt="UNICEF photo 2">
      <img src="{{ '/assets/img/unicef3.jpg' | relative_url }}" onerror="this.src='https://placehold.co/400x400/d8d8fa/333?text=UNICEF+3'" alt="UNICEF photo 3">
      <img src="{{ '/assets/img/unicef4.jpg' | relative_url }}" onerror="this.src='https://placehold.co/400x400/b0b0f5/333?text=UNICEF+4'" alt="UNICEF photo 4">
      <div class="grid-overlay">🔍 View 4 Photos</div>
    </div>
  </div>
</div>

<div id="lightboxModal" class="lightbox-modal">
  <span class="lightbox-close" onclick="closeGallery()">&times;</span>
  <button class="lightbox-prev" onclick="changeSlide(-1)">&#10094;</button>
  <div class="lightbox-content-box">
    <img id="lightboxImg" src="" alt="Enlarged photo">
  </div>
  <button class="lightbox-next" onclick="changeSlide(1)">&#10095;</button>
  <div class="lightbox-counter" id="lightboxCounter">1 / 4</div>
</div>

<script>
  // Stores image paths for each volunteering gallery organized by category keys.
  const galleries = {
    girlup: [
      "{{ '/assets/img/girlup1.jpg' | relative_url }}",
      "{{ '/assets/img/girlup2.JPG' | relative_url }}",
      "{{ '/assets/img/girlup3.JPG' | relative_url }}",
      "{{ '/assets/img/girlup4.jpg' | relative_url }}"
    ],
    unicef: [
      "{{ '/assets/img/unicef1.jpg' | relative_url }}",
      "{{ '/assets/img/unicef2.jpg' | relative_url }}",
      "{{ '/assets/img/unicef3.jpg' | relative_url }}",
      "{{ '/assets/img/unicef4.jpg' | relative_url }}"
    ]
  };

  let currentGallery = [];
  let currentIndex = 0;

  // Initializes the active photo set at the selected index, updates the display, and reveals the lightbox modal.
  function openGallery(galleryName, index) {
    currentGallery = galleries[galleryName];
    currentIndex = index;
    updateLightbox();
    document.getElementById("lightboxModal").classList.add("active");
  }

  // Hides the lightbox modal by removing its active CSS class.
  function closeGallery() {
    document.getElementById("lightboxModal").classList.remove("active");
  }

  // Advances or reverses the photo carousel using modular arithmetic to loop continuously through images.
  function changeSlide(direction) {
    currentIndex = (currentIndex + direction + currentGallery.length) % currentGallery.length;
    updateLightbox();
  }

  // Updates the modal image source, configures a fallback placeholder on load errors, and refreshes the counter.
  function updateLightbox() {
    const imgElement = document.getElementById("lightboxImg");
    imgElement.src = currentGallery[currentIndex];
    // Swaps in a placeholder image if the requested image fails to load.
    imgElement.onerror = function() {
      this.src = "https://placehold.co/900x600/ccccff/333?text=Image+Placeholder";
    };
    document.getElementById("lightboxCounter").innerText = (currentIndex + 1) + " / " + currentGallery.length;
  }

  // Listens for global keystrokes to control the lightbox modal via keyboard shortcuts.
  document.addEventListener("keydown", function(e) {
    const modal = document.getElementById("lightboxModal");
    // Handles navigation and dismissal shortcuts only when the lightbox modal is actively visible.
    if (modal && modal.classList.contains("active")) {
      if (e.key === "ArrowLeft") changeSlide(-1);
      if (e.key === "ArrowRight") changeSlide(1);
      if (e.key === "Escape") closeGallery();
    }
  });
</script>