<template>
  <h1>Participating Schools</h1>

  <div class="collage">
    <section class="event" v-for="country in schools">
      <h3 class="event-title">{{ country.country }}</h3>
      <span class="profile" v-for="profile in country.schools">
        <img class="profile-img" :src="'/images/profiles/schools/' + profile.name + '.jpg'" alt="" />
        <span class="name">{{ profile.name }}</span>
      </span>
    </section>
  </div>
</template>

<style scoped>
@import url('~/assets/css/profiles.css');

.collage .event {
  grid-template-columns: repeat(auto-fill, minmax(min(80%, 18rem), 1fr));
}

.collage .event-title {
  grid-column: span 1;
  background-color: white;
  font-size: 36px;
  font-style: normal;
}

.collage .profile {
  grid-column: span 1;
  aspect-ratio: 1.9;
  display: grid;
  grid-template-columns: 1fr 1fr;
  background-color: white;
  background-image: none;
  border: 1px solid var(--fg);
  overflow: hidden;
}

.collage .profile-img {
  /* padding: 18.75%; */
  vertical-align: middle;
  max-width: 62.5%;
  max-height: 62.5%;
}

.collage .name {
  position: static;
  height: 100%;
  padding-inline: 0.75rem;
  display: grid;
  place-items: center start;

  background-image: none;
  --bg: var(--gray-100);
  --fg: var(--gray-900);
  background-color: var(--bg);
  box-shadow: 0px 0px 20px 0px #272f4077;

  /* Theres a thin black underline for some reason, this is just to cancel it out */
  text-decoration: underline;
  text-decoration-color: var(--bg);
  text-align: left;
  font-size: 15px;
  font-weight: 500;
  line-height: 1.25em;
}
</style>

<script setup>
const schoolsUnordered = [
  { 'country': 'Overseas', 'name': 'New Generation School Preah Sisowath High School' }, 
  { 'country': 'Overseas', 'name': 'The Angkor Intellectual Academy' }, 
  { 'country': 'Overseas', 'name': 'The Second High School Attached to Bejing Normal University' }, 
  { 'country': 'Overseas', 'name': 'Taipei First Girls High School' }, 
  { 'country': 'Overseas', 'name': 'Taipei Municipal Chien Kuo High School' }, 
  { 'country': 'Overseas', 'name': 'Tallinn Secondary School of Science' }, 
  { 'country': 'Overseas', 'name': "Diocesan Girls' School" }, 
  { 'country': 'Overseas', 'name': 'Center for Young Scientists' }, 
  { 'country': 'Overseas', 'name': 'SMA Negeri 4 Denpasar High School' }, 
  { 'country': 'Overseas', 'name': 'National Gifted Secondary School of Laos' }, 
  {'country':'Overseas','name':'SMJK Chung Ling Pulau Pinang'},
  { 'country': 'Overseas', 'name': 'Philippine Science High School Main Campus' }, 
  { 'country': 'Overseas', 'name': 'Korea Science Academy of KAIST' }, 
  { 'country': 'Local', 'name': 'Anglican High School' }, 
  { 'country': 'Local', 'name': "CHIJ St. Nicholas Girls' School" }, 
  { 'country': 'Local', 'name': 'Chung Cheng High School (Main)' }, 
  { 'country': 'Local', 'name': 'Clementi Town Secondary School' }, 
  { 'country': 'Local', 'name': "Crescent Girls' School" }, 
  { 'country': 'Local', 'name': 'Dunman High School' }, 
  { 'country': 'Local', 'name': "Methodist Girls' School" }, 
  { 'country': 'Local', 'name': 'Nan Chiau High School' }, 
  { 'country': 'Local', 'name': 'Nanyang Girls\' High School' }, 
  { 'country': 'Local', 'name': 'National Junior College' }, 
  { 'country': 'Local', 'name': 'NUS High School of Mathematics and Science' }, 
  { 'country': 'Local', 'name': "Raffles Girls' School (Secondary)" }, 
  { 'country': 'Local', 'name': 'Raffles Institution' }, 
  { 'country': 'Local', 'name': 'River Valley High School' }, 
  { 'country': 'Local', 'name': 'School of Science and Technology, Singapore' }, 
  { 'country': 'Local', 'name': "St. Margaret's School (Secondary)" }, 
  { 'country': 'Local', 'name': "St. Joseph's Institution (Secondary)" }, 
  { 'country': 'Local', 'name': 'Tanjong Katong Secondary School' }, 
  { 'country': 'Local', 'name': 'Temasek Junior College' }, 
  { 'country': 'Local', 'name': 'Yuan Ching Secondary School' }, 
  { 'country': 'Local', 'name': 'Victoria Junior College' }, 
  { 'country': 'Local', 'name': 'Xinmin Secondary School' }, 
  { 'country': 'Local', 'name': 'Zhonghua Secondary School' }, 
  { 'country': 'Local', 'name': 'Jurong Secondary School' }, 
  { 'country': 'Local', 'name': 'Hwa Chong Institution' }, 
  { 'country': 'Overseas', 'name': 'Kamnoetvidya Science Academy' }, 
  { 'country': 'Overseas', 'name': 'Mahidol Wittayanusorn School' }, 
  { 'country': 'Overseas', 'name': 'Staples High School' }, 
  { 'country': 'Overseas', 'name': 'HUS High School for Gifted Students' }];

const aggregatedData = schoolsUnordered.reduce((result, item) => {
  const country = item.country;
  if (!result[country]) {
    result[country] = { country, schools: [] };
  }
  result[country].schools.push({ name: item.name, image: item.image });
  return result;
}, {});

// Convert the aggregated data object back to an array
const schools = Object.values(aggregatedData).sort((a, b) =>
  a.country.localeCompare(b.country),
);

console.log(schools);
</script>
