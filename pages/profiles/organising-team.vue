<template>
  <h1>The Organising Team</h1>

  <div class="comm" v-for="comm in profiles">
    <div class="comm-title">{{ comm.name }}</div>
    <div class="comm-showcase">
      <img
        class="comm-img"
        :src="'/images/profiles/organising-team/' + comm.image + '.webp'"
      />
      <div class="comm-description">
        <p v-html="comm.description" class="commDescription"></p>
        <p v-html="comm.imgCaption"></p>
      </div>
    </div>
  </div>
</template>

<style scoped>

.commDescription {
  margin-top: 0rem;
}
.comm {
  margin-block: 3rem 3.5rem;
}

.comm-title {
  font-size: 56px;
  font-weight: bold;
  margin-block: 0 -0.25rem;
  margin-left: 0.5rem;
  line-height: 0.9em;
  margin-bottom: 1rem;

  color: var(--primary);
}

.comm-showcase {
  display: grid;
  grid-template-columns: 6fr 4fr;
  gap: 2rem;
}

.comm-img {
  width: 100%;
  border-radius: 4px;
}

@media screen and (max-width: 900px) {
  .comm-title {
    font-size: 48px;
  }

  .comm-showcase {
    grid-template-columns: 1fr;
    gap: 0.5rem;
  }

  .comm-description {
    margin-top: 0;
  }

  .comm-showcase p {
    margin-block: 0.75rem;
  }
}
@media screen and (max-width: 600px) {
  .comm-title {
    font-size: 38px;
    margin-left: 0;
    /* margin-bottom: -0.075em; */
  }
}
</style>

<script setup>
const profiles = [
  {
    name: 'Admin & Operations',
    image: 'ano',
    description:
      'The Admin & Operations team are dedicated individuals who work tirelessly to ensure your ISYF experience is smooth and seamless. They orchestrate and tie events together behind the scenes to bring you a truly fulfilling experience!',
    imgCaption:
      'Chan Jin Tian Donovan, Wong Yu Feng, Liu Dong Yue, Jeremiah Ho Leung Enn, Kim Eng Kian, Cao Zihan',
  },
  {
    name: 'Ceremonies',
    image: 'ceremonies',
    description:
      'The Ceremonies team have planned two major events for ISYF: The ISYF Keynote Lecture and Closing Lunch. <br/><br/> The Keynote Lecture is a great chance for you to hear more from Nobel laureates and eminent scientists on issues surrounding the theme of the forum. You also get a chance to pose your very own questions to the experts in a forum styled question-and-answer session. <br/><br/> The Closing Ceremony on the other hand is our way of ending off ISYF on a high note, so be ready with your cameras to take some memorable photos!',
    imgCaption:
      'Jolin Lim En Qi, Kan Wei Sen, Kwek Yee Shong, Nguyen Do Khanh Phuong, Kenneth Kuah Seng Ray, Ang En Ci',
  },
  {
    name: 'Masterclasses',
    image: 'dnm',
    description:
      'The Masterclasses team seek to connect you to knowledgeable and prominent scientists, allowing you to explore new perspectives and gain new insights on notable scientific research. We hope you stay curious and embrace this valuable oportunity with eminent scientists and Nobel laureates!',
    imgCaption:
      'Alex Liu Su, Leong Wei Chan, Sun Zizhuo, Zhang Qinqi, Alexis Lee Simin, Zhou Ruihan, Cao Xizhen, Vu Minh Tran',
  },
  {
    name: 'Media & Publications',
    image: 'mnp',
    description:
      'The Media & Publications team constantly strive to deliver to you the best publicity efforts and media projects. Stay informed with the ISYF website, Instagram pages and the student handbook. Also enjoy the unique designs on the ISYF merchandise made by our very own designers. We hope that the content we create will be able to add to your ISYF experience!',
    imgCaption:
      'Amy Ong Jin Lu (Wang Jingru), Cheah Sheng Xin, Zhao Jianzhi, Wee Xi Ya Venecia, Liu Jia Yue, Tay Hao Chen, Wang Shihan, Chua Wenzheng Frederic,	Ernest Chan Ern Yi, Jiang Yixiang, Sophie Tung Xuan Ying<br>External Sub-comm:</b> Tay Hao Chen, Wang Shihan, Chua Wenzheng Frederic,	Ernest Chan Ern Yi, Jiang Yixiang, Sophie Tung Xuan Ying			',
  },
  {
    name: 'Recreational Activities',
    image: 'reacts',
    description:
      'The Recreational Activities team are in charge of ensuring you enjoy yourself thoroughly, through fun activities like the Singapore Discovery Tour, Cultural Hour and Exhibitions. ISYF is the perfect avenue to meet new friends who are passionate in science, and we hope that these activities provide a great time for you to bond with them!',
    imgCaption:
      'Tan Eu Chern, Koo Xin Xuan (Gu Xinxuan), Liang Zhongchen, Wang Shao Kai, Xie Sihao, Gao Yuxin, Dai Jiacheng, Su Ruo En <br> External: Su Ruo En',
  },
  {
    name: 'Science Activities',
    image: 'sciacts',
    description:
      'The Science Activities team will enrich your learning with various activities to dive deeper into the world of Science. Do look forward to science excursions and challenges, which will be sure to provide something new for everyone!',
    imgCaption:
      'Jethro Chai Tsin Kai, Caelen Chang Kai Mun, Zhu Yijun, Kong Jia Le Dylan, Yao Zilu Isaiah, Boyce, Sim Shuan Luck ',
  },
];
</script>
