---
layout: project
title: Spotted Lanternfly Trap
description: Client pitch and functional prototype for a vineyard SLF capture system
---

<style>
.toc-box {
  border: 1px solid #ddd;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin: 1rem 0 2rem 0;
  background: #fafafa;
}

.toc-box ul {
  margin: 0.5rem 0 0 1.2rem;
}

.section-card {
  margin: 2rem 0 3rem 0;
  padding: 1.25rem;
  border: 1px solid #e5e5e5;
  border-radius: 12px;
  background: white;
}

.pdf-frame {
  width: 100%;
  height: 75vh;
  border: 0;
  margin-top: 1rem;
}

.jump-link {
  text-decoration: none;
  font-weight: 600;
}

.jump-link:hover {
  text-decoration: underline;
}
</style>

## Project Overview

This project proposes and tests a mechanical spotted lanternfly (SLF) trap for vineyard use. The design goal is to trap spotted lanternflies while they feed, using a rotating fan mechanism to sweep them into a one-way trap.

<div class="toc-box">
  <strong>Contents</strong>
  <ul>
    <li><a class="jump-link" href="#client-pitch">Client Pitch</a></li>
    <li><a class="jump-link" href="#functional-prototype">Functional Prototype</a></li>
  </ul>
</div>

<div id="client-pitch" class="section-card">
  <h2>Client Pitch</h2>

  <p>
    This milestone presents the original design concept, intended user need, and early validation plan for the spotted lanternfly trap.
  </p>

  <p>
    <a href="{{ '/assets/Batties_ClientPitch.pdf' | relative_url }}" target="_blank" rel="noopener">
      Open Client Pitch PDF
    </a>
  </p>

  <iframe
    src="{{ '/assets/Batties_ClientPitch.pdf' | relative_url }}"
    class="pdf-frame"
    loading="lazy">
  </iframe>
</div>

<div id="functional-prototype" class="section-card">
  <h2>Functional Prototype</h2>

  <h3>Purpose of the Prototype</h3>
  <p>
    The functional prototype was built to test whether a rotating fan-and-platform mechanism could move spotted lanternfly-sized objects into collection slots while maintaining smooth motion and acceptable mechanical clearance.
  </p>

  <h3>What Was Tested</h3>
  <ul>
    <li>Whether the fan moved smoothly through the bristled regions</li>
    <li>Whether the system could operate in the target low-speed range</li>
    <li>Whether friction between the fan and plate was manageable</li>
    <li>Whether bending or warping affected the mechanism</li>
    <li>Whether SLF-sized objects could actually be moved into the trap openings</li>
  </ul>

  <h3>Outcome</h3>
  <p>
    The prototype showed that the concept can move SLF-sized objects, but the wooden construction created important limitations. The fan required substantially more force to move through the bristled regions than through flat regions, indicating that the motion was not yet smooth enough. Manual cranking demonstrated that low-speed operation was possible, but motor testing was postponed. We also observed friction, bending, and spacing issues that affected reliability and capture efficiency.
  </p>

  <p>
    Based on these results, the next design iteration will likely replace wood with more precise or flexible materials, improve bristle geometry and spacing, and add better structural support such as a bearing.
  </p>

  <p>
    <a href="{{ '/assets/ODP_5.pdf' | relative_url }}" target="_blank" rel="noopener">
      Open Functional Prototype PDF
    </a>
  </p>

  <iframe
    src="{{ '/assets/ODP_5.pdf' | relative_url }}"
    class="pdf-frame"
    loading="lazy">
  </iframe>
</div>