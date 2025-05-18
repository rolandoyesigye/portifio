<template>
  <div class="projects">
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
  </div>
</template>

<script setup>
const projects = [
  {
    id: 1,
    title: 'E-Commerce Platform',
    description:
      'A full-stack e-commerce platform with user authentication, product management, and payment integration.',
    image: '/images/project1.jpg',
    tags: ['Bootstrap','Flux', 'Laravel', 'Mysql', 'Stripe'],
    github: 'https://github.com/yourusername/ecommerce',
    demo: 'https://ecommerce-demo.com',
  },
  {
    id: 2,
    title: 'Hospital Management System',
    description:
      'A collaborative hospital management application with real-time updates and team features.',
    image: '/images/project2.jpg',
    tags: ['Bootsrap', 'Laravel','mysql', 'Material-UI'],
    github: 'https://github.com/yourusername/task-manager',
    demo: 'https://task-manager-demo.com',
  },
  {
    id: 2,
    title: 'School Website',
    description:
      'A collaborative hospital management application with real-time updates and team features.',
    image: '/images/school.png',
    tags: ['Bootsrap', 'Php','mysql'],
    github: 'https://github.com/yourusername/task-manager',
    demo: 'https://task-manager-demo.com',
  },
  {
    id: 3,
    title: 'Portfolio Website',
    description: 'A modern portfolio website built with Vue.js and Vite.',
    image: '/images/project3.jpg',
    tags: ['Vue.js', 'Vite', 'CSS3'],
    github: 'https://github.com/yourusername/portfolio',
    demo: 'https://portfolio-demo.com',
  },
]
</script>

<style scoped>
.projects {
  padding: 4rem 2rem;
}

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

.projects-grid {
  display: flex;
  overflow-x: auto;
  gap: 2rem;
  padding-bottom: 1rem;

}

.project-card {
  background: rgb(139, 135, 135);
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
</style>
