<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title" ref="title">
            Hi, I'm <span class="accent">Hartono</span>
          </h1>
          <h2 class="hero-subtitle" ref="subtitle">            
            <span class="typewriter" :class="{ typing: isTyping }">{{ currentText }}</span>
          </h2>
          <p class="hero-description" ref="description">
            I craft modern web applications with clean code and intuitive user experiences. 
            Passionate about turning ideas into reality through technology.
          </p>
          <div class="hero-actions" ref="actions">
            <a href="#work-experience" @click.prevent="scrollToWorkExperience" class="btn btn-primary">View My Work</a>
            <a href="#contact" @click.prevent="scrollToContact" class="btn">Get In Touch</a>
          </div>
        </div>
        <div class="hero-visual">
          <div class="code-block float" ref="codeBlock">
            <div class="code-header">
              <div class="code-dots">
                <span></span>
                <span></span>
                <span></span>
              </div>
              <span class="code-title">developer.js</span>
            </div>
            <div class="code-content">
              <div class="code-line">
                <span class="code-keyword">const </span> 
                <span class="code-variable">developer</span> = {
              </div>
              <div class="code-line code-indent">
                <span class="code-property">name</span>: 
                <span class="code-string">'Hartono'</span>,
              </div>
              <div class="code-line code-indent">
                <span class="code-property">skills</span>: [
                <span class="code-string">'.Net'</span>, 
                <span class="code-string">'Vue.js'</span>,
                <span class="code-string">'SQL'</span>],
              </div>
              <div class="code-line code-indent">
                <span class="code-property">experience</span>: 
                <span class="code-number">4</span> + 
                <span class="code-string">' years'</span>,
              </div>
              <div class="code-line">}</div>
            </div>
          </div>
        </div>
      </div>
      <div class="scroll-indicator" ref="scrollIndicator">
        <span>Scroll Down</span>
        <div class="scroll-arrow">↓</div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const title = ref(null)
const subtitle = ref(null)
const description = ref(null)
const actions = ref(null)
const codeBlock = ref(null)
const scrollIndicator = ref(null)
const texts = ['Full-Stack Developer', '.NET Developer', 'Backend Enthusiast', 'Vue.js Enthusiast', 'SQL Server Developer'];
const typingSpeed = 100;
const pauseTime = 1500;
const deleteSpeed = 50;
const currentText = ref('');
const isTyping = ref(true);
const currentIndex = ref(0);

const typeWriter = () => {
  const text = texts[currentIndex.value];
  let i = 0;

  const type = () => {
    if (i < text.length) {
      currentText.value = text.substring(0, i + 1);
      i++;
      setTimeout(type, typingSpeed);
    } else {
      isTyping.value = false;
      setTimeout(() => {
        deleteText();
      }, pauseTime);
    }
  };

  type();
};

const deleteText = () => {
  let i = currentText.value.length;

  const deleteChar = () => {
    if (i > 0) {
      currentText.value = currentText.value.substring(0, i - 1);
      i--;
      setTimeout(deleteChar, deleteSpeed);
    } else {
      currentIndex.value = (currentIndex.value + 1) % texts.length;
      isTyping.value = true;
      setTimeout(() => {
        typeWriter();
      }, 200);
    }
  };

  deleteChar();
};

const scrollToWorkExperience = () => {
  const workExperienceSection = document.querySelector('#work-experience');
  if (workExperienceSection) {
    workExperienceSection.scrollIntoView({ behavior: 'smooth' });
  }
};

const scrollToContact = () => {
  const contactSection = document.querySelector('#contact');
  if (contactSection) {
    contactSection.scrollIntoView({ behavior: 'smooth' });
  }
};

onMounted(() => {
  // Animate elements on load
  typeWriter();
  const elements = [title, subtitle, description, actions, codeBlock, scrollIndicator]
  elements.forEach((el, index) => {
    if (el.value) {
      setTimeout(() => {
        el.value.classList.add('fade-in-up')
      }, index * 150)
    }
  })
})
</script>

<style scoped>
.typewriter {
  border-right: 2px solid #58a6ff;
  animation: blink 1s infinite;
}

.typewriter.typing {
  border-right: 2px solid #58a6ff;
}

@keyframes blink {
  0%, 50% { border-color: #58a6ff; }
  51%, 100% { border-color: transparent; }
}

.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  background: linear-gradient(135deg, var(--bg-primary) 0%, var(--bg-secondary) 100%);
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: radial-gradient(circle at 50% 50%, rgba(88, 166, 255, 0.1) 0%, transparent 50%);
  pointer-events: none;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  opacity: 0;
}

.hero-visual {
  display: flex;
  justify-content: center;
}


.accent {
  color: var(--accent-primary);
}

.hero-subtitle {
  font-size: 1.5rem;
  font-weight: 400;
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
  opacity: 0;
}

.hero-description {
  font-size: 1.1rem;
  color: var(--text-tertiary);
  margin-bottom: 2rem;
  line-height: 1.6;
  opacity: 0;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  opacity: 0;
}

.code-block {
  background-color: #0d1117;
  border: 1px solid #30363d;
  border-radius: 8px;
  overflow: hidden;
  width: 100%;
  max-width: 400px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
}

.code-header {
  background-color: var(--bg-secondary);
  padding: 12px 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid var(--border-primary);
}

.code-dots {
  display: flex;
  gap: 6px;
}

.code-dots span {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: var(--border-primary);
}

.code-dots span:nth-child(1) {
  background-color: #ff5f56;
}

.code-dots span:nth-child(2) {
  background-color: #ffbd2e;
}

.code-dots span:nth-child(3) {
  background-color: #27ca3f;
}

.code-title {
  font-size: 0.9rem;
  color: var(--text-tertiary);
}

.code-content {
  padding: 16px;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 0.9rem;
  line-height: 1.5;
}

.code-line {
  margin-bottom: 4px;
}

.code-indent {
  padding-left: 24px;
}

.code-keyword {
  color: #ff7b72;
}

.code-variable {
  color: var(--text-primary);
}

.code-property {
  color: #79c0ff;
}

.code-string {
  color: #a5d6ff;
}

.code-number {
  color: #79c0ff;
}

.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  text-align: center;
  color: var(--text-tertiary);
  font-size: 0.9rem;
  opacity: 0;
}

.scroll-arrow {
  margin-top: 0.5rem;
  animation: bounce 2s infinite;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-5px);
  }
  60% {
    transform: translateY(-3px);
  }
}

@media (max-width: 768px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }
  
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-subtitle {
    font-size: 1.2rem;
  }
  
  .hero-actions {
    justify-content: center;
    flex-wrap: wrap;
  }
  
  .code-block {
    order: -1;
  }

  .scroll-indicator {
    position: static;
    margin-top: 2rem;
  }
}
</style>