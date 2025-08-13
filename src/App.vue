<template>
  <div id="app">
    <HeroSection />
    <SkillsSection />
    <ResumeSection />
    <ProjectsSection />
    <WorkExperienceSection />
    <EducationSection />
    <FooterSection />
  </div>
</template>

<script setup>
import HeroSection from './components/HeroSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ResumeSection from './components/ResumeSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import WorkExperienceSection from './components/WorkExperienceSection.vue'
import EducationSection from './components/EducationSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<style scoped>
#app {
  min-height: 100vh;
  background-color: #0d1117;
}
</style>