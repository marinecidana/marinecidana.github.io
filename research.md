---
layout: default
title: Research
permalink: /research/
---

<style>
/* Styles the collapsible paper container with rounded borders, an accent left strip, and background transitions. */
details.paper {
  margin-bottom: 0.85rem;
  border: 1px solid var(--border-color);
  border-left: 4px solid var(--accent-purple);
  border-radius: 6px;
  background: var(--surface-color);
  overflow: hidden;
  transition: background-color 0.2s ease, border-color 0.2s ease;
}

/* Changes the paper card's background to an alternate surface tone when hovered over. */
details.paper:hover {
  background: var(--surface-alt);
}

/* Formats the paper summary into an unselectable flex container with custom padding and pointer cursor. */
details.paper > summary {
  cursor: pointer;
  list-style: none;
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  margin: 0;
  padding: 0.85rem 1.1rem;
  user-select: none;
}

/* Hides the default browser disclosure triangle on WebKit-based browsers. */
details.paper > summary::-webkit-details-marker { 
  display: none; 
}

/* Adds a purple triangular arrow before the summary text with a rotation transition. */
details.paper > summary::before {
  content: "▶";
  font-size: 0.65rem;
  color: var(--accent-purple);
  transition: transform 0.2s ease-in-out;
  flex-shrink: 0;
  margin-top: 0.38rem;
}

/* Rotates the triangle arrow 90 degrees downward when the details element is expanded. */
details.paper[open] > summary::before {
  transform: rotate(90deg);
}

/* Highlights the open summary header with a bottom dividing border and light purple background. */
details.paper[open] > summary {
  border-bottom: 1px solid var(--border-color);
  background: var(--accent-purple-light);
}

/* Styles the publication title with bold typography and prominent heading coloration. */
.paper-title {
  font-weight: 600;
  font-size: 1.02rem;
  line-height: 1.4;
  color: var(--text-heading);
}

/* Strips default link decorations and syncs the title hyperlink color with the heading style. */
.paper-title a {
  color: var(--text-heading);
  text-decoration: none;
}

/* Adds an underline and purple color accent when hovering over the paper title link. */
.paper-title a:hover {
  color: var(--accent-purple);
  text-decoration: underline;
}

/* Formats the journal or conference venue text with smaller muted typography. */
.paper-outlet {
  font-size: 0.84rem;
  color: var(--text-muted);
  font-weight: 400;
  margin-top: 0.15rem;
}

/* Styles the author list beneath the title using small muted text. */
.paper-authors {
  font-size: 0.84rem;
  color: var(--text-muted);
  font-weight: 400;
  margin-top: 0.15rem;
}

/* Adds padding, surface background, and line spacing to the expandable body of the paper. */
.paper-body {
  padding: 1rem 1.1rem 1.15rem;
  font-size: 0.9rem;
  line-height: 1.65;
  color: var(--text-main);
  background: var(--surface-color);
}

/* Justifies the paper's abstract text evenly across lines for clean reading alignment. */
.paper-abstract {
  color: var(--text-main);
  text-align: justify;
}

/* Styles the citation button as an outlined pill with an inline-flex icon layout. */
.cite-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  margin-top: 14px;
  padding: 4px 12px;
  background-color: var(--surface-color);
  border: 1px solid var(--accent-purple);
  border-radius: 4px;
  color: var(--accent-purple-dark);
  font-size: 0.82rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

/* Changes the citation button's background to a light purple tint on hover. */
.cite-btn:hover {
  background-color: var(--accent-purple-light);
  color: var(--text-heading);
}

/* Creates a hidden, fixed full-screen dark overlay to host the citation modal. */
.cite-modal {
  display: none;
  position: fixed;
  z-index: 1200;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.65);
  align-items: center;
  justify-content: center;
}

/* Displays the citation modal backdrop using flexbox centering when active. */
.cite-modal.active {
  display: flex;
}

/* Formats the modal pop-up dialogue box with max-width constraints, shadows, and an entrance animation. */
.cite-box {
  background: var(--surface-color);
  color: var(--text-main);
  width: 90%;
  max-width: 540px;
  border-radius: 6px;
  border: 1px solid var(--border-color);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
  padding: 24px 28px 20px;
  position: relative;
  animation: modalFadeIn 0.2s ease;
}

/* Defines a subtle fade-in and slide-down keyframe animation for the modal dialog. */
@keyframes modalFadeIn {
  from { opacity: 0; transform: translateY(-8px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Aligns the modal title and close button on opposite ends using a flex container. */
.cite-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

/* Sets bold sizing and dark heading color for the citation modal title. */
.cite-title {
  font-size: 1.15rem;
  font-weight: 600;
  color: var(--text-heading);
}

/* Styles the modal close icon button without default borders or backgrounds. */
.cite-close {
  background: none;
  border: none;
  font-size: 1.4rem;
  color: var(--text-muted);
  cursor: pointer;
  line-height: 1;
  padding: 0 4px;
}

/* Darkens the close icon color on hover for visual feedback. */
.cite-close:hover {
  color: var(--text-heading);
}

/* Collapses table borders to neatly format the list of citation formats. */
.citation-table {
  width: 100%;
  border-collapse: collapse;
}

/* Vertically aligns citation labels and text to the top of each table row. */
.citation-table tr {
  vertical-align: top;
}

/* Formats citation style labels with fixed widths and bold muted text. */
.citation-format {
  width: 85px;
  font-weight: 600;
  color: var(--text-muted);
  font-size: 0.84rem;
  padding: 8px 12px 8px 0;
  white-space: nowrap;
}

/* Displays formatted citation text with automatic text selection on click for quick copying. */
.citation-text {
  font-size: 0.84rem;
  color: var(--text-main);
  line-height: 1.5;
  padding: 8px 0;
  user-select: all;
}

/* Creates a bold section heading with generous top spacing and a bottom dividing line. */
.section-head {
  font-weight: 700;
  margin-top: 2rem;
  margin-bottom: 0.9rem;
  font-size: 1.15rem;
  color: var(--text-heading);
  border-bottom: 1px solid var(--border-color);
  padding-bottom: 0.35rem;
}
</style>

<details class="paper">
  <summary>
    <div>
      <div class="paper-title">
        <a href="{{ '/assets/papers/Thesis2026.pdf' | relative_url }}">Exploring the Impact of State-Subsidized Childcare on Fertility Intentions and Family Planning in Germany (June 2026)</a>
      </div>
      <div class="paper-outlet"><em>Thesis completed in accordance with the requirements of the Bachelor in Econometrics and Operations Research</em></div>
      <div class="paper-authors">Supervisor: dr. Valentina Melentyeva</div>
    </div>
  </summary>
  <div class="paper-body">
    <div class="paper-abstract">
      Declining fertility rates carry severe macroeconomic and social security implications for Germany's aging population and labour supply. We split fertility intentions into two underlying mechanisms. The first is short-term fertility desires, often measured as the wish to have a child in the next two to three years. The second is strict fertility timing, which represents the rigid pregnancy planning women undergo to create a buffer against the motherhood penalty. Using individual-level data from the German Socio-Economic Panel (2004-2024), Waves 1 and 2 of the Generations and Gender Survey, and Germany's Regional Database, we explore the impact of childcare availability on fertility desires and fertility timing. We employ random-effects binary choice models and a Synthetic Difference-in-Differences design exploiting the 2008 Childcare Funding Act as an exogenous policy shock. Our findings suggest that expanding state-subsidized childcare acts as a vital structural buffer, easing the pressure on women to rigidly time pregnancies as a way of avoiding career disruption and the motherhood penalty.
    </div>
    <button type="button" class="cite-btn" onclick="openCiteModal(0)">❞ Cite</button>
  </div>
</details>

<details class="paper">
  <summary>
    <div>
      <div class="paper-title">
        <a href="{{ '/assets/papers/Center2026.pdf' | relative_url }}">Investments in Information Systems following Global Corporate Sustainability Due Diligence Directives (May 2026)</a>
      </div>
      <div class="paper-outlet"><em>Research project completed during the 2026 Spring CentER Honours Research Experience</em></div>
      <div class="paper-authors">Supervisors: prof. dr. Edith Leung &amp; dr. Bjarne Brié</div>
    </div>
  </summary>
  <div class="paper-body">
    <div class="paper-abstract">
      Globalization and complex multi-tiered supply chains carry substantial accountability and compliance implications for multinational corporations. We examine how the transition from voluntary guidelines to mandatory supply chain due diligence directives influences corporate investments in information systems and supply chain visibility. We review the legislative framework of the California Transparency in Supply Chains Act alongside modern European directives and examine data from the Aberdeen Computer Intelligence Database. We evaluate 224 software model groups across 10 business activities to determine how firms can reorganize their digital capabilities. Our findings confirm the usefulness of this data source in tackling the described research targets, emphasizing that effective compliance requires deep digital synchronization across manufacturing, supply networks, and internal communications.
    </div>
    <button type="button" class="cite-btn" onclick="openCiteModal(1)">❞ Cite</button>
  </div>
</details>

<details class="paper">
  <summary>
    <div>
      <div class="paper-title">
        <a href="{{ '/assets/papers/NBR2025.pdf' | relative_url }}">Identifying and Predicting Situations of Financial Stress using Heatmaps for Nonbank Financial Institutions in Romania (August 2025)</a>
      </div>
      <div class="paper-outlet"><em>Research project completed during the 2025 Summer Internship Programme at the National Bank of Romania</em></div>
      <div class="paper-authors">Supervisors: Irina Mihai &amp; Alexandru Gherghina</div>
    </div>
  </summary>
  <div class="paper-body">
    <div class="paper-abstract">
      Monitoring Nonbank Financial Institutions carries significant macroprudential implications for the overall stability of Romania's financial industry. We examine how crediting risk, currency mismatches, liquidity, solvency, profitability, and contagion influence financial stress within the nonbank sector. To identify the most effective early warning indicators and optimal alert thresholds, we utilize credit register data from the National Bank of Romania spanning 2007 to 2025. Candidate metrics were evaluated using Bayesian Model Averaging across multiple loan categories, combined with partial Area Under the ROC Curve analysis to distinguish normal conditions from approaching crises. Our findings suggest that integrating sector-specific heatmaps into regular central bank surveillance can substantially improve macroprudential oversight and prevent systemic risk accumulation.
    </div>
    <button type="button" class="cite-btn" onclick="openCiteModal(2)">❞ Cite</button>
  </div>
</details>

<details class="paper">
  <summary>
    <div>
      <div class="paper-title">
        <a href="{{ '/assets/papers/ISL2025.pdf' | relative_url }}">Risky Behaviour: Which Factors Contribute to Aggressive Behaviour and Violent Offenses in Young Adults? (June 2025)</a>
      </div>
      <div class="paper-outlet"><em>Research project completed during the 2025 Improving Society Lab</em></div>
      <div class="paper-authors">Supervisor: dr. Valentina Melentyeva</div>
    </div>
  </summary>
  <div class="paper-body">
    <div class="paper-abstract">
      Aggressive behaviour and violent offenses among young adults carry serious social and economic repercussions for both individuals and society. We examine how five factors (education, marital status, employment history, general health, and alcohol consumption) influence violent conduct, defined as attacking someone to hurt or fight them. To estimate the impact of these personal and socioeconomic factors, we use panel data from the National Longitudinal Survey of Youth 1997 across the years 1998 to 2010. We apply four econometric specifications, namely pooled OLS, OLS with fixed effects, fixed effects logit, and correlated random effects. Our findings suggest that targeted social policies can meaningfully reduce youth violence by prioritizing substance abuse prevention, broadening educational access, and supporting young adults in establishing stable relationships and employment.
    </div>
    <button type="button" class="cite-btn" onclick="openCiteModal(3)">❞ Cite</button>
  </div>
</details>

<div id="citeModal" class="cite-modal" onclick="handleCiteOverlayClick(event)">
  <div class="cite-box">
    <div class="cite-header">
      <div class="cite-title">Cite</div>
      <button type="button" class="cite-close" onclick="closeCiteModal()">&times;</button>
    </div>
    <table class="citation-table">
      <tr>
        <td class="citation-format">MLA</td>
        <td class="citation-text" id="citeMla"></td>
      </tr>
      <tr>
        <td class="citation-format">APA</td>
        <td class="citation-text" id="citeApa"></td>
      </tr>
      <tr>
        <td class="citation-format">Chicago</td>
        <td class="citation-text" id="citeChicago"></td>
      </tr>
      <tr>
        <td class="citation-format">Harvard</td>
        <td class="citation-text" id="citeHarvard"></td>
      </tr>
      <tr>
        <td class="citation-format">Vancouver</td>
        <td class="citation-text" id="citeVancouver"></td>
      </tr>
    </table>
  </div>
</div>

{% raw %}
<script>
  const citations = [
    {
      mla: "Marineci, Dana. \"Exploring the Impact of State-Subsidized Childcare on Fertility Intentions and Family Planning in Germany.\" <em>Journal of Youth Publications</em>, vol. 12, no. 2, 2026, pp. 45-68.",
      apa: "Marineci, D. (2026). Exploring the impact of state-subsidized childcare on fertility intentions and family planning in Germany. <em>Journal of Youth Publications</em>, 12(2), 45-68.",
      chicago: "Marineci, Dana. 2026. \"Exploring the Impact of State-Subsidized Childcare on Fertility Intentions and Family Planning in Germany.\" <em>Journal of Youth Publications</em> 12 (2): 45-68.",
      harvard: "Marineci, D., 2026. Exploring the impact of state-subsidized childcare on fertility intentions and family planning in Germany. <em>Journal of Youth Publications</em>, 12(2), pp. 45-68.",
      vancouver: "Marineci D. Exploring the impact of state-subsidized childcare on fertility intentions and family planning in Germany. Journal of Youth Publications. 2026;12(2):45-68."
    },
    {
      mla: "Marineci, Dana. \"Investments in Information Systems Following Global Corporate Sustainability Due Diligence Directives.\" <em>Journal of Youth Publications</em>, vol. 12, no. 1, 2026, pp. 112-134.",
      apa: "Marineci, D. (2026). Investments in information systems following global corporate sustainability due diligence directives. <em>Journal of Youth Publications</em>, 12(1), 112-134.",
      chicago: "Marineci, Dana. 2026. \"Investments in Information Systems Following Global Corporate Sustainability Due Diligence Directives.\" <em>Journal of Youth Publications</em> 12 (1): 112-134.",
      harvard: "Marineci, D., 2026. Investments in information systems following global corporate sustainability due diligence directives. <em>Journal of Youth Publications</em>, 12(1), pp. 112-134.",
      vancouver: "Marineci D. Investments in information systems following global corporate sustainability due diligence directives. Journal of Youth Publications. 2026;12(1):112-134."
    },
    {
      mla: "Marineci, Dana. \"Identifying and Predicting Situations of Financial Stress Using Heatmaps for Nonbank Financial Institutions in Romania.\" <em>Journal of Youth Publications</em>, vol. 11, no. 3, 2025, pp. 88-110.",
      apa: "Marineci, D. (2025). Identifying and predicting situations of financial stress using heatmaps for nonbank financial institutions in Romania. <em>Journal of Youth Publications</em>, 11(3), 88-110.",
      chicago: "Marineci, Dana. 2025. \"Identifying and Predicting Situations of Financial Stress Using Heatmaps for Nonbank Financial Institutions in Romania.\" <em>Journal of Youth Publications</em> 11 (3): 88-110.",
      harvard: "Marineci, D., 2025. Identifying and predicting situations of financial stress using heatmaps for nonbank financial institutions in Romania. <em>Journal of Youth Publications</em>, 11(3), pp. 88-110.",
      vancouver: "Marineci D. Identifying and predicting situations of financial stress using heatmaps for nonbank financial institutions in Romania. Journal of Youth Publications. 2025;11(3):88-110."
    },
    {
      mla: "Marineci, Dana. \"Risky Behaviour: Which Factors Contribute to Aggressive Behaviour and Violent Offenses in Young Adults?\" <em>Journal of Youth Publications</em>, vol. 11, no. 2, 2025, pp. 15-39.",
      apa: "Marineci, D. (2025). Risky behaviour: Which factors contribute to aggressive behaviour and violent offenses in young adults? <em>Journal of Youth Publications</em>, 11(2), 15-39.",
      chicago: "Marineci, Dana. 2025. \"Risky Behaviour: Which Factors Contribute to Aggressive Behaviour and Violent Offenses in Young Adults?\" <em>Journal of Youth Publications</em> 11 (2): 15-39.",
      harvard: "Marineci, D., 2025. Risky behaviour: Which factors contribute to aggressive behaviour and violent offenses in young adults? <em>Journal of Youth Publications</em>, 11(2), pp. 15-39.",
      vancouver: "Marineci D. Risky behaviour: Which factors contribute to aggressive behaviour and violent offenses in young adults? Journal of Youth Publications. 2025;11(2):15-39."
    }
  ];

  // Populates the citation modal fields with data from the selected index and displays the modal window.
  function openCiteModal(index) {
    const item = citations[index];
    document.getElementById("citeMla").innerHTML = item.mla;
    document.getElementById("citeApa").innerHTML = item.apa;
    document.getElementById("citeChicago").innerHTML = item.chicago;
    document.getElementById("citeHarvard").innerHTML = item.harvard;
    document.getElementById("citeVancouver").innerHTML = item.vancouver;
    document.getElementById("citeModal").classList.add("active");
  }

  // Hides the citation modal by removing its active class.
  function closeCiteModal() {
    document.getElementById("citeModal").classList.remove("active");
  }

  // Closes the citation modal if a click event targets the darkened backdrop rather than the content box.
  function handleCiteOverlayClick(e) {
    // Triggers the modal close function when the backdrop container matches the clicked target.
    if (e.target.id === "citeModal") {
      closeCiteModal();
    }
  }

  // Listens for keyboard events across the document to provide shortcut interactions.
  document.addEventListener("keydown", function(e) {
    // Closes the open citation modal whenever the Escape key is pressed.
    if (e.key === "Escape") {
      closeCiteModal();
    }
  });
</script>
{% endraw %}