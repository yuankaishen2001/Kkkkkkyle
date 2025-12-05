<script setup>
// Font Awesome Icon
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faCircleQuestion, faSort, faSortUp, faSortDown, faBook, faFileAlt, faSearch } from '@fortawesome/free-solid-svg-icons'
import { faGithub } from '@fortawesome/free-brands-svg-icons'

// Publication Thumbnails
import AUFormer from '@/assets/publication/AUFormer.png'
import ANT from '@/assets/publication/ANT.png'
import AUTTT from '@/assets/publication/AUTTT.png'
import EmoLLAMA from '@/assets/publication/EmoLLAMA.png'
import FEALLM from '@/assets/publication/FEALLM.png'
import MedTVTR1 from '@/assets/publication/MedTVTR1.png'
import PeriodLLM from '@/assets/publication/PeriodLLM.png'
import SACL from '@/assets/publication/SACL.png'
import CoEmoGen from '@/assets/publication/CoEmoGen.png'
import AULLM from '@/assets/publication/AULLM.png'
import POLARIS from '@/assets/publication/POLARIS.png'


// Add reactive reference and computed property
import { ref, computed } from 'vue'

// Add prop definition
const props = defineProps({
  is_selected: {type: Boolean, default: false}
})

const search_query = ref('')
const sort_date = ref('none') // 'none', 'asc', 'desc'
const filtered_publication = computed(() => {
  let filtered = publication;
  
  // selected publication
  if (props.is_selected) {
    filtered = filtered.filter(pub => pub.selected);
  }

  // search bar
  if (search_query.value) {
    const query = search_query.value.toLowerCase();
    filtered = filtered.filter(pub => 
      pub.title.toLowerCase().includes(query)
    );
  }

  // sort by date
  if (sort_date.value === 'asc') {
    return [...filtered].reverse();
  } else if (sort_date.value === 'desc') {
    return filtered;
  }
  return filtered;
});

const publication = [
  {
    title: "POLARIS: Projection-Orthogonal Least Squares for Robust and Adaptive Inversion in Diffusion Models",
    author: "Wenshuo Chen, Haosen Li, Shaofeng Liang, Lei Wang, Haozhe Jia, <strong>Kaishen Yuan</strong>, Jiemin Wu, Bowen Tian, Yutao Yue",
    venue: "Arxiv",
    img: POLARIS,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2512.00369"},
      {button: "GitHub", logo: faGithub, link: "https://polaris-code-official.github.io/"}
    ],
    selected: true
  },
  {
    title: "CoEmoGen: Towards Semantically-Coherent and Scalable Emotional Image Content Generation",
    author: "<strong>Kaishen Yuan</strong>, Yuting Zhang, Shang Gao, Yijie Zhu, Wenshuo Chen, Yutao Yue",
    venue: "Arxiv",
    img: CoEmoGen,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2508.03535"},
      {button: "GitHub", logo: faGithub, link: "https://github.com/yuankaishen2001/CoEmoGen"}
    ],
    selected: true
  },
  {
    title: "MedTVT-R1: A Multimodal LLM Empowering Medical Reasoning and Diagnosis",
    author: "Yuting Zhang*, <strong>Kaishen Yuan</strong>*, Hao Lu, Yutao Yue, Jintai Chen, Kaishun Wu",
    venue: "Arxiv",
    img: MedTVTR1,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2506.18512"},
      {button: "GitHub", logo: faGithub, link: "https://github.com/keke-nice/MedTVT-R1"}
    ],
    selected: true
  },
  {
    title: "EMO-LLaMA: Enhancing Facial Emotion Understanding with Instruction Tuning",
    author: "Bohao Xing, Zitong Yu, Xin Liu, <strong>Kaishen Yuan</strong>, Qilang Ye, Weicheng Xie, Huanjing Yue, Jingyu Yang, Heikki Kälviäinen",
    venue: "Arxiv",
    img: EmoLLAMA,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2408.11424"},
      {button: "GitHub", logo: faGithub, link: "https://github.com/xxtars/EMO-LLaMA"}
    ],
    selected: false
  },
  {
    title: "AU-LLM: Micro-Expression Action Unit Detection via Enhanced LLM-Based Feature Fusion",
    author: "Zhishu Liu*, <strong>Kaishen Yuan</strong>*, Bo Zhao, Yong Xu, Zitong Yu",
    venue: "CCBR 2025",
    img: AULLM,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2507.21778"},
      {button: "GitHub", logo: faGithub, link: "https://github.com/ZS-liu-JLU/AU-LLMs"}
    ],
    selected: false
  },
  {
    title: "ANT: Adaptive Neural Temporal-Aware Text-to-Motion Model",
    author: "Wenshuo Chen, Kuimou Yu, Haozhe Jia, <strong>Kaishen Yuan</strong>, Bowen Tian, Songning Lai, Hongru Xiao, Erhang Zhang, Lei Wang, Yutao Yue",
    venue: "ACM MM 2025",
    img: ANT,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2506.02452"},
      {button: "GitHub", logo: faGithub, link: "https://github.com/CCSCovenant/ANT"}
    ],
    selected: false
  },
  {
    title: "FEALLM: Advancing Facial Emotion Analysis in Multimodal Large Language Models with Emotional Synergy and Reasoning",
    author: "Zhuozhao Hu*, <strong>Kaishen Yuan</strong>*†, Xin Liu, Zitong Yu, Yuan Zong, Jingang Shi, Huanjing Yue, Jingyu Yang",
    venue: "ACM MM 2025",
    img: FEALLM,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2505.13419"},
      {button: "GitHub", logo: faGithub, link: "https://github.com/953206211/FEALLM"}
    ],
    selected: true
  },
  {
    title: "AU-TTT: Vision Test-Time Training model for Facial Action Unit Detection",
    author: "Bohao Xing*, <strong>Kaishen Yuan</strong>*, Zitong Yu, Xin Liu, Heikki Kälviäinen",
    venue: "ICME 2025",
    img: AUTTT,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2503.23450"},
    ],
    selected: false
  },
  {
    title: "Period-LLM: Extending the Periodic Capability of Multimodal Large Language Model",
    author: "Yuting Zhang, Hao Lu, Qingyong Hu, Yin Wang, <strong>Kaishen Yuan</strong>, Xin Liu, Kaishun Wu",
    venue: "CVPR 2025",
    img: PeriodLLM,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhang_Period-LLM_Extending_the_Periodic_Capability_of_Multimodal_Large_Language_Model_CVPR_2025_paper.pdf"},
      {button: "GitHub", logo: faGithub, link: "https://github. com/keke-nice/Period-LLM"}
    ],
    selected: false
  },
  {
    title: "AUFormer: Vision Transformers are Parameter-Efficient Facial Action Unit Detectors",
    author: "<strong>Kaishen Yuan</strong>, Zitong Yu, Xin Liu, Weicheng Xie, Huanjing Yue, Jingyu Yang",
    venue: "ECCV 2024",
    img: AUFormer,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2403.04697"},
      {button: "GitHub", logo: faGithub, link: "https://github.com/yuankaishen2001/AUFormer"}
    ],
    selected: true
  },
  {
    title: "Multi-scale Promoted Self-adjusting Correlation Learning for Facial Action Unit Detection",
    author: "Xin Liu*, <strong>Kaishen Yuan</strong>*, Xuesong Niu, Jingang Shi, Zitong Yu, Huanjing Yue, Jingyu Yang",
    venue: "IEEE TAFFC 2024",
    img: SACL,
    buttons: [
      {button: "Paper", logo: faFileAlt, link: "https://arxiv.org/pdf/2308.07770"},
      {button: "GitHub", logo: faGithub, link: "https://github.com/yuankaishen2001/Self-adjusting-AU"}
    ],
    selected: true
  },
];
</script>

<template>
  <main :class="{ 'main-content': !props.is_selected }">
    <!-- Header -->
    <div class="academic-header">
      <h2>
        <FontAwesomeIcon :icon="faBook" style="color: #4fc08d"/> {{ props.is_selected ? 'Selected Publication' : 'Publication (*Equal Contribution, †Project Lead)' }}
      </h2>
      
      <div class="academic-header-toolbox">
        <!-- Search Bar -->
        <div class="search-bar">
          <FontAwesomeIcon :icon="faSearch" class="search-icon" />
          <input 
            type="text" 
            v-model="search_query" 
            placeholder="Search publications..." 
            class="search-input"
          />
        </div>

        <!-- Control Icons -->
        <div class="control-icons">
          <div class="tooltip">
            <FontAwesomeIcon :icon="faCircleQuestion" class="tooltip-icon control-icon" />
            <span class="tooltip-content">* denotes Equal Contribution</span>
          </div>

          <div class="tooltip">
            <FontAwesomeIcon 
              :icon="sort_date === 'asc' ? faSortUp : sort_date === 'desc' ? faSortDown : faSort" 
              class="tooltip-icon control-icon"
              @click="sort_date = sort_date === 'none' ? 'asc' : sort_date === 'asc' ? 'desc' : 'none'"
            />
            <span class="tooltip-content">Sort by date</span>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Publication -->
    <div v-for="pub in filtered_publication" :key="pub.title" class="academic-block">
      <div>
        <div class="academic-venue">{{ pub.venue }}</div>
        <a :href="pub.arxiv" target="_blank" rel="noopener noreferrer">
          <img :src="pub.img" :alt="pub.title + ' Thumbnail'" class="academic-img">
        </a>
      </div>
      <div class="academic-content">
        <h3>{{ pub.title }}</h3>
        <div class="academic-tags">
          <span v-for="tag in pub.tags" :key="tag" class="academic-tag">{{ tag }}</span>
        </div>
        <p class="program" v-html="pub.author"></p>
        <div class="academic-tags">
          <a v-for="button in pub.buttons" :key="button.button" :href="button.link" target="_blank" rel="noopener noreferrer" class="academic-button">
            <FontAwesomeIcon :icon="button.logo" /> {{ button.button }}
          </a>
        </div>
      </div>
    </div>
  </main>
</template>