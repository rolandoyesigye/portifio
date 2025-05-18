<template>
  <div class="about">
    <div class="container">
      <h1>About Me</h1>
      <div class="about-content">
        <div class="about-text">
          <p>
            Oyesigye Roland is a passionate software developer with a strong focus on
            creating innovative and user-friendly applications. He enjoys solving complex problems and
            turning ideas into reality through code.
          </p>
          <p>
            With a background in software development, He has worked on various projects ranging from
            web applications to mobile apps. He is constantly learning and adapting to new
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
  </div>
</template>

<script setup>
// Component logic here
</script>

<style scoped>
.about {
  padding: 4rem 2rem;
  width: 100vw;
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

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
  }

  .about-stats {
    grid-template-columns: 1fr;
  }
}
</style>
