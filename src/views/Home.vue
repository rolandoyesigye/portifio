<script setup>
import heroImage from '@/assets/roland.png'
import { ref } from 'vue'

const activeSection = ref('home')

const scrollToSection = (section) => {
  activeSection.value = section
  const element = document.getElementById(section)
  element?.scrollIntoView({ behavior: 'smooth' })
}

// Projects data
const projects = [
  {
    id: 1,
    title: 'E-Commerce Platform',
    description:
      'A full-stack e-commerce platform with user authentication, product management, and payment integration.',
    image: '/images/ecommerce.png',
    tags: ['Bootstrap', 'Flux', 'Laravel', 'Mysql', 'Stripe'],
    github: 'https://github.com/oyerol/ecommerce.git',
    demo: '',
  },
  {
    id: 2,
    title: 'Hospital Management System',
    description:
      'A collaborative hospital management application with real-time updates and team features.',
    image: '/images/hospital.png',
    tags: ['Bootstrap', 'Laravel', 'mysql', 'Material-UI'],
    github: 'https://github.com/oyerol/hospital.git',
    demo: '',
  },
  {
    id: 3,
    title: 'School Website',
    description:
      'A collaborative hospital management application with real-time updates and team features.',
    image: '/images/school.png',
    tags: ['Html', 'Css', 'Bootstrap'],
    github: 'https://github.com/oyerol/ntungamohighschool2.git',
    demo: ' https://oyerol.github.io/ntungamohighschool2',
  },
  {
    id: 4,
    title: 'Portfolio Website',
    description: 'A modern portfolio website built with Vue.js and Vite.',
    image: '/images/project3.jpg',
    tags: ['Vue.js', 'Vite', 'CSS3'],
    github: 'https://github.com/yourusername/portfolio',
    demo: 'https://portfolio-demo.com',
  },
]

// Skills data
const frontendSkills = [
  { name: 'HTML5', level: 95, icon: 'fab fa-html5' },
  { name: 'CSS3', level: 90, icon: 'fab fa-css3-alt' },
  { name: 'Bootstrap', level: 90, icon: 'fab fa-bootstrap' },
  { name: 'Tailwind CSS', level: 85, icon: 'fab fa-css3' },
  { name: 'JavaScript', level: 85, icon: 'fab fa-js' },
  { name: 'Vue.js', level: 70, icon: 'fab fa-vuejs' },
]

const backendSkills = [
  { name: 'PHP', level: 85, icon: 'fab fa-php' },
  { name: 'Laravel', level: 80, icon: 'fab fa-laravel' },
  { name: 'Python', level: 65, icon: 'fab fa-python' },
  { name: 'Java', level: 65, icon: 'fab fa-java' },
  { name: 'PostgreSQL', level: 75, icon: 'fas fa-database' },
  { name: 'SQL', level: 70, icon: 'fas fa-database' },
]

const toolsSkills = [
  { name: 'Git', level: 90, icon: 'fab fa-git-alt' },
  { name: 'Eclipse', level: 75, icon: 'fas fa-code' },
  { name: 'IntelliJ IDEA', level: 70, icon: 'fas fa-code' },
  { name: 'VS Code', level: 95, icon: 'fas fa-code' },
]

// Contact form data
const form = ref({
  name: '',
  email: '',
  subject: '',
  message: '',
})

const handleSubmit = () => {
  console.log('Form submitted:', form.value)
  form.value = {
    name: '',
    email: '',
    subject: '',
    message: '',
  }
}
</script>

<template>
  <div class="home">
    <!-- Navigation -->

    <!-- Home Section -->
    <section id="home" class="hero container-fluid">
      <div class="row align-items-center justify-content-center text-center text-sm-start">
        <div class="col-12 col-md-6 mb-4 mb-md-0">
          <img :src="heroImage" alt="Roland" class="img-fluid rounded hero-img" />
        </div>
        <div class="col-12 col-md-6 text-dark px-3">
          <h2 class="display-4 mb-4">Software Developer</h2>
          <p class="lead mb-5">Building innovative solutions with modern technologies</p>
          <div
            class="d-flex flex-column flex-sm-row gap-3 justify-content-center justify-content-md-start"
          >
            <button
              @click="scrollToSection('projects')"
              class="btn btn-outline-success btn-lg px-4"
            >
              View My Work
            </button>
            <button @click="scrollToSection('contact')" class="btn btn-outline-primary btn-lg px-4">
              Contact Me
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
      <div class="container">
        <h1>About Me</h1>
        <div class="about-content">
          <div class="about-text">
            <p>
              Oyesigye Roland is a passionate software developer with a strong focus on creating
              innovative and user-friendly applications. He enjoys solving complex problems and
              turning ideas into reality through code.
            </p>
            <p>
              With a background in software development, He has worked on various projects ranging
              from web applications to mobile apps. He is constantly learning and adapting to new
              technologies to stay at the forefront of software development.
            </p>
            <p>
              When he is not coding, you can find him exploring new technologies, contributing to
              open-source projects, or sharing my knowledge with the developer community.
            </p>
          </div>
          <div class="about-stats">
            <div class="stat-item">
              <h3>Years of Experience</h3>
              <p>2+</p>
            </div>
            <div class="stat-item">
              <h3>Projects Completed</h3>
              <p>6+</p>
            </div>
            <div class="stat-item">
              <h3>Happy Clients</h3>
              <p>10+</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="skills">
      <div class="container">
        <h1>My Skills</h1>
        <div class="skills-content">
          <div class="skills-category">
            <h2>Frontend Development</h2>
            <div class="skills-grid">
              <div v-for="skill in frontendSkills" :key="skill.name" class="skill-card">
                <div class="skill-icon">
                  <i :class="skill.icon"></i>
                </div>
                <h3>{{ skill.name }}</h3>
                <div class="skill-level">
                  <div class="progress-bar" :style="{ width: skill.level + '%' }"></div>
                </div>
              </div>
            </div>
          </div>

          <div class="skills-category">
            <h2>Backend Development</h2>
            <div class="skills-grid">
              <div v-for="skill in backendSkills" :key="skill.name" class="skill-card">
                <div class="skill-icon">
                  <i :class="skill.icon"></i>
                </div>
                <h3>{{ skill.name }}</h3>
                <div class="skill-level">
                  <div class="progress-bar" :style="{ width: skill.level + '%' }"></div>
                </div>
              </div>
            </div>
          </div>

          <div class="skills-category">
            <h2>Tools & Technologies</h2>
            <div class="skills-grid">
              <div v-for="skill in toolsSkills" :key="skill.name" class="skill-card">
                <div class="skill-icon">
                  <i :class="skill.icon"></i>
                </div>
                <h3>{{ skill.name }}</h3>
                <div class="skill-level">
                  <div class="progress-bar" :style="{ width: skill.level + '%' }"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="projects">
      <div class="container">
        <h1>My Projects</h1>
        <div class="projects-grid">
          <div v-for="project in projects" :key="project.id" class="project-card">
            <div class="project-image">
              <img :src="project.image" :alt="project.title" />
            </div>
            <div class="project-content">
              <h3>{{ project.title }}</h3>
              <p>{{ project.description }}</p>
              <div class="project-tags">
                <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
              </div>
              <div class="project-links">
                <a :href="project.github" target="_blank" class="btn">GitHub</a>
                <a :href="project.demo" target="_blank" class="btn">Live Demo</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact">
      <div class="container">
        <h1>Contact Me</h1>
        <div class="contact-content">
          <div class="contact-info">
            <h2>Get in Touch</h2>
            <p>
              I'm always open to discussing new projects, creative ideas, or opportunities to be
              part of your vision.
            </p>
            <div class="contact-details">
              <div class="contact-item">
                <i class="fas fa-envelope"></i>
                <span>rolandoyesigye39@gmail.com</span>
              </div>
              <div class="contact-item">
                <i class="fas fa-phone"></i>
                <span>+256 783 892 220</span>
              </div>
              <div class="contact-item">
                <i class="fas fa-map-marker-alt"></i>
                <span>Kampala Uganda</span>
              </div>
            </div>
            <div class="social-links">
              <a href="https://github.com/oyerol" class="social-link"
                ><i class="fab fa-github"></i
              ></a>
              <a href="https://www.linkedin.com/in/oyesigye-roland-1aab9633b/" class="social-link"
                ><i class="fab fa-linkedin"></i
              ></a>
              <a href="https://x.com/OyesigyeRoland" class="social-link"
                ><i class="fab fa-x-twitter"></i
              ></a>
            </div>
          </div>
          <div class="contact-form">
            <form @submit.prevent="handleSubmit">
              <div class="form-group">
                <label for="name">Name</label>
                <input type="text" id="name" v-model="form.name" required />
              </div>
              <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" v-model="form.email" required />
              </div>
              <div class="form-group">
                <label for="subject">Subject</label>
                <input type="text" id="subject" v-model="form.subject" required />
              </div>
              <div class="form-group">
                <label for="message">Message</label>
                <textarea id="message" v-model="form.message" rows="5" required></textarea>
              </div>
              <button type="submit" class="submit-btn">Send Message</button>
            </form>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
/* Hero Section */
.hero {
  width: 100vw;
  min-height: 100vh;
  padding: 2rem 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 56px;
}

.hero-img {
  max-width: 100%;
  height: auto;
  border-radius: 1rem;
  object-fit: cover;
}

/* About Section */
.about {
  padding: 4rem 2rem;
  width: 100vw;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.about-text p {
  margin-bottom: 1.5rem;
  line-height: 1.6;
  color: #4a5568;
}

.about-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.stat-item {
  text-align: center;
  padding: 2rem;
  background-color: #f7fafc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.stat-item h3 {
  color: #2c3e50;
  margin-bottom: 1rem;
  font-size: 1.2rem;
}

.stat-item p {
  color: #42b983;
  font-size: 2rem;
  font-weight: bold;
}

/* Skills Section */
.skills {
  padding: 4rem 2rem;
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.skills-content {
  display: flex;
  flex-direction: column;
  gap: 4rem;
  align-items: center;
}

.skills-category {
  width: 100%;
  max-width: 900px;
}

.skills-category h2 {
  color: #2c3e50;
  margin-bottom: 2rem;
  font-size: 1.8rem;
  text-align: center;
}

.skills-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2rem;
}

.skill-card {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
  width: 200px;
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.skill-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}

.skill-icon {
  font-size: 2.5rem;
  color: #42b983;
  margin-bottom: 1rem;
}

.skill-card h3 {
  color: #2c3e50;
  margin-bottom: 1rem;
  font-size: 1.2rem;
}

.skill-level {
  background-color: #e2e8f0;
  height: 8px;
  border-radius: 4px;
  overflow: hidden;
}

.progress-bar {
  height: 100%;
  background-color: #42b983;
  border-radius: 4px;
  transition: width 0.3s ease;
}

/* Projects Section */
.projects {
  padding: 4rem 2rem;
}

.projects-grid {
  display: flex;
  overflow-x: auto;
  gap: 2rem;
  padding-bottom: 1rem;
}

.project-card {
  background: rgb(245, 241, 241);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  max-width: 350px;
  flex-shrink: 0;
}

.project-card:hover {
  transform: translateY(-5px);
}

.project-image {
  width: 100%;
  height: 200px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.project-content {
  padding: 1.5rem;
}

.project-content h3 {
  color: #2c3e50;
  margin-bottom: 1rem;
  font-size: 1.5rem;
}

.project-content p {
  color: #4a5568;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tag {
  background-color: #e2e8f0;
  color: #4a5568;
  padding: 0.25rem 0.75rem;
  border-radius: 15px;
  font-size: 0.875rem;
}

.project-links {
  display: flex;
  gap: 1rem;
}

.btn {
  padding: 0.5rem 1rem;
  background-color: #42b983;
  color: white;
  text-decoration: none;
  border-radius: 4px;
  font-weight: 500;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #3aa876;
}

/* Contact Section */
.contact {
  padding: 4rem 2rem;
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
}

.contact-info {
  padding: 2rem;
  background-color: #f7fafc;
  border-radius: 8px;
}

.contact-info h2 {
  color: #2c3e50;
  margin-bottom: 1rem;
  font-size: 1.8rem;
}

.contact-info p {
  color: #4a5568;
  margin-bottom: 2rem;
  line-height: 1.6;
}

.contact-details {
  margin-bottom: 2rem;
}

.contact-item {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.contact-item i {
  color: #42b983;
  margin-right: 1rem;
  font-size: 1.2rem;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  color: #2c3e50;
  font-size: 1.5rem;
  transition: color 0.3s ease;
}

.social-link:hover {
  color: #42b983;
}

.contact-form {
  padding: 2rem;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.form-group {
  margin-bottom: 1.5rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  color: #2c3e50;
  font-weight: 500;
}

input,
textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #e2e8f0;
  border-radius: 4px;
  font-size: 1rem;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #42b983;
}

.submit-btn {
  width: 100%;
  padding: 1rem;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.submit-btn:hover {
  background-color: #3aa876;
}

/* Common Styles */
.container {
  max-width: 1200px;
  margin: 0 auto;
}

h1 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 3rem;
  font-size: 2.5rem;
}

/* Responsive Styles */
@media (max-width: 768px) {
  .about-content,
  .contact-content {
    grid-template-columns: 1fr;
  }

  .about-stats {
    grid-template-columns: 1fr;
  }

  .skills-grid {
    justify-content: center;
  }

  .skill-card {
    width: 100%;
    max-width: 250px;
  }

  .hero h1 {
    font-size: 2.5rem;
  }

  .hero h2 {
    font-size: 1.8rem;
  }

  .hero p {
    font-size: 1rem;
  }
}
</style>
