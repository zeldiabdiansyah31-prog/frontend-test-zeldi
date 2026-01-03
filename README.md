# Technical Test – Junior Frontend Developer

## Project Overview
This project is a technical test for the **Junior Frontend Developer** position at **Summit Global Teknologi**.

The goal of this test is to recreate the scroll-based experience from the reference Webflow website using **Vue.js 2 (Options API)**, **SASS**, and **GSAP ScrollTrigger**, focusing on smooth animations, pinned sections, and clean component structure.

Reference website:  
https://tr-scroll-toggle.webflow.io/

---

## Technologies Used
- Vue.js 2 (Options API)
- Vue CLI
- SASS / SCSS
- GSAP (GreenSock Animation Platform)
- GSAP ScrollTrigger Plugin

---

## Features
- Modular component-based architecture
- Scroll-based animations using GSAP ScrollTrigger
- Pinned section with step-by-step scroll interaction
- Smooth and performant animations
- Responsive layout (desktop, tablet, mobile)
- Clean and readable code structure

---

## Project Structure
```text
frontend-test-zeldi/
├─ public/
│  └─ index.html
├─ src/
│  ├─ assets/
│  │  ├─ images/
│  │  └─ styles/
│  │     └─ main.scss
│  ├─ components/
│  │  ├─ Header.vue
│  │  ├─ HeroSection.vue
│  │  ├─ AboutSection.vue
│  │  ├─ FeatureSection.vue
│  │  ├─ ScrollExperience.vue
│  │  └─ FooterSection.vue
│  ├─ pages/
│  │  └─ Index.vue
│  ├─ App.vue
│  └─ main.js
├─ .gitignore
├─ babel.config.js
├─ jsconfig.json
├─ package.json
├─ vue.config.js
└─ README.md
