<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'
import { useRoute, useRouter } from 'vue-router'

// State to track scroll position and navbar visibility
const lastScrollTop = ref(0)
const navbarVisible = ref(false) // Initially hidden
const scrollThreshold = 100 // Show navbar after scrolling this many pixels
const activeSection = ref('home')
const route = useRoute()
const router = useRouter()

// Function to handle scroll events
const handleScroll = () => {
  const currentScrollTop = window.pageYOffset || document.documentElement.scrollTop

  // Show navbar after scrolling down past threshold
  if (currentScrollTop > scrollThreshold) {
    navbarVisible.value = true

    // Update active section based on scroll position
    if (route.path === '/') {
      updateActiveSection()
    }
  } else {
    // Hide navbar when at the top of the page
    navbarVisible.value = false
  }

  // Store last scroll position
  lastScrollTop.value = currentScrollTop <= 0 ? 0 : currentScrollTop
}

// Function to update active section based on scroll position
const updateActiveSection = () => {
  const sections = ['home', 'about', 'projects', 'skills', 'contact']

  for (const section of sections) {
    const element = document.getElementById(section)
    if (element) {
      const rect = element.getBoundingClientRect()
      // If the section is in view (with some buffer for better UX)
      if (rect.top <= 150 && rect.bottom >= 150) {
        activeSection.value = section
        break
      }
    }
  }
}

// Function to navigate to section
const navigateToSection = (section) => {
  activeSection.value = section

  if (route.path === '/') {
    // If already on home page, just scroll to the section
    scrollToSection(section)
  } else {
    // If on another page, navigate to home page first, then scroll
    router.push('/').then(() => {
      // Wait for navigation to complete and DOM to update
      setTimeout(() => {
        scrollToSection(section)
      }, 100)
    })
  }
}

// Function to scroll to a section
const scrollToSection = (section) => {
  const element = document.getElementById(section)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

// Computed property to determine if we're on the home page
const isHomePage = computed(() => {
  return route.path === '/'
})

// Set up and clean up scroll event listener
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <div class="app">
    <nav
      class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top"
      :class="{ 'navbar-hidden': !navbarVisible, 'navbar-visible': navbarVisible }"
    >
      <div class="container">
        <router-link class="navbar-brand" to="/">Oyesigye Roland</router-link>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item">
              <a
                href="#"
                class="nav-link"
                @click.prevent="navigateToSection('home')"
                :class="{ active: isHomePage && activeSection === 'home' }"
              >
                Home
              </a>
            </li>
            <li class="nav-item">
              <a
                href="#"
                class="nav-link"
                @click.prevent="navigateToSection('about')"
                :class="{
                  active:
                    (!isHomePage && $route.path === '/about') ||
                    (isHomePage && activeSection === 'about'),
                }"
              >
                About
              </a>
            </li>
            <li class="nav-item">
              <a
                href="#"
                class="nav-link"
                @click.prevent="navigateToSection('projects')"
                :class="{
                  active:
                    (!isHomePage && $route.path === '/projects') ||
                    (isHomePage && activeSection === 'projects'),
                }"
              >
                Projects
              </a>
            </li>
            <li class="nav-item">
              <a
                href="#"
                class="nav-link"
                @click.prevent="navigateToSection('skills')"
                :class="{
                  active:
                    (!isHomePage && $route.path === '/skills') ||
                    (isHomePage && activeSection === 'skills'),
                }"
              >
                Skills
              </a>
            </li>
            <li class="nav-item">
              <a
                href="#"
                class="nav-link"
                @click.prevent="navigateToSection('contact')"
                :class="{
                  active:
                    (!isHomePage && $route.path === '/contact') ||
                    (isHomePage && activeSection === 'contact'),
                }"
              >
                Contact
              </a>
            </li>
            <li class="nav-item">
              <a href="/Oyesigye Roland-cv.pdf" download class="btn btn-success ms-4">
                Download CV
              </a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <main class="main-content">
      <router-view></router-view>
    </main>

    <footer class="footer">
      <div class="container text-center">
        <p class="mb-2">
          &copy; {{ new Date().getFullYear() }} Oyesigye Roland.All rights reserved.
        </p>
        <div class="d-flex justify-content-center gap-3">
          <a
            href="https://github.com/rolandoyesigye"
            target="_blank"
            class="text-white text-decoration-none"
          >
            <i class="bi bi-github"></i> GitHub
          </a>
          <a
            href="https://www.linkedin.com/in/oyesigye-roland-1aab9633b/"
            target="_blank"
            class="text-white text-decoration-none"
          >
            <i class="bi bi-linkedin"></i> LinkedIn
          </a>
          <a href="mailto:rolandoyesigye39@gmail.com" class="text-white text-decoration-none">
            <i class="bi bi-envelope"></i> Email
          </a>
        </div>
      </div>
    </footer>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  height: 100%;
  width: 100%;
  overflow-x: hidden;
  margin: 0;
  padding: 0;
}

.app {
  min-height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
}

.navbar {
  background-color: #1e1f21 !important;
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.navbar-nav {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.navbar-hidden {
  transform: translateY(-100%);
  opacity: 0;
}

.navbar-visible {
  transform: translateY(0);
  opacity: 1;
}

.navbar-brand {
  font-size: 1.8rem;
  font-weight: 600;
  color: #ffffff !important;
}

.nav-link {
  color: #cccccc !important;
  font-weight: 400;
  position: relative;
  font-size: 1rem;
  transition: all 0.3s ease-in-out;
}

.nav-link:hover {
  color: #42b983 !important;
}

/* Add styles for active nav links */
.nav-link.active {
  color: #42b983 !important;
  font-weight: 600;
  position: relative;
}

.nav-link.active::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: #42b983;
  transition: width 0.3s ease;
}

.main-content {
  flex: 1;
  width: 100%;
  /* Remove top margin since navbar is initially hidden */
  margin-top: 0;
  min-height: 100vh;
  padding-bottom: 100px;
}
.footer {
  /* position: fixed; */
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: #212529;
  color: white;
  text-align: center;
  padding: 1rem 0;
  z-index: 1000;
  box-shadow: 0 -2px 5px rgba(0, 0, 0, 0.2);
}

/* Ensure content fits on screen */
html,
body {
  width: 100%;
  overflow-x: hidden;
}

/* Improve responsiveness */
@media (max-width: 768px) {
  .container {
    padding-left: 15px;
    padding-right: 15px;
  }

  .navbar-brand {
    font-size: 1.1rem;
  }

  .nav-link {
    padding: 0.5rem 0.75rem;
  }
}

/* Fix any overflow issues */
.row {
  margin-left: 0;
  margin-right: 0;
}

img {
  max-width: 100%;
  height: auto;
}
</style>
