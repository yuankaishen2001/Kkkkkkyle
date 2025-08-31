<script setup>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faGraduationCap, faStar, faUser, faBook, faFileAlt, faCircleQuestion, faAward, faCheckCircle, faClipboardList, faSquareCheck, faCircle, faSquare	} from '@fortawesome/free-solid-svg-icons'
import { faGithub } from '@fortawesome/free-brands-svg-icons'
import HKUST  from '@/assets/institution/HKUST.png'
import TJU  from '@/assets/institution/TJU.png'
import Publication from '@/views/publication.vue'

const education = [
  {
    institution: "The Hong Kong University of Science and Technology (Guangzhou)",
    program: "PhD in Artificial Intelligence",
    time: "Sep 2025 - Present",
    logo: HKUST,
  },
  {
    institution: "Tianjin University",
    program: "MSc in Information and Communication Engineering",
    time: "Sep 2022 - Jan 2025",
    logo: TJU,
  },
  {
    institution: "Tianjin University",
    program: "BSc in Communication Engineering",
    time: "Sep 2018 - Jun 2022",
    logo: TJU,
  }
];
</script>

<template>
  <main class="main-content">
    <!-- Introduction -->
    <section>
      <div class="academic-header">
        <h2>
          <FontAwesomeIcon :icon="faUser" style="color: #4fc08d"/>
          Introduction
        </h2>
      </div>
      <p style="line-height: 1.5;">
        Welcome to my academic homepage! 👏
        My name is Kaishen Yuan (苑凯深). I am currently a first-year PhD candidate at the Hong Kong University of Science and Technology (Guangzhou), supervised by <a href="https://facultyprofiles.hkust-gz.edu.cn/faculty-personal-page?id=401" target="_blank" rel="noopener noreferrer">Prof. Yutao Yue</a>. 
        Prior to this, I obtained my Bachelor's and Master's degrees from Tianjin University in 2022 and 2025, respectively, with my Master's supervised by <a href="https://sites.google.com/view/xinliu/" target="_blank" rel="noopener noreferrer">Prof. Xin Liu</a>. 
        I also work closely with <a href="https://zitong-yu.github.io/yzt/" target="_blank" rel="noopener noreferrer">Prof. Zitong Yu</a> at Great Bay University.
      </p>
      <p style="line-height: 1.5;">
        My research interests primarily lie in <em>Affective Computing</em>, <em>Facial Analysis</em>, <em>Generative AI</em>.
      </p>
      <p style="line-height: 1.5;">
        If you see potential for collaboration, please don't hesitate to reach out.
      </p>
    </section>
    
    <!-- Education -->
    <section>
      <div class="academic-header">
        <h2>
          <FontAwesomeIcon :icon="faGraduationCap" style="color: #4fc08d"/> Education
        </h2>
      </div>
      <div v-for="edu in education" :key="edu.program" class="academic-block">
        <img :src="edu.logo" :alt="edu.institution + ' Logo'" class="academic-logo">
        <div class="academic-content">
          <h3>{{ edu.institution }}</h3>
          <p>{{ edu.program }}</p>
          <p class="time">{{ edu.time }}</p>
          <div class="academic-tags" v-if="edu.tags">
            <span v-for="tag in edu.tags" :key="tag" class="academic-tag">{{ tag }}</span>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Selected Publication -->
    <Publication :is_selected="true" />

    <section>
      <div class="academic-header">
        <h2>
          <FontAwesomeIcon :icon="faClipboardList" style="color: #4fc08d"/> Paper Review
        </h2>
      </div>
      <ul style="list-style-type: none; padding-left: 0;">
        <li>
          <FontAwesomeIcon :icon="faSquare" style="color: #4fc08d; font-size: 0.6rem;"/> 
          <span>&nbsp;&nbsp;Conferences: AAAI 26, NeurIPS 25, ICLR 25, ACM MM 25, ICME 25, IJCB 24</span>
        </li>
        <li>
          <FontAwesomeIcon :icon="faSquare" style="color: #4fc08d; font-size: 0.6rem;"/> 
          <span>&nbsp;&nbsp;Journals: IEEE Transactions on Knowledge and Data Engineering (IEEE TKDE), The Visual Computer (TVC)</span>
        </li>
      </ul>
    </section>


    <!-- Honors & Awards -->
    <section>
      <div class="academic-header">
        <h2>
          <FontAwesomeIcon :icon="faAward" style="color: #4fc08d"/> Honors & Awards
        </h2>
      </div>
      <ul style="list-style-type: none; padding-left: 0;">
        <li>
          <FontAwesomeIcon :icon="faCircle" style="color: #4fc08d; font-size: 0.6rem;"/> 
          <span>&nbsp;&nbsp;Tianjin University Academic Scholarship (Three times)</span>
        </li>
        <li>
          <FontAwesomeIcon :icon="faCircle" style="color: #4fc08d; font-size: 0.6rem;"/> 
          <span>&nbsp;&nbsp;Tianjin University Meritorious Student Scholarship (Three times)</span>
        </li>
        <li>
          <FontAwesomeIcon :icon="faCircle" style="color: #4fc08d; font-size: 0.6rem;"/> 
          <span>&nbsp;&nbsp;Tianjin University Outstanding Student Honor (Top 2%)</span>
        </li>
        <li>
          <FontAwesomeIcon :icon="faCircle" style="color: #4fc08d; font-size: 0.6rem;" /> 
          <span>&nbsp;&nbsp;Tianjin University Zhuang Bingchang Scholarship</span>
        </li>
      </ul>
    </section>

  </main>
</template>