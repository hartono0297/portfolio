<template>
  <section class="section work-experience" id="work-experience">
    <div class="container">
      <h2 class="section-title">Work Experience</h2>
      <div class="timeline">
        <div 
          v-for="(experience, index) in workExperience" 
          :key="index" 
          class="timeline-item"
        >
          <div class="timeline-marker"></div>
          <div class="timeline-content">
            <div class="experience-header">
              <h3 class="job-title">{{ experience.title }}</h3>
              <span class="job-period">{{ experience.period }}</span>
            </div>
            <h4 class="company-name">{{ experience.company }}</h4>
            <p class="job-description">{{ experience.description }}</p>
            <ul class="responsibilities">
              <li v-for="responsibility in experience.responsibilities" :key="responsibility">
                {{ responsibility }}
              </li>
            </ul>
            <div class="technologies">
              <span 
                v-for="tech in experience.technologies" 
                :key="tech" 
                class="tech-tag"
              >
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive } from 'vue'

const workExperience = reactive([
  {
    title: 'IT-Developer',
    company: 'PT. Mega Central Finance',
    period: '2022 - Present',
    description: 'Develop and maintain web applications using modern ASP.NET technologies.',
    responsibilities: [
      'Developed an automated calculation process using stored procedures to streamline data processing.',
      'Assessed user requirements and developed a solution by creating both technical and functional designs.',
      'Defined system test to ensure the program operates as expected under normal conditions.',
      'Troubleshooting errors and bugs to enhance and optimize application performance.',
      'Collaborated with the project manager to discuss and align on project details and progress.',
      'Migrated a console application from .NET Framework to .NET Core 8, improving performance and maintainability.'
    ],
    technologies: ['.NET', '.NET CORE', 'SQL Server', 'Entity Framework', 'MVC', 'JavaScript', 'HTML5', 'CSS3', 'Bootstrap', 'Git','GitLab', 'Postman', 'Swagger']
  },
  {
    title: 'IT-MIS',
    company: 'PT. Mega Central Finance',
    period: '2021 - 2022',
    description: 'Solving and providing data solutions for internal users',
    responsibilities: [
      'Responsible for providing data tailored to users specific requests',
      'Developing customized queries to meet their requirements',
      'Solving problems efficiently based on the challenges or issues they present',      
    ],
    technologies: ['SQL Server', 'Microsoft Sql Server Management Studio', 'Stored Procedure']
  }
])
</script>

<style scoped>
.work-experience {
  background-color: var(--bg-secondary);
}

.timeline {
  max-width: 800px;
  margin: 0 auto;
  position: relative;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 30px;
  top: 0;
  bottom: 0;
  width: 2px;
  background-color: var(--border-primary);
}

.timeline-item {
  position: relative;
  margin-bottom: 3rem;
  padding-left: 80px;
}

.timeline-marker {
  position: absolute;
  left: 22px;
  top: 8px;
  width: 16px;
  height: 16px;
  background-color: var(--accent-primary);
  border-radius: 50%;
  border: 3px solid var(--bg-secondary);
}

.timeline-content {
  background-color: var(--bg-tertiary);
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid var(--border-primary);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.timeline-content:hover {
  transform: translateX(10px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.experience-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 0.5rem;
  flex-wrap: wrap;
  gap: 1rem;
}

.job-title {
  font-size: 1.4rem;
  font-weight: 600;
  color: var(--text-primary);
}

.job-period {
  background-color: var(--bg-primary);
  color: var(--accent-primary);
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 500;
  border: 1px solid var(--border-primary);
}

.company-name {
  font-size: 1.1rem;
  font-weight: 500;
  color: var(--accent-primary);
  margin-bottom: 1rem;
}

.job-description {
  color: var(--text-tertiary);
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.responsibilities {
  list-style: none;
  margin-bottom: 1.5rem;
}

.responsibilities li {
  position: relative;
  padding-left: 1.5rem;
  margin-bottom: 0.5rem;
  color: var(--text-secondary);
}

.responsibilities li::before {
  content: '▶';
  position: absolute;
  left: 0;
  color: var(--accent-primary);
  font-size: 0.8rem;
}

.technologies {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  background-color: var(--bg-primary);
  color: var(--text-primary);
  padding: 4px 12px;
  border-radius: 16px;
  font-size: 0.8rem;
  border: 1px solid var(--border-primary);
}

@media (max-width: 768px) {
  .timeline::before {
    left: 20px;
  }
  
  .timeline-item {
    padding-left: 60px;
  }
  
  .timeline-marker {
    left: 12px;
  }
  
  .timeline-content {
    padding: 1.5rem;
  }
  
  .experience-header {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .job-title {
    font-size: 1.2rem;
  }
}
</style>