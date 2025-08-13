<template>
  <section class="section education" id="education">
    <div class="container">
      <h2 class="section-title">Education</h2>
      <div class="education-grid">
        <div 
          v-for="(education, index) in educationList" 
          :key="index" 
          class="education-card"
        >
          <div class="education-icon">
            <svg width="40" height="40" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12,3L1,9L12,15L21,10.09V17H23V9M5,13.18V17.18L12,21L19,17.18V13.18L12,17L5,13.18Z" />
            </svg>
          </div>
          <div class="education-info">
            <h3 class="degree">{{ education.degree }}</h3>
            <h4 class="institution">{{ education.institution }}</h4>            
            <p class="graduation-date">{{ education.graduationDate }}</p>
            <p v-if="education.gpa" class="gpa">GPA: {{ education.gpa }}</p>
            <p v-if="education.description" class="description">{{ education.description }}</p>
            <div v-if="education.achievements" class="achievements">
              <h5>Key Achievements:</h5>
              <ul>
                <li v-for="achievement in education.achievements" :key="achievement">
                  {{ achievement }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      
      <!-- <div class="certifications">
        <h3 class="certifications-title">Certifications & Courses</h3>
        <div class="certifications-list">
          <div 
            v-for="(cert, index) in certifications" 
            :key="index" 
            class="certification-item"
          >
            <h4>{{ cert.name }}</h4>
            <span class="cert-issuer">{{ cert.issuer }}</span>
            <span class="cert-year">{{ cert.year }}</span>
          </div>
        </div>
      </div> -->
    </div>
  </section>
</template>

<script setup>
import { reactive } from 'vue'

const educationList = reactive([
  {
    degree: 'Bachelor of Computer Science',
    institution: 'University of Bunda Mulia',
    major: 'Information System',
    graduationDate: 'July 2018',
    gpa: '3.32/4.0',
    description: 'Specialized in software engineering and web development technologies.',    
  }
])

// const certifications = reactive([
//   {
//     name: 'AWS Certified Developer',
//     issuer: 'Amazon Web Services',
//     year: '2023'
//   },
//   {
//     name: 'Google Cloud Professional',
//     issuer: 'Google Cloud',
//     year: '2022'
//   },
//   {
//     name: 'Vue.js Certification',
//     issuer: 'Vue School',
//     year: '2021'
//   },
//   {
//     name: 'JavaScript Algorithms and Data Structures',
//     issuer: 'freeCodeCamp',
//     year: '2020'
//   }
// ])
</script>

<style scoped>
.education {
  background-color: var(--bg-primary);
}

.education-grid {
  display: grid;
  gap: 2rem;
  max-width: 800px;
  margin: 0 auto 4rem;
}

.education-card {
  background-color: var(--bg-tertiary);
  border: 1px solid var(--border-primary);
  border-radius: 12px;
  padding: 2rem;
  display: flex;
  align-items: flex-start;
  gap: 2rem;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.education-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.education-icon {
  color: var(--accent-primary);
  flex-shrink: 0;
}

.education-info {
  flex: 1;
}

.degree {
  font-size: 1.3rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.institution {
  font-size: 1.1rem;
  font-weight: 500;
  color: var(--accent-primary);
  margin-bottom: 0.5rem;
}

.graduation-date {
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
}

.gpa {
  font-weight: 500;
  color: var(--success);
  margin-bottom: 1rem;
}

.description {
  color: var(--text-tertiary);
  line-height: 1.6;
  margin-bottom: 1rem;
}

.achievements h5 {
  color: var(--text-primary);
  margin-bottom: 0.5rem;
  font-size: 1rem;
}

.achievements ul {
  list-style: none;
  padding: 0;
}

.achievements li {
  position: relative;
  padding-left: 1.5rem;
  margin-bottom: 0.3rem;
  color: var(--text-secondary);
}

.achievements li::before {
  content: '🏆';
  position: absolute;
  left: 0;
  font-size: 0.9rem;
}

.certifications {
  max-width: 800px;
  margin: 0 auto;
}

.certifications-title {
  font-size: 1.8rem;
  font-weight: 600;
  text-align: center;
  margin-bottom: 2rem;
  color: var(--text-primary);
}

.certifications-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.certification-item {
  background-color: var(--bg-secondary);
  border: 1px solid var(--border-primary);
  border-radius: 8px;
  padding: 1.5rem;
  text-align: center;
  transition: transform 0.2s ease;
}

.certification-item:hover {
  transform: scale(1.02);
  border-color: var(--accent-primary);
}

.certification-item h4 {
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.cert-issuer {
  display: block;
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
}

.cert-year {
  display: inline-block;
  background-color: var(--accent-secondary);
  color: white;
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: 500;
}

@media (max-width: 768px) {
  .education-card {
    flex-direction: column;
    gap: 1rem;
    padding: 1.5rem;
  }
  
  .education-icon {
    align-self: center;
  }
  
  .certifications-list {
    grid-template-columns: 1fr;
  }
}
</style>