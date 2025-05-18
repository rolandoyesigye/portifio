<template>
  <div class="skills">
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
  </div>
</template>

<script setup>
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
</script>

<style scoped>
.skills {
  padding: 4rem 2rem;
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

h1 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 3rem;
  font-size: 2.5rem;
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
  transition: transform 0.3s ease, box-shadow 0.3s ease;
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

@media (max-width: 768px) {
  .skills-grid {
    justify-content: center;
  }
  
  .skill-card {
    width: 100%;
    max-width: 250px;
  }
}
</style>

