---
layout: project
title: Spotted Lanternfly Trap
description: Client pitch and functional prototype for a vineyard SLF capture system
image: /assets/images/SLF_trap.jpg
---

<style>
.project-links {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  margin: 1rem 0 1.5rem 0;
}

.project-links a {
  display: inline-block;
  padding: 0.55rem 0.9rem;
  border: 1px solid #444;
  border-radius: 999px;
  text-decoration: none;
  color: inherit;
  transition: 0.2s ease;
}

.project-links a:hover {
  background: rgba(255,255,255,0.08);
}

.project-section {
  margin-top: 2.5rem;
}

.project-card {
  border: 1px solid #333;
  border-radius: 14px;
  padding: 1.25rem;
  margin-top: 1rem;
}

.project-card iframe {
  width: 100%;
  height: 75vh;
  border: 0;
  margin-top: 1rem;
}
</style>

## Project Overview

The design goal is to trap spotted lanternflies while they feed at the basin, using a rotating fan mechanism to sweep them into a one-way trap.

<div class="project-links">
  <a href="#client-pitch">Client Pitch</a>
  <a href="#functional-prototype">Functional Prototype</a>
  <a href="#top">Full Website</a>
</div>

<div id="client-pitch" class="project-section">
  <h2>Client Pitch</h2>
  <div class="project-card">
    <p>
      This milestone introduces the initial design concept, user need, and validation plan for the trap.
    </p>

    <p>
      <a href="{{ '/assets/Batties_ClientPitch.pdf' | relative_url }}" target="_blank" rel="noopener">
        Open Client Pitch PDF
      </a>
    </p>

    <iframe
      src="{{ '/assets/Batties_ClientPitch.pdf' | relative_url }}"
      loading="lazy">
    </iframe>
  </div>
</div>

<div id="functional-prototype" class="project-section">
  <h2>Functional Prototype</h2>
  <div class="project-card">
    <h3>Purpose</h3>
    <p>
      The functional prototype was built to test whether the rotating mechanism could move spotted lanternfly-sized objects into collection slots while maintaining smooth motion and workable spacing.
    </p>

    <h3>What was tested</h3>
    <ul>
      <li>Smooth motion through the bristled regions</li>
      <li>Ability to operate at low rotational speed</li>
      <li>Friction between the fan and the plate</li>
      <li>Bending and warping of the structure</li>
      <li>Ability to move SLF-sized objects into the trap openings</li>
    </ul>

    <h3>Outcome</h3>
    <p>
      The prototype showed that the mechanism can move SLF-sized objects, but the wooden construction caused significant friction, bending, and spacing issues. These results suggest that future iterations should use more precise or flexible materials, improve tooth spacing and geometry, and add better structural support.
    </p>

    <p>
      <a href="{{ '/assets/ODP5.pdf' | relative_url }}" target="_blank" rel="noopener">
        Open Functional Prototype PDF
      </a>
    </p>

    <iframe
      src="{{ '/assets/ODP5.pdf' | relative_url }}"
      loading="lazy">
    </iframe>
  </div>
</div>