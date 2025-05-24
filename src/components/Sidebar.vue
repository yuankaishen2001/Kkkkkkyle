<script setup>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faRankingStar, faFilePdf, faUniversity, faEnvelope } from '@fortawesome/free-solid-svg-icons'
import { faGoogleScholar, faGithub, faLinkedin, faInstagram, faXTwitter } from '@fortawesome/free-brands-svg-icons'
import { useRouter } from 'vue-router'

const router = useRouter()

const SocialMedia = [
  { name: 'Google Scholar', icon: faGoogleScholar, color: '#4A90E2', url: 'https://scholar.google.com/citations?user=2QyPdfgAAAAJ&hl=en' },
  { name: 'GitHub', icon: faGithub, color: '#333', url: 'https://github.com/RolandMinrui' },
  { name: 'LinkedIn', icon: faLinkedin, color: '#0077B5', url: 'https://www.linkedin.com/in/minrui-xu-531b30242/' },
  { name: 'CV', icon: faFilePdf, color: '#2E7D32', url: '#', isRouter: true },
  // { name: 'X', icon: faXTwitter, color: '#000000' },
  { name: 'Instagram', icon: faInstagram, 
    color: 'linear-gradient(45deg, #405DE6, #5851DB, #833AB4, #C13584, #E1306C, #FD1D1D, #F56040, #F77737, #FCAF45, #FFDC80)' },
];

const News = [
  {
    date: '2025.05',
    content: 'One paper accepted to ACL 2025!',
  },
  {
    date: '2024.10',
    content: 'One paper accepted to MATH-AI Workshop at NeurIPS 2024!',
  },
  {
    date: '2024.09',
    content: 'One paper accepted to EMNLP 2024!',
  },
  {
    date: '2024.07',
    content: 'One paper accepted to UIST 2024!',
  },
];
</script>


<template>
  <aside class="sidebar">
    <!-- Profile Card -->
    <div class="profile-section">
      <img src="@/assets/profile/profile_life.jpg" alt="Profile Photo">
      <h3 style="margin: 0 0 1rem 0; color: #2c3e50; font-size: 1.5rem;">Minrui Xu</h3>
      <div>
        <FontAwesomeIcon :icon="faUniversity" />
        <p style="margin: 0; font-size: 1.2rem;">HKUST, Hong Kong</p>
      </div>
      <div>
        <FontAwesomeIcon :icon="faEnvelope" />
        <p style="margin: 0; font-size: 1.2rem;">mxubh@connect.ust.hk</p>
      </div>
    </div>

    <!-- Social Media -->
    <div class="sidebar-card social-section">
      <div class="social-links">
        <a 
          v-for="link in SocialMedia" 
          :key="link.name"
          :href="link.isRouter ? undefined : (link.url || '#')" 
          class="tooltip-wrapper" 
          :title="link.name"
          :style="{ background: link.color }"
          :target="link.isRouter ? undefined : '_blank'"
          :rel="link.isRouter ? undefined : 'noopener noreferrer'"
          @click="link.isRouter ? router.push(link.url) : undefined"
        >
          <FontAwesomeIcon :icon="link.icon" />
        </a>
      </div>
    </div>

    <!-- News -->
    <div class="sidebar-card news-section">
      <h3>News
        <FontAwesomeIcon :icon="faRankingStar" style="color: #4fc08d"/>
      </h3>
      <div v-for="item in News" :key="item.date" class="news-item">
        <div style="font-size: 1rem; color: #4fc08d; font-weight: 600; margin-bottom: 0.25rem;">{{ item.date }}</div>
        <div style="font-size: 1.1rem; line-height: 1.4;">{{ item.content }}</div>
      </div>
    </div>
  </aside>
</template>


<style scoped>
/* Basic */
.sidebar {
  width: 35%;
  padding: 1.5rem;
  background-color: #f8f9fa;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  overflow-y: auto;
  height: 92vh;
  box-sizing: border-box;
}

.sidebar-card {
  background: white;
  border-radius: 8px;
  padding: 1rem;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

/* Profile Card */
.profile-section {
  text-align: center;
  padding: 1rem;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
  position: relative;
}

.profile-section img {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid #4fc08d;
  margin-bottom: 1.5rem;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
  position: relative;
}

.profile-section img::after {
  content: "Jeju Island, 2025";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: rgba(0, 0, 0, 0.7);
  color: white;
  padding: 8px 12px;
  border-radius: 4px;
  font-size: 0.9rem;
  opacity: 0;
  transition: opacity 0.3s ease;
  pointer-events: none;
}

.profile-section img:hover::after {
  opacity: 1;
}

.profile-section img:hover {
  transform: scale(1.2);
}

.profile-section > div {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  margin-bottom: 0.75rem;
}

/* Social Media */
.social-section {
  text-align: center;
}

.social-section h4 {
  margin-top: 0;
  margin-bottom: 1rem;
  color: #2c3e50;
}

.social-links {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.tooltip-wrapper {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  color: white;
  font-size: 1.1rem;
  transition: transform 0.2s;
  position: relative;
}

.tooltip-wrapper:hover {
  transform: translateY(-5px);
}

.tooltip-wrapper::after {
  content: attr(title);
  position: absolute;
  bottom: -30px;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0, 0, 0, 0.8);
  color: white;
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 0.8rem;
  white-space: nowrap;
  z-index: 1000;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.2s, visibility 0.2s;
}

.tooltip-wrapper::before {
  content: '';
  position: absolute;
  bottom: -6px;
  left: 50%;
  transform: translateX(-50%);
  border-width: 4px;
  border-style: solid;
  border-color: transparent transparent rgba(0, 0, 0, 0.8) transparent;
  z-index: 1000;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.2s, visibility 0.2s;
}

.tooltip-wrapper:hover::after,
.tooltip-wrapper:hover::before {
  opacity: 1;
  visibility: visible;
}

.tooltip-wrapper svg {
  width: 1em;
  height: 1em;
  vertical-align: middle;
}

/* News */
.news-item {
  margin-bottom: 0.6rem;
  padding-bottom: 0.6rem;
  border-bottom: 1px solid #eee;
}

.news-item:hover {
  background: #f8f8f8;
  color: #4fc08d;
  transition: all 0.3s ease;
}

.news-item:last-child {
  margin-bottom: 0;
  padding-bottom: 0;
  border-bottom: none;
}

/* Responsive Design */
@media (max-width: 1024px) {
  .sidebar {
    width: 100%;
    min-width: 25%;
    height: auto;
    flex-direction: row;
    flex-wrap: wrap;
    padding: 1rem;
  }

  .sidebar-card {
    flex: 1 1 300px;
    min-width: 250px;
    margin: 0.5rem;
  }

  .profile-section {
    padding: 1.5rem;
  }

  .profile-photo img {
    width: 100px;
    height: 100px;
    margin-bottom: 1rem;
  }

  .profile-info h3 {
    font-size: 1.2rem;
    margin-bottom: 0.75rem;
  }

  .info-item {
    margin-bottom: 0.5rem;
  }

  .social-links {
    justify-content: center;
  }
}

@media (max-width: 600px) {
  .profile-section {
    flex-direction: column;
    text-align: center;
  }

  .sidebar-card {
    flex: 1 1 100%;
  }
}
</style>