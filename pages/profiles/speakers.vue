<template>
  <h1>Invited Speakers</h1>

  <p>
    Click on each speakers name to see their profile! You can also scroll down and see
    further details
  </p>

  <div class="collage">
    <section class="event" v-for="(event, eventIndex) in profiles" :class="{ 'event-open': eventsOpen[eventIndex] }">
      <h3 class="event-title">{{ event.event }}</h3>
      <a class="profile" v-for="profile in event.profiles" :href="'#' + profile.name.replaceAll(' ', '')"
        @click="resetLink">
        <img class="profile-img" :src="'/images/profiles/speakers/' + profile.image + '.jpg'" alt="" />
        <div class="name">
          {{ profile.name }}
        </div>
      </a>
    </section>
  </div>

  <div class="intros">
    <div class="event" v-for="event in profiles">
      <h2>
        <div class="scroll-banner-wrapper">
          <span class="scroll-banner">{{
            event.event.concat('&nbsp;&nbsp;•&nbsp;&nbsp;').repeat(30)
          }}</span>
        </div>
      </h2>

      <section class="profile" v-for="profile in event.profiles">
        <div class="scroll-anchor" :id="profile.name.replaceAll(' ', '')"></div>
        <img :src="'/images/profiles/speakers/' + profile.image + '.jpg'" :alt="profile.name"/>
        <div class="info">
          <h3>{{ profile.name }}</h3>
          <h4 v-if="profile.status">{{ profile.status }}</h4>
          <p>
            <span v-html="profile.description"></span>
          </p>
        </div>
      </section>
    </div>
  </div>
</template>

<style scoped>
@import url('~/assets/css/profiles.css');

.collage .event {
  grid-template-columns: repeat(auto-fill, minmax(min(40%, 10.8rem), 1fr));
}

.collage .name {
  bottom: -1rem;
  background-color: var(--bg);
  width: 80%;
  color: var(--fg);
  border-radius: 2rem;
  border: 1px solid var(--gray-900);
}

.collage .profile-img{
  outline: 1px solid var(--fg);
  height: 100%;
  width: 100%;
  object-fit: cover;
  border-radius: 8px;
}

</style>

<script setup>
import { ref } from "vue";

function resetLink() {
  setTimeout(() => {
    var newurl =
      window.location.protocol +
      "//" +
      window.location.host +
      window.location.pathname;
    window.history.pushState({ path: newurl }, "", newurl);
  }, 1);
}

const profiles = [
  {
    event: "Keynote Lecture",
    profiles: [
      {
        name: "Prof Brian Schmidt",
        status: "Keynote Speaker",
        image: "brian-schmidt",
        description:
        "Brian Schmidt is Distinguished Professor of Astronomy at the Australian National University, of which he has been a faculty member since 1995. From 2016 to 2023, he was the university’s 12th Vice Chancellor and President. He is a Fellow of the Australian Academy of Science, the US National Academy of Sciences and the Royal Society (London), as well as a Foreign Member of the Spanish Royal Academy of Sciences and the Indian Academy of Sciences. He also serves on a number of boards and councils, including Australia’s National Science and Technology Council and Singapore’s Research Innovation and Enterprise Council.<br><br>Prof Schmidt has worked across many areas of astronomy, including supernovae, gamma-ray bursts, gravitational wave transients, exo-planets and metal-poor stars. In 2000, he received the Australian Government’s inaugural Malcolm McIntosh Award for achievement in the physical sciences. This was followed by the 2006 Shaw Prize for Astronomy and the 2007 Gruber Prize for Cosmology. For his work on the accelerating universe, he shared the 2011 Nobel Prize in Physics with Adam Riess and Saul Perlmutter. In 2013, he was made a Companion of the Order of Australia."
      }
    ],
  },
  {
    event: "Guest of Honour",
    profiles: [
      {
        name: "Dr Ong Chen Hui",
        status: "Guest of Honour",
        image: "ong-chen-hui",
        description:
          "Dr Ong Chen Hui is the Assistant Chief Executive of the Business and Technology at the Infocomm Media Development Authority (IMDA), where she oversees the agency’s efforts in developing the industry and research ecosystem around emerging digital technologies, such as AI, AI safety, quantum communications and green computing. She developed the A.I. Verify toolkit and Project Moonshot for governance of AI, launched the National Multimodal LLM R&D programme that supports SEA-LION and MERaLiON LLMs, Future Communications R&D Programme to support 6G research, Digital Trust Centre to support research into trust technologies and National Quantum Safe Networks Plus Programme to support business access to quantum safe communications.<br><br>Chen Hui has spent more than 20 years in R&D and technology innovation. She serves on the technical boards of non-profits and is the Chair of AI Verify Foundation. Prior to IMDA, she was the APJ CTO in Trustwave – a Singtel company and Principal Member of Technical Staff in DSO National Laboratories.",
      },
      ]
  },
  {
    event: "Masterclasses",
    profiles: [
      {
        name: "Prof Roger Foo Sik Yin",
        image: "roger-foo",
        description: "Professor Roger Foo is the inaugural chair holder of the Zayed Bin Sultan Al Nahyan Professorship of Medicine and Vice Dean (Research) at the NUS Yong Loo Lin School of Medicine. He is also Director of the National University Health System (NUHS) Cardiovascular Research Institute (CVRI) and Senior Consultant at the National University Heart Centre Singapore (NUHCS), where he serves as the Clinical Lead for the Cardiac Genetics Service.<br><br>A cardiac geneticist with specific interest in cardio-metabolism, Prof Foo has established Singapore’s first Cardiac Genetics clinical service and has published widely in the field of Cardiovascular Molecular Epigenetics and Cell Biology. Prof Foo trained and worked in Cambridge, UK, for over 20 years, before moving his lab to Singapore in 2013. Research in his lab continues to use genomic technology to study the cardiac epigenome and hunt for novel heart failure mechanisms.",
      },
      {
        name: "Professor Armin Aberle",
        image: "armin-aberle",
        description: "Prof Armin Aberle serves as CEO and Head of the Solar Energy Research Institute of Singapore (SERIS) at the National University of Singapore (NUS). He is also a tenured full professor in the university’s Department of Electrical and Computer Engineering. He holds BSc/MSc, PhD and Dr habil degrees in physics from German universities (Freiburg, Hannover). His research focus is on photovoltaic (PV) materials, devices and modules. His R&D work covers the full spectrum from fundamental materials research to the industrial evaluation of advanced or novel PV technologies at the pilot line level and their transfer to industry. In his 38-year career in the PV sector he has (co)authored more than 600 scientific-technical papers (which have received more than 20,000 citations, h-index 68) and has been supervising more than 60 PhD students. He is an Editorial Board member of Progress in Photovoltaics and other scientific journals. From 1994 to 1998 he was the Scientific Director of the newly established Silicon PV Department at the Institute for Solar Energy Research (ISFH) in Hamelin, Germany. He then worked for 10 years in Sydney, Australia as a solar energy professor at the University of New South Wales (UNSW) and a member of the UNSW team that developed and taught the world’s first Bachelor of Engineering degree programme for Photovoltaic and Renewable Energy Engineering. In 2008 he joined NUS to establish SERIS, as the Deputy CEO and Director of the Silicon PV Cluster. Since 2012 he serves as SERIS CEO. He is also the Director of the institute’s Next-Generation Industrial Solar Cells & Modules Cluster and the Acting Director of the Novel PV Concepts Cluster."
      },
      {
        name: "Prof Dario Poletti",
        image: "dario-poletti",
        description:
          "Dr Dario Poletti is an Associate Professor and Head of the Science, Mathematics and Technology department of the Singapore University of Technology and Design (SUTD). He is also Principal Investigator at the Centre for Quantum Technologies and coordinator of the Majulab for the Quantum Thermodynamics, Energetics and Resources axis. Dario first joined SUTD in 2012 as an Assistant Professor, starting his own group. He was previously a postdoc at CQT and with groups in France and Switzerland. He obtained his joint PhD in Physics from the National University of Singapore and the Australian National University in 2009, for which he received the Medal of the Materials Research Society of Singapore for the best PhD thesis in NUS Physics Department. Before that, he earned a Master of Engineering (Nuclear Engineering) from Politecnico di Milano and Master of Engineer (Applied Physics) from Ecole Centrale Paris. In 2015, he was named in Asia Pacific MIT Technology Review’s Innovators under 35 list, and in 2017 received the IoP Outstanding Referee Award for New Journal of Physics. He has publications in journals including Nature, Nature Communications, Nature Quantum Information, Physical Review Letters, Physical Review X and Review of Modern Physics. He is serving as Vice President for the Institute of Physics Singapore. His work focuses on the physics of large quantum systems, especially their dynamics and interaction with environment, and development of numerical methods to study them including tensor networks and neural networks. In recent years his research has expanded also towards quantum and quantum-inspired computing."
      },
      {
        name: "Prof Dan Chia",
        image: "dan-chia",
        description:
          "Wei Ming Dan Chia is an Associate Professor in the Infocom Technology cluster at the Singapore Institute of Technology. He has obtained his PhD from the School of Computing Science at the University of Glasgow. Prior to his academic career, he gained 17 years of industry experience at Delphi, Siemens VDO, and Continental from 2001 to 2017. His last position at Continental was Director of the ITS Laboratory and Head of Advanced Development in Asia for infotainment and connectivity products. His primary research interests focus on the applied research of artificial intelligence to enhance the safety operations of autonomous vehicles and to develop intelligent transport systems.",
      },
      {
        name: "Sir Richard Roberts",
        image: "richard-roberts",
        description: "Sir Richard J. Roberts is Chief Scientific Officer at New England Biolabs in Ipswich, Massachusetts, United States. He first joined the company as chief consultant in 1975 and later moved there permanently in 1992. He received his PhD in Organic Chemistry in 1968 from Sheffield University and was a postdoctoral fellow at Harvard University. <br><br>While at Cold Spring Harbor Laboratory from 1972 to 1992, he began work on the newly discovered Type II restriction enzymes. His laboratory discovered more than 70 percent of the first 100 enzymes described. Studies of transcription in Adenovirus-2 led to the discovery of split genes and mRNA splicing in 1977, for which he received the Nobel Prize in Physiology or Medicine in 1993. Since then, Sir Richard has been involved in organising a number of Nobel initiatives to correct scientific misunderstandings and promote humanitarian causes, such as supporting the use of genetically modified organism techniques to improve plant breeding practices.",
      },
      {
        name: "Prof Joan Rose",
        image: "joan-rose",
        description:
          "Professor Joan B. Rose holds the Homer Nowlin Chair in Water Research at Michigan State University, where she has worked for the last 22 years. She is Director of the university’s Water Alliance, leading interdisciplinary efforts to solve global water problems. She is also a member of the US National Academy of Engineering, the Royal Institution of Singapore and the EU Academy of Sciences, as well as a Corresponding Member of the Royal Academy of Sciences and Arts of Barcelona, Spain.<br><br>Prof Rose is an international expert in water microbiology, water quality and public health safety with over 300 publications. She is the recipient of the 2016 Stockholm Water Prize and the 2024 IWA Global Water Award. Her research focuses on the application of new molecular methods, pathogen surveillance, microbial source tracking, removal of pathogens by water and wastewater treatment, and quantitative microbial risk assessment. She is currently Chair of the International Joint Commission’s Health Professionals Advisory Board. She has also been collaborating with the Michigan Department of Environment, Great Lakes, and Energy on the state-wide programme to use advanced technology for beach water testing and with the Michigan Department of Human Health Services on wastewater surveillance.",
      },
      {
        name: "Prof Aaron Ciechanover",
        image: "aaron-ciechanover",
        description: "Professor Aaron Ciechanover is Distinguished Research Professor in the Faculty of Medicine at Technion - Israel Institute of Technology. He completed his MSc and MD at the Hebrew University in Jerusalem, and a doctorate in biological sciences at Technion. His collaboration with Avram Hershko and Irwin A. Rose led to the discovery that the covalent attachment of ubiquitin to a target protein signals it for degradation. They deciphered the mechanism of conjugation, described the general proteolytic functions of the system, and proposed a model according to which this modification serves as a recognition signal for a specific downstream protease. For their findings, they were jointly awarded the Nobel Prize in Chemistry in 2004. <br><br>Other accolades that Prof Ciechanover has received include the 2000 Albert Lasker Award, the 2006 Sir Hans Krebs Medal and the 2011 Humboldt Research Award. He is also a member of the Israeli National Academy of Sciences and Humanities, the US National Academies of Sciences and of Medicine (Foreign Associate), the Pontifical Academy of Sciences at the Vatican, and the Chinese Academy of Sciences (Foreign Member).",
      },
      {
        name: "Prof Christian Kurtsiefer",
        image: "christian-kurtsiefer",
        description: "Professor Christian Kurtsiefer is a leading experimental physicist whose research has significantly advanced the fields of quantum optics and atomic physics. He received his Ph.D. in experimental physics from the University of Konstanz, Germany, in 1997, specialising in atom interferometry. Following a postdoctoral fellowship at IBM’s Almaden Research Center in San Jose, he joined the Ludwig-Maximilian University of Munich as a research scientist from 1999 to 2003 before moving to the National University of Singapore (NUS), where he became one of the founding members of the Centre for Quantum Technologies (CQT) in 2007.<br><br>At CQT, Professor Kurtsiefer leads the Quantum Optics Group (QOLAH). His main research interests lie in quantum optics and atomic physics, with a focus on experimental quantum information and communication, single-photon technologies, and atom–light interactions. His recent work explores practical quantum key distribution (QKD) systems, atom–photon interfaces, hybrid quantum systems, and quantum randomness sources.<br><br>A Fellow of the American Physical Society and past President of the Institute of Physics Singapore, Professor Kurtsiefer was the recipient of the 2025 IPS President’s Award for his pioneering contributions to quantum physics and his dedicated service to the physics community in Singapore.",
      },
    ],
  },
];

const eventsOpen = ref(Array(profiles.length).fill(false));
</script>
