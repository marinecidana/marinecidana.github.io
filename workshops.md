---
layout: default
title: Workshops
permalink: /workshops/
---

<div class="filter-container">
  <button type="button" class="filter-btn active" data-filter="all">All</button>
  <button type="button" class="filter-btn" data-filter="advocacy">Advocacy</button>
  <button type="button" class="filter-btn" data-filter="quantitative">Data</button>
  <button type="button" class="filter-btn" data-filter="careers">Business</button>
  <button type="button" class="filter-btn" data-filter="crisis">Management</button>
</div>

<div class="workshop-card" data-category="crisis">
    <div class="workshop-header">
      <h3 class="workshop-title">Resilience in Post-Disaster Zones</h3>
      <span class="workshop-date">October 2025</span>
    </div>
    <div class="workshop-collab">
     A collaboration between <strong>UNICEF Student Team Tilburg</strong> &amp; <strong>Studium Generale Tilburg</strong>
    </div>
    <p class="workshop-desc">
      An interactive crisis management simulation examining how humanitarian agencies respond when environmental catastrophes destroy educational infrastructure. Students walked through real emergency protocols such as rapid mobilization of temporary learning tents, water sanitation and psycho-social protection for displaced children in the first 72 hours of sudden disasters.
    </p>
  </div>

  <div class="workshop-card" data-category="careers">
    <div class="workshop-header">
      <h3 class="workshop-title">Purpose-Driven Finance and Management</h3>
      <span class="workshop-date">April 2025</span>
    </div>
    <div class="workshop-collab">
      A collaboration between <strong>UNICEF Student Team Tilburg</strong> &amp; <strong>Economic Business Weeks Tilburg</strong>
    </div>
    <p class="workshop-desc">
      Tailored for students in TiSEM, this session explored the different career paths that graduates can pivot into. We covered fiscal transparency, donor fund allocation, and audit standards in international NGOs, demonstrating that financial accounting and strategic analytics are critical assets for public service and humanitarian organizations such as UNICEF.
    </p>
  </div>

  <div class="workshop-card" data-category="quantitative">
    <div class="workshop-header">
      <h3 class="workshop-title">Math Against Malnutrition</h3>
      <span class="workshop-date">November 2024</span>
    </div>
    <div class="workshop-collab">
      A collaboration between <strong>UNICEF Student Team Tilburg</strong> &amp; <strong>Zero Hunger Lab</strong>
    </div>
    <p class="workshop-desc">
      This interdisciplinary session bridged mathematical programming and humanitarian logistics. Participants explored how linear programming, network routing, and mixed-integer optimization models are actively deployed to optimize food distribution chains, minimize transit times, and tackle malnutrition in famine-affected regions.
    </p>
  </div>

<div class="workshop-grid">
  <div class="workshop-card" data-category="advocacy">
    <div class="workshop-header">
      <h3 class="workshop-title">Addressing the Global Literacy Crisis</h3>
      <span class="workshop-date">March 2024</span>
    </div>
    <div class="workshop-collab">
      A collaboration between <strong>UNICEF Student Team Tilburg</strong> &amp; <strong>The Scriptorium</strong>
    </div>
    <p class="workshop-desc">
      A collaborative workshop addressing both the current youth literacy gap and the art of structured advocacy writing. Participants examined recent global data on functional literacy disruptions post-COVID-19, followed by a training module on how students can translate complex humanitarian findings into persuasive and accessible articles.
    </p>
  </div>

</div>

{% raw %}
<script>
// Encapsulates the script within an Immediately Invoked Function Expression to avoid damaging the global scope.
(function() {
  // Finds filter buttons and workshop cards, attaching click listeners to handle category filtering.
  function initFilter() {
    var buttons = document.querySelectorAll(".filter-btn");
    var cards = document.querySelectorAll(".workshop-card");

    if (!buttons.length || !cards.length) return;

    // Iterates through each filter button to bind click handling behavior.
    buttons.forEach(function(btn) {
      // Handles button clicks by updating active styling and showing or hiding matching workshop cards.
      btn.onclick = function() {
        var selectedFilter = this.getAttribute("data-filter");

        // Removes the active highlight class from all filter buttons.
        buttons.forEach(function(b) { b.classList.remove("active"); });
        this.classList.add("active");

        // Evaluates each card against the selected filter and toggles its display property accordingly.
        cards.forEach(function(card) {
          var cardCat = card.getAttribute("data-category");
          // Shows the card if the filter matches its category or if "all" is selected.
          if (selectedFilter === "all" || cardCat === selectedFilter) {
            card.style.display = "block";
          // Hides cards that do not match the chosen filter category.
          } else {
            card.style.display = "none";
          }
        });
      };
    });
  }

  if (document.readyState === "loading") {
    document.addEventListener("DOMContentLoaded", initFilter);
  // Executes initialization immediately if the document has already finished loading.
  } else {
    initFilter();
  }
})();
</script>
{% endraw %}