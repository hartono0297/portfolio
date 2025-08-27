<template>
  <section class="section resume" id="resume">
    <div class="container">
      <h2 class="section-title">Resume</h2>
      <div class="resume-content">
        <div class="resume-text">
          <h3>Download My Complete Resume</h3>
          <p>
            Get a comprehensive overview of my professional experience, education, 
            and technical skills. The PDF includes detailed project descriptions 
            and achievements throughout my career.
          </p>
          <div class="resume-stats">
            <div class="stat">
              <span class="stat-number">4+</span>
              <span class="stat-label">Years Experience</span>
            </div>
            <div class="stat">
              <span class="stat-number">20+</span>
              <span class="stat-label">Tasks/Projects Completed</span>
            </div>
            <div class="stat">
              <span class="stat-number">∞</span>
              <span class="stat-label">Hot Coffees</span>
            </div>
          </div>
        </div>
        <div class="resume-action">
          <div class="resume-preview">
            <div class="preview-document">
              <div class="document-header">
                <div class="document-title">Hartono</div>
                <div class="document-subtitle">Full-Stack Developer</div>
              </div>
              <div class="document-content">
                <div class="document-line"></div>
                <div class="document-line short"></div>
                <div class="document-line"></div>
                <div class="document-line medium"></div>
              </div>
            </div>
          </div>
          <button @click="downloadResume" class="btn btn-primary download-btn">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
              <path d="M14,2H6A2,2 0 0,0 4,4V20A2,2 0 0,0 6,22H18A2,2 0 0,0 20,20V8L14,2M18,20H6V4H13V9H18V20Z" />
            </svg>
            Download Resume (PDF)
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const downloadResume = () => {
  // In a real application, this would download the actual PDF
  // For demo purposes, we'll create a sample download
  const link = document.createElement('a')
  link.href = 'https://drive.google.com/file/d/1mdnUkH8-fBqOnquUm9RDet03v9XF9ROU/view?usp=sharing'
  link.target = '_blank'
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)
}
</script>

<style scoped>
.resume {
  background-color: var(--bg-primary);
}

.resume-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  max-width: 1000px;
  margin: 0 auto;
}

.resume-text h3 {
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: var(--text-primary);
}

.resume-text p {
  font-size: 1.1rem;
  color: var(--text-tertiary);
  line-height: 1.6;
  margin-bottom: 2rem;
}

.resume-stats {
  display: flex;
  gap: 2rem;
}

.stat {
  text-align: center;
}

.stat-number {
  display: block;
  font-size: 2rem;
  font-weight: 700;
  color: var(--accent-primary);
}

.stat-label {
  font-size: 0.9rem;
  color: var(--text-secondary);
}

.resume-action {
  text-align: center;
}

.resume-preview {
  margin-bottom: 2rem;
  display: flex;
  justify-content: center;
}

.preview-document {
  width: 200px;
  height: 260px;
  background-color: var(--bg-tertiary);
  border: 1px solid var(--border-primary);
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s ease;
}

.preview-document:hover {
  transform: scale(1.05);
}

.document-header {
  text-align: center;
  margin-bottom: 20px;
}

.document-title {
  font-size: 1rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 4px;
}

.document-subtitle {
  font-size: 0.8rem;
  color: var(--text-secondary);
}

.document-content {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.document-line {
  height: 3px;
  background-color: var(--border-primary);
  border-radius: 2px;
}

.document-line.short {
  width: 60%;
}

.document-line.medium {
  width: 80%;
}

.download-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1.1rem;
  padding: 16px 32px;
  margin: 0 auto;
}

.download-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(88, 166, 255, 0.3);
}

@media (max-width: 768px) {
  .resume-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }
  
  .resume-stats {
    justify-content: center;
  }
  
  .resume-text h3 {
    font-size: 1.8rem;
  }
}
</style>