<template>
  <section class="section skills" id="skills">
    <div class="container">
      <h2 class="section-title">Skills & Technologies</h2>
      <div class="skills-grid">
        <div class="skill-category" v-for="category in skillCategories" :key="category.title">
          <h3 class="category-title">{{ category.title }}</h3>
          <ul class="skills-list">
            <li v-for="skill in category.skills" :key="skill" class="skill-item">
              {{ skill }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive } from 'vue'

const skillCategories = reactive([
  {
    title: 'Frontend',
    skills: [
      'Vue.js',      
      'JavaScript (ES6+)',
      'HTML5 & CSS3',
      'SCSS',
      'Tailwind CSS',
      'Bootstrap',
      'Vite'
    ]
  },
  {
    title: 'Backend',
    skills: [           
      'ASP.NET',
      '.NET Core',
      '.NET Framework',
      '.NET MVC',
      'SQL Server',      
      
      'Entity Framework',   
    ]
  },
  {
    title: 'Tools',
    skills: [
      'Git & GitHub',
      'GitLab',      
      'AWS',
      'Visual Studio', 
      'VS Code',
      'Postman'      
    ]
  },
  {
    title: 'Architecture',
    skills: [
      'RESTful APIs',
      'Clean Architecture',
      'MVC Pattern'
    ]
  }
])
</script>

<style scoped>
.skills {
  background-color: var(--bg-secondary);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 3rem;  
  max-width: 1000px;  
  margin: 0 auto;
}

.skill-category {
  background-color: #161b22;
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid #30363d;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.skill-category:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.category-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--accent-primary);
  margin-bottom: 1.5rem;
  text-align: center;
  position: relative;
}

.category-title::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 50px;
  height: 3px;
  background-color: var(--accent-primary);
  border-radius: 2px;
}

.skills-list {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.skill-item {
  background-color: #21262d;
  color: #f0f6fc;
  padding: 0.6rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 500;
  border: 1px solid #30363d;
  transition: all 0.3s ease;
  cursor: default;
}

.skill-item:hover {
  background-color: var(--accent-secondary);
  border-color: var(--accent-secondary);
  color: white;
  transform: scale(1.05);
}

@media (max-width: 768px) {
  .skills-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .skill-category {
    padding: 1.5rem;
  }
}
</style>