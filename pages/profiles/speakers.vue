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
        <img class="profile-img" :src="'/images/profiles/speakers/' + profile.image + '_square.webp'" alt="" />
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
        <img :src="'/images/profiles/speakers/' + profile.image + '.webp'" :alt="profile.name" />
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
  color: var(--fg);
  border-radius: 2rem;
  border: 1px solid var(--primary);
}

.collage .profile-img{
  outline: 1px solid var(--fg);
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
        name: "Prof Ng Huck Hui",
        status: "Guest of Honour",
        image: "ng-huck-hui",
        description:
          "Professor Huck-Hui Ng is the Assistant Chief Executive of Research and Talent Development (R&TD), under the Agency for Science, Technology and Research. Professor Ng helped to set up and implement several national funding initiatives such as the Singapore Food Story, Prenatal and Early Childhood for Human Potential, and Nucleic Acids Therapeutics. <br> <br> Professor Ng is active in research and sits on several boards such as Science Center Singapore and NUS High School, and R&D funding steering committees. In recognition of his scientific contributions, Professor Ng has received numerous local and international honours and awards.",
      },
      {
        name: "Prof Duncan Haldane",
        status: "Keynote Speaker",
        image: "duncan-haldane",
        description:
        "F. Duncan M. Haldane, who shared the 2016 Nobel Prize for Physics with David Thouless and Michael Kosterlitz, is the Sherman Fairchild University Professor of Physics at Princeton University, a Fellow of the Royal Society of London, the U.S. National Academy of Sciences, and the Slovenian Academy of Sciences and Arts (foreign member). He is also a Fellow of the American Academy of Arts and Sciences, the American Association for the Advancement of Science, and the American Physical Society.  <br> <br> He was awarded a share of the Nobel Prize for his theoretical work on “topological states of matter”, including pioneering work on unexpected (and initially controversial) “topological quantum states” of one-dimensional systems of magnetic atoms (for which he had previously received the 1993 Oliver Buckley Prize of the American Physical Society), and on the theoretical prediction of (ferromagnetic) topological insulators (exhibiting the “quantum anomalous Hall effect”, finally first observed experimentally in 2013) for which he had shared the 2012 Dirac medal of the International Center Theoretical Physics (Trieste) with Charles Kane and Shou-Cheng Zhang. His work helped to open up new directions and ways of thinking about quantum effects in condensed matter, and in recent years, “topological quantum matter” has grown into a very active experimental field which many believe may provide platforms for “quantum computing”. He also initiated the field of “topological photonics”. He currently works on “quantum geometry” in the “fractional quantum Hall effect”. <br> <br> Haldane received his Ph.D. in theoretical condensed matter physics from Cambridge University, under the direction and mentorship of Philip W. Anderson (Nobel Laureate in Physics 1977), and, before his appointment at Princeton University, worked at the Institut Laue-Langevin (Grenoble, France), the University of Southern California, Bell Laboratories, and the University of California, San Diego, in the U.S.A. Haldane was born in London in 1951, with mixed Scottish and Austrian/Slovenian origins, and was educated at St. Pauls school, then Christ’s College, Cambridge."
      }
    ],
  },
  {
    event: "Guest Lectures",
    profiles: [
      {
        name: "Prof Sow Chorng Haur",
        image: "sow-chorng-haur",
        description: "Professor Sow Chorng Haur received his Bachelor of Science Degree (1st Class) in Physics from the National University of Singapore (NUS) in 1991. He received his Master of Science degree in Physics after spending two more years at NUS for research. Prof Sow then completed his PhD degree in the University of Chicago in 1998. For the next two years, he worked as a postdoctoral fellow at Bell Laboratory, Lucent Technologies. He then returned and joined the Department of Physics, NUS in 2001. He is now the Vice Dean (Outreach and Admissions) of the Faculty of Science and the Vice President of the Singapore National Academy of Science. Prof Sow’s research interests include carbon nanotubes, nanomaterials, and the fundamental studies of 2D materials (e.g. graphene, dichalcogenide, and phosphorene) and their applications. He has worked on developing a laser pruning method to create unique 2D and 3D structures made of carbon nanotubes, the synthesis of a wide variety of nanoscale metallic oxide materials, and the assembly of nanowires and nanowalls. Prof Sow, with over 270 publications, has authored and co-authored many papers in the field of nanoscience and nanomaterials. Prof Sow is also known for being an inspiring educator, having been awarded various teaching awards such as the University Award: Outstanding Educator Award from NUS in 2008, and the Faculty Teaching Excellence Award from 2002 to 2013."
      },
      ]
  },
  {
    event: "Masterclasses",
    profiles: [
      {
        name: "Prof Dame Sue Black",
        image: "dame-sue-black",
        description: "Professor Dame Sue Black is the President of St John's College, Oxford. She is a leading forensic anthropologist who has been involved in many mass fatality events and war crimes investigations.",
      },
      {
        name: "Prof Aaron Ciechanover",
        image: "aaron-ciechanover",
        description: " “I don’t have a job, I have a hobby,” says Aaron Ciechanover, Distinguished Research Professor in the Faculty of Medicine at Technion – Israel Institute of Technology. Prof Ciechanover places a strong emphasis on doing what one loves in a career and believes that it is never too late to pursue one’s passions. <br> <br> This line of thinking was certainly shaped by Prof Ciechanover’s own experience. He is a physician by training, but his first love has always been biology and understanding the natural world. During his medical degree, he started to wonder about the mechanisms underlying diseases and realised that a physician’s role is limited to examining diseases after they have developed. Seeing science as the answer to his questions, he pivoted to research and has never looked back. <br> <br> In many ways, Prof Ciechanover is grateful for his medical training because he felt that the field has enriched his scientific knowledge and contributed to his ability to understand and develop drugs to treat diseases. <br> <br> He joined Professor Avram Hershko’s laboratory as part of his internship requirement to obtain his medical license, and the two have collaborated closely ever since. <br> <br> Prof Ciechanover, Prof Hershko, and the late Professor Irwin Rose worked together to understand protein degradation. Proteins are in all living things and are constantly removed or replaced. Although researchers had figured out how cells produce various proteins, the mechanism to remove and recycle them was unknown at that time. <br> <br> For their discovery of a small protein called ubiquitin that marks old proteins for destruction, Prof Ciechanover and his colleagues were awarded the Nobel Prize in Chemistry in 2004. Their seminal work advanced our understanding of cellular processes and disease formation as well as contributed to drug development. <br> <br> Prof Ciechanover sees collaborations as fundamental in research, particularly when scientific fields like biology and physics have expanded tremendously since his days as a student. “You need to collaborate. The multiple hands that make the world these days are not an option anymore, they are essential,” he explains. However, Prof Ciechanover believes that successful collaborations rely on the individual expertise of each collaborator. <br> <br> He advises young scientists to focus on building their niche, knowledge, and skills—in other words, to create demand for themselves and offer expertise that others will seek. <br> <br> He also equates establishing a career in science to running a long marathon or climbing a mountain, both of which require resilience and patience. <br> <br> He advises budding scientists to see their struggles as progress, their mistakes as learning points, and their successes as possibilities. “What I tell young people is this: what you see in front of you when you look at me is not a dream, it's reality. So materialise your own reality,” says Prof Ciechanover. "
      },
      {
        name: "Sir Tim Hunt",
        image: "tim-hunt",
        description:
          "Sir Tim Hunt grew up in Oxford, where he became fascinated by science at the Dragon School. At 14, he entered Magdalen College School, where his interest in biology grew. Sir Tim entered Clare College, Cambridge in 1961 to read Natural Sciences. He joined the Department of Biochemistry in 1964 as a graduate student working on the control of haemoglobin synthesis. In 1968 he moved to the Albert Einstein College of Medicine in New York as a postdoctoral Fellow with Irving London. Sir Hunt returned to the Department of Biochemistry in Cambridge in 1971 where he continued to work on translational control throughout the 1970s. He taught summer courses at the Marine Biological Laboratory, Woods Hole, Massachusetts from 1977 to 1983, looking at changes in protein synthesis in sea urchin and clam eggs after fertilisation. In 1979, he helped Joan Ruderman and Eric Rosenthal with experiments on the translational control of maternal mRNA in clam eggs, where two of the major mRNAs concerned later turned out to be the A and B-type cyclins. By 1982, Sir Hunt had almost exhausted the potential of sea urchin eggs, but it was then that he performed the experiment that led to the discovery of cyclins and subsequent research on the control of the cell cycle. In 1990, he joined ICRF (now The Francis Crick Institute) in London. He became a fellow of the Royal Society in 1991, a foreign associate of the US National Academy of Sciences in 1999, and shared the Nobel Prize for Physiology or Medicine with Lee Hartwell and Paul Nurse in 2001. Sir Hunt enjoys cooking, photography, and making up problems for Molecular Biology of the Cell with his friend John Wilson. In 2016, he and his wife Mary Collins moved to Okinawa, where Mary was the Provost of OIST (Okinawa Institute of Science and Technology). In 2022, Mary was appointed Director of the Blizard Institute of QMUL and they returned to London."
      },
      {
        name: "Professor Takaaki Kajita",
        image: "takaaki-kajita",
        description:
          "Prof Takaaki Kajita is the Special University Professor at The University of Tokyo, and also the Professor at the Institute for Cosmic Ray Research (ICRR) of The University of Tokyo. Prof Kajita received his Ph.D. from The University of Tokyo School of Science in 1986 and has been researching Kamiokande and Super-Kamiokande detectors at the Kamioka Observatory in central Japan. In 1998, at the Neutrino International Conference held in Takayama, Gifu, he showed the analysis results which provided strong evidence for atmospheric neutrino oscillations. In 2015 he shared the Nobel Prize in Physics for his role in discovering atmospheric neutrino oscillations. Currently, he is the project leader for the KAGRA Project, aiming to explore gravitational wave astronomy."
      },
      {
        name: "Sir Richard Roberts",
        image: "richard-roberts",
        description:
          "Dr. Richard J. Roberts is the Chief Scientific Officer at New England Biolabs, Ipswich, Massachusetts. He received a Ph.D. in Organic Chemistry in 1968 from Sheffield University and then moved as a postdoctoral fellow to Harvard. From 1972 to 1992, he worked at Cold Spring Harbor Laboratory, eventually becoming Assistant Director for Research under Dr. J.D. Watson. He began work on the newly discovered Type II restriction enzymes in 1972 and his laboratory discovered more than 70% of the first 100 enzymes described. In 1975 he became the fourth employee of New England Biolabs first as their chief consultant and later moved to the company permanently in 1992. Studies of transcription in Adenovirus-2 led to the discovery of split genes and mRNA splicing in 1977, for which he received the Nobel Prize in Medicine in 1993. <br> <br> During the sequencing of the Adenovirus-2 genome, computational tools became essential and his laboratory pioneered the application of computers in this area. <br><br> DNA methyltransferases, as components of restriction-modification systems are also of active interest and the first crystal structures for the HhaI methyltransferase led to the discovery of base flipping. Bioinformatic studies of microbial genomes to find new restriction systems are a major research focus as is the elucidation of DNA methyltransferase recognition sequences using SMRT sequencing and a new approach to elucidating m5C-containing recognition sequences. It is now clear that these enzymes do much more than simply protect host DNA from the action of their restriction enzymes. <br><br> Since winning the Nobel Prize, Dr. Roberts has been involved in organizing a number of Nobel initiatives to correct scientific misunderstandings and promote humanitarian causes. His most recent campaign has been on the issue of GMOs, where 160 Nobel Laureates have supported the use of GMO techniques to improve plant breeding practices that could greatly help the developing world.",
      },
      {
        name: "Prof Gregory Goh",
        image: "gregory-goh",
        description:
          "Prof. Gregory Goh is the Executive Director of the National Metrology Centre at A*STAR. Before this appointment, he was the Deputy Executive Director of the Institute of Materials Research and Engineering at A*STAR and had held appointments such as Director of the Strategic Research Office and Head of the Ceramics Materials department. Prof. Goh is the Covering Focal Point for the Sub Committee on Materials Science and Technology, part of the ASEAN Committee on Science, Technology and Innovation. He has also held an adjunct position in Materials Science and Engineering department at Nanyang Technological University since 2005. <br><br> From 2017 to 2019, Prof. Goh held a concurrent appointment as the Director of Special Projects in the Science and Engineering Research Council, A*STAR, where he scoped future R&D programmes and oversaw electrification of transport and related matters in the Urban and GreenTech Office. He also represented A*STAR on various working committees such as Land and Liveability, Smart Urban Habitat, and the biennial MND Urban Sustainability R&D Congress. In addition, Prof. Goh is the founding chair of Singapore Battery Consortium. In the years before taking up management responsibilities, Prof. Goh led R&D projects under the 1st and 2nd Joint A*STAR-MND Green Building Thematic Strategic Research Programmes and also served as the Programme Manager for the 2nd programme. He also initiated and led research collaborations with overseas institutions such as Tohoku University, University College London and the University of California, Santa Barbara. His research focused on the deposition of functional and electroceramic films and nanostructures which can be utilised in self-cleaning, heat reflection and also electrochemical applications. He has delivered over 30 invited lectures and has served on the Scientific Advisory Committees of international conferences in Asia and Europe. He is an inventor of several Singapore, PCT, Japan and US patent applications. <br> <br> Prof. Goh graduated with a Bachelor of Engineering (1st Class Honours) and Master of Engineering from the Department of Mechanical Engineering at the National University of Singapore and obtained his Doctor of Philosophy from the Department of Materials Science and Engineering at the University of California at Santa Barbara on an IMRE Fellowship. Prof. Goh’s doctoral studies focused on developing a new, low-temperature method for forming films of electronic ceramics while his Master's Degree research investigated the fabrication of ceramic cutting tools.",
      },
      {
        name: "A/Prof Huang Shao Ying ",
        image: "huang-shao-ying",
        description:
          "Shao Ying Huang is an Associate Professor in the pillar of Engineering Product Development, Singapore University of Technology and Design. She received her B.Eng., M. Eng., and Ph.D. degrees from Nanyang Technological University, Singapore in 2003, 2006, and 2011, respectively. Her research interests include low-field portable MRI (magnets and coils), non-linear MRI image reconstructions, RF aspects of MRI, MR electrical property tomography, radiofrequency (RF) / microwave noninvasive / contactless sensing, wireless power transfer, and wideband RF/microwave components. <br> <br> She owns 10 patents and 6 technology disclosures. She has authored and coauthored more than 60 papers in refereed journals, 1 book chapter, and more than 200 international conference papers. ",
      },
      {
        name: "Dr Lee Hwee Kuan",
        image: "lee-hwee-kuan",
        description:
          "Dr. Lee Hwee Kuan earned his Ph.D. from Carnegie Mellon University in Pittsburgh, PA, USA, in theoretical physics. Currently, he serves as the Head of the Imaging Informatics Division as well as the Deputy Director for Training and Talent Development at the Bioinformatics Institute, A*STAR in Singapore. Dr. Lee's expertise lies in the development and deployment of machine learning and deep learning algorithms. With a strong foundation in theoretical physics, Dr. Lee brings a unique perspective to the field of artificial intelligence, driving innovative solutions for both clinical and biological applications. <br><br> At present, Dr. Lee Hwee Kuan leads a laboratory dedicated to the advancement of Artificial Intelligence (AI) research for clinical and biological purposes. His research endeavours encompass a broad spectrum of activities, from fundamental AI-centric investigations to practical AI applications. Dr. Lee's work is particularly influenced by high-impact clinical use cases, driving theoretical AI development. His laboratory addresses critical areas such as diagnostics in cancers, cardiology, dermatology, and interventional radiology. In the realm of biology, Dr. Lee's team develops bioinformatics pipelines for spatial omics and single-cell analysis, alongside pioneering AI applications in protein science and drug discovery. Beyond his role at the Bioinformatics Institute, Dr. Lee holds significant appointments in various local universities and research institutions.",
      },
      
      
      {
        name: "A/Prof Sierin Lim",
        image: "sierin-lim",
        description:
          "Dr Sierin Lim is an Associate Professor of Bioengineering at the School of Chemistry, Chemical Engineering and Biotechnology at Nanyang Technological University, Singapore (NTU). Her research group focuses on the design and engineering of hybrid nano/microscale biodevices using proteins for applications in health and the environment. Specifically, her Bioengineered and Applied Nanomaterials Lab (BeANs Lab) uses protein cages as the building blocks and a platform for the formulation and delivery of active molecules to the skin. Her lab also explores the utility of protein cages to enhance contrast in imaging atherosclerotic plaques. In her Molecular & ﻿Cellular Bioengineering Lab (MCBe Lab), she leads a program in engineering enzymes and microbes to upcycle plastic wastes to oil, cellulose, and cannabinoids using cyanobacteria, cellulose bacteria, and yeast. <br><br> She is currently serving as the Associate Dean of Global Partnerships at the NTU Graduate College. ﻿She earned her B.S. in Chemical Engineering and Ph.D. in Biomedical Engineering from the University of California Los Angeles (UCLA). ",
      },
      {
        name: "Prof Bin Liu",
        image: "bin-liu",
        description:
          "Professor Bin Liu is Tan Chin Tuan Centennial Professor and Deputy Provost (Research and Technology) at the National University of Singapore (NUS). She is an international member of the US National Academy of Engineering, a Fellow of the Singapore Academy of Engineering, and the Singapore National Academy of Sciences. <br><br> Bin graduated with Bachelor’s and Master’s degrees from Nanjing University and a Ph.D. in Chemistry from NUS. She had postdoctoral training at the University of California, Santa Barbara before joining NUS as an Assistant Professor in late 2005 and was promoted to full Professorship in 2016. <br><br> Bin is a leader in the field of organic functional materials, who has been well-recognized for her contributions to polymer chemistry and organic nanomaterials for energy and biomedical applications. She has been named among the World's Most Influential Scientific Minds and the Top 1% Highly Cited Researchers by Clarivate since 2014. She is a prolific researcher with 500 publications and over 50,000 citations. She holds 30 patents with 16 of them licensed to different companies in the US, UK, and Asia. <br><br> Bin has received many awards, including the National Science and Technology Young Scientist Award (2008), the President’s Technology Award (2016), the American Chemical Society ACS Nano Lectureship Award (2019), the Royal Society of Chemistry’s Centenary Prize (2021), Kabiller’s Young Investigator Award (2021) and the IUPAC Distinguished Women in Chemistry or Chemical Engineer Award (2023). Bin serves on the editorial advisory boards of more than a dozen top peer-reviewed chemistry and materials journals. Since 2019, she has served as the Deputy Editor to launch and develop ACS Materials Letters, a flagship materials journal of the American Chemical Society."
      },
      {
        name: "A/Prof Soo Han Sen",
        image: "soo-han-sen",
        description:
          "Dr. Soo is an Associate Professor at the School of Chemistry, Chemical Engineering and Biotechnology in Nanyang Technological University (NTU) Singapore. He graduated from MIT with Bachelor’s and Master’s degrees and completed his Ph.D. work at U.C. Berkeley. Subsequently, he joined the Lawrence Berkeley National Laboratory as a postdoctoral fellow, working on materials and nanotechnology for artificial photosynthesis. <br><br> Dr. Soo started his independent career at NTU in 2012. The overarching theme of his research programme is the development of artificial photosynthesis systems by using solar and other forms of renewable energy to catalyse the production of fuels and chemical feedstocks from “waste” materials. One of the latest breakthroughs from his group is the demonstration of a way to use light to upcycle non-biodegradable plastics into platform chemical feedstocks under ambient temperatures and pressures, which can dramatically reduce the energy intensity and greenhouse gas emissions of the process."
      },
      {
        name: "Dr Tang Kok Zuea",
        image: "tang-kok-zuea",
        description:
          "Dr KZ Tang is presently a senior lecturer in the Innovation and Design Programme (iDP), College of Design and Engineering, National University of Singapore since 2010. He received his Bachelor of Electrical Engineering (1998), Masters in Electrical and Computer Engineering (2000), and Doctor of Philosophy in Electrical and Computer Engineering (2005) from the National University of Singapore. <br> <br> Prior to joining the iDP, he was an active academic research member in the Department of Electrical and Computer Engineering (NUS). He has published over 40 books, book chapters, international-refereed journals, and conference papers. He is also a certified Autodesk Instructor since Apr 2011 and a certified LabVIEW associate developer since 2008. He was awarded the ‘Top 100 Engineers (2011)’ from the International Biographical Centre. One of these works is awarded the ‘Top 10 articles in Biomed Library and another is invited to be included in SciTopics. He is also invited as a speaker to various IEEE-sponsored international and regional conferences. <br><br> One of Dr. Tang’s patented inventions is also successfully licensed to a biomedical apparatus company, Biofactory. He has conducted several well-received professional training classes, workshops, and seminars for professional engineers, undergraduates, and high school students. <br> <br> He is a recipient of various international design and innovative awards (Highlight: Best Innovation in Robotics 2010, ASEAN Virtual Instrumentation Applications Contest, First Prize 2009 International Digital Signal Processing Creative Design Contest and Best Paper (Mechatronics) Award, IEEE ICMA 2009, IEEE International Conference on Mechatronics Automation). <br> <br> Leveraging his research activities, experiences, and interests, he hopes to contribute effectively as a mentor and supervisor to the multi-disciplinary student teams in the CDE. Particularly, with his contacts with experts and know-how of state-of-the-art technology in his related research fields, he hopes to bring in new dimensions to the students’ teams. His teaching objective is to create effective student teams and inject new learning dimensions into the students, with new leads to tackle the Grand Challenges in their undergraduate study and beyond. Particularly, he is motivated to develop and implement new teaching techniques, with a focus on a design approach. <br><br> He is also interested in introducing smart classrooms and learning concepts to enhance the learning process. <br><br> Related to developing new AI methods, Dr. Tang’s research interests include new and improved control and diagnostic methodologies for intelligent mechatronics, servo and precision motion systems and servomechanisms, and improvements on current methods for adaptive neural control for the above-mentioned systems, new control methods for biomedical and other related systems, and new and improved optimization methods for different platforms."
      },
      {
        name: "Prof Wu Wei",
        image: "wu-wei",
        description:
          "Prof Wu Wei received his PhD degree at Swiss Federal Institute of Technology in Lausanne (EPFL), Switzerland. Before joining Nanyang Technological University (NTU), Singapore, he was a Postdoctoral Scholar at Stanford University, USA. He is currently an Associate Professor at NTU and serves as the Honorary Secretary of Society for Rock Mechanics & Engineering Geology (SRMEG), the Associate Editor for the International Journal of Rock Mechanics and Mining Sciences, and the Assistant Chair for Research in the School of Civil and Environmental Engineering (CEE), NTU. <br> <br> Prof Wu’s research focuses on experimental geophysics and energy geomechanics, with an emphasis on underground space development, geo-energy extraction, and storage, as well as induced geohazards due to climate change and energy extraction. He currently leads several research projects on geothermal energy exploration, underground energy storage, and urban geophysical surveys in Singapore. <br><br> He has received numerous awards such as the NTU CEE Research Award in 2023, the SRMEG Outstanding Paper Award in 2017, and the Swiss Perspective Researcher Fellowship in 2013."
      },
    ],
  },
];

const eventsOpen = ref(Array(profiles.length).fill(false));
</script>
