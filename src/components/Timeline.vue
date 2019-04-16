<template>

  <div class="main">
    <div class="container">

      <div class="slider" id="sld" :style="slideContent">

          <div class="box"  v-for="singleContent in content" :key="singleContent">

                  <h3 class="title" v-if="!singleContent.textMain">{{ singleContent.title }}</h3>

                    <img :src="singleContent.img" class="container__image image"/>
                     <span
                      class="textMain">{{ singleContent.textMain }}
                      <p>
                      <strong v-if="!singleContent.title">&#8592; {{ singleContent.arrowText }} </strong>
                    </p>
                  </span>
                <span class="first__text">{{ singleContent.first__text }}</span>

          </div>
      </div>
    </div>

<transition name="slide-fade">
        <div class="textAppear" :key="currentContent.shortText">
        {{ currentContent.shortText }}
        </div>
</transition>


<div class="container2">
 <ul class="progressbar">
   <li v-for="(object, index) in content" :ref="object.color" :class="object.color" @click="goToIndex(index)">
     <a :class="{ 'active': showed_box === index}"
     @click="goToIndex(index, object.color)">{{ object.buttonText }}</a>
    </li>
 </ul>
</div>
</div>


</template>

<script>
export default {
  name: 'Timeline',
  data() {
    return {
      showed_box: 0,
      singleWidth: 1300,
      content: [
        {
        title: "Družina nekoč in danes",
        shortText: "Družina nekoč in danes...",
        first__text: "Družina se je od nastanka človeka do danes neprestano spreminjala. Spreminjala se je velikost družine, pa tudi odnosi med družinskimi člani. Nekoč so prevladovale družine z veliko otroki, starši, starimi starši in drugimi sorodniki. Danes prevladujejo majhne družine.",
        buttonText: "Uvod",
        color:"white"
        },
        {
        img: "/static/photo1.jpg",
        arrowText: "Prve skupnosti",
        textMain: 'Ljudje so živeli v večjih skupinah, ki so poleg staršev in otrok vključevale tudi stare starše in bljižnje sorodnike. Delo v družini je bilo razdeljeno. Moški so lovili živali in izdelovali orožje in orodje. Ženske so nabirale sadeže, pripravljale hrano, varovale ogenj in skrbele za otroke. Ženske so zaradi materinstva zelo cenili. Otoci so že od najzgodnješih let pomagali pri družinskih opravilih. Marsikje po svetu se je tak način življenja ohranil skoraj do danes.',
        shortText: "V času prvih skupnosti...",
        buttonText: "Pred 100 000 leti",
        color:"orange"
        },
        {
         img: "/static/photo2.jpg",
         arrowText:"Rimljanska družina",
         textMain: "V družini so odločali moški. Ženske so podrejene očetu, po poroki pa možu. Največ ljudi se je preživljalo z obdelovanjem zemlje., zato je vsa družina večino časa preživela na polju. Glavna naloga žensk je bila rojevanje otrok in njihova vzgoja. Ženske v bogatih družinah so se udeleževale družabnih srečanj s svojimi prijateljicami, medtem ko so ženske na kmetijah opravljale kmečka in gospodinjska dela.",
         shortText: "V času Grkov in Rimljanov...",
         buttonText: "Leto 100",
         color:"green"
        },
        {
         img: "/static/photo3.jpg",
         arrowText:"Družina na polju",
         textMain: "Poroke so bile največkrat dogovorjene med starši ko sta bila bodoča zakonca še otroka. V družini je imel oče neomejeno oblast nad vsemi člani družine. Dečke so že zgodaj vzgajali za vojake, dekleta pa za vodenja gospodinjstva. Kmečke družine, ki so prevladovale, so dneve preživljale ob delu na polju.",
         shortText: "V času gradnje gradov...",
         buttonText: "Leto 1000",
         color:"violet"
        },
        {
         img: "/static/photo4.jpg",
         arrowText:"Družina za mizo",
         textMain: "V družinah meščnov so veliko pozornosti namenili vzgoji in izobraževanju otrok. Oče je bil glavna oseba v družini, odgovorna za varnost in premoženje družine. Bil je zgled svojim sinovom. Žene so bile podrejene možem, njihova dolžnost je bila vodonje gospodinjstva in vzgoja hčera. Kmečke in delavske družine so živele skromno. Na polju in v tovarjah so delali vsi družinski člani, tudi otroci.",
         shortText: "V času gradnje prvih tovarn...",
         buttonText: "Leto 1850",
         color:"red"
        },
        {
         img: "/static/photo5.jpg",
         arrowText:"Družina na počitnicah",
         textMain: "Položaj moškega in ženske v družbi je v večini po svetu enakopraven. Večina žensk je zaposlenih. Partnerji se za skupno življenje in otroke odločijo skoraj deset let kasneje kot nekoč. Otroci namenimo največ časa šoli, šolskim in obšolskih obveznostim.",
         shortText: "Danes...",
         buttonText: "Danes",
         color:"blue"
       }
     ],
    }
  },
        methods: {
          goToIndex: function(index, elementRef) {
            this.showed_box = index;
          }
        },
          computed: {
            currentContent: function() {
              return this.content[Math.abs(this.showed_box) % this.content.length];
          },
          slideContent: function() {
            return `transform: translateX(${this.singleWidth*(-1) * this.showed_box}px)`
        }
      }
   }
</script>

<style scoped>

* {
  box-sizing: border-box;
  font-family: sans-serif;
  color: grey;
  line-height: 1.4;
  -webkit-animation: pageLoad 1s; /* Safari, Chrome and Opera > 12.1 */
     -moz-animation: pageLoad 1s; /* Firefox < 16 */
      -ms-animation: pageLoad 1s; /* Internet Explorer */
       -o-animation: pageLoad 1s; /* Opera < 12.1 */
          animation: pageLoad 1s;
}

.title {
  font-size: 45px;
  margin-top: 12%;
}

.main{
  position: relative;
}

.image {
    display: inline-block;
    vertical-align: top;
    width: 45%;
    margin: 65px 90px 0 0;
}


.textMain {
    display: inline-block;
    text-align: left;
    font-size: 23px;
    margin-top: 90px;
    width: 30%;
    @media (max-width: 1300px) {
        width: 100%;
    }
 }

 .first__text {
     width: 80%;
     text-align: center;
     display: inline-block;
     font-size: 25px;
     /* margin-top: 5% */
     /* margin-left: 8%;  */
 }

 .timelineItem {
   /* margin-top: 7%; */
   display: inline-block;
 }


.timelineItem {
  background-color: #fdd530;
  width: 100%;
  display: block;
}

.singleWidth {
  width: 1300px;
}


.container{
  width: 1300px;
  height: 700px;
  margin: 20px auto;
  /* border: 20px solid #FDD530; */
  position: relative;
  overflow: hidden;
  background-color: #FDD530;
}

.container .slider{
  width: 7800px;
  height: 700px;
  position: absolute;
  transition: all 1s ease-in-out;
}

.container .slider .box{
  float: left;
  width: 1300px;
  height: 100%;
  background-color: #FDD530;
}


/* BUTTONS */

.container2 {
  padding: 20px 40px 40px;
  width: 1200px;
  margin: auto;
  position: relative;
  display: block;
  justify-content: center;
}

.progressbar {
  text-align: center;
  padding: 0;
  margin-top: 30px;
}

.progressbar li {
  list-style-type: none;
  display: inline;
  float: left;
  width: calc(100% / 6);
  position: relative;
  padding-bottom: 40px;
  margin: 0 auto;
  cursor: pointer;
}

.progressbar a {
  display: inline-block;
  text-align: center;
  text-decoration: none;
  font-size: 20px;
}

.white {
  color: white;
}

.orange {
  color: #fc9f30;
}

.green {
  color: #a1d52a;
}

.violet {
  color: #e03ea9;
}

.red {
  color: #fb481e;
}

.blue {
  color: #1fb5fc;
}

.progressbar li::before {
  content: counter(step);
  counter-increment: step;
  width: 40px;
  height: 40px;
  line-height: 40px;
  border: 3px solid grey;
  display: block;
  text-align: center;
  margin: 0 auto 10px auto;
  border-radius: 50%;
  background-color: #fc9f30;
}


.progressbar li::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 3px;
  background: grey;
  top: 20px;
  left: -40%;
  z-index: -1;
}

.progressbar li:first-child::after {
  content: none;
}

.progressbar .white::before {
  background-color: white;
}

.progressbar .green::before {
  background-color: #a1d52a;
}

.progressbar .violet::before {
  background-color: #e03ea9;
}

.progressbar .red::before {
  background-color: #fb481e;
}

.progressbar .blue::before {
  background-color: #1fb5fc;
}

.active {
  background-color: #FDD530;
  transition: all .5s ease-in-out;
  padding: 5px;
  color: black;
  font-size: 25px;
}

.textAppear {
  padding-top: 30px;
  font-size: 20px;
  text-align: center;
  position: relative;
}

.slide-fade-enter-active {
  transition: all 2s ease;
}

.slide-fade-leave-active {
  display: none;
}

.slide-fade-enter, .slide-fade-leave-to{
  transform: translateY(-20px);
  opacity: 0;
}


.slider-enter-active {
  transition: 1.5s;
}

.slider-leave-active {
  transition: 1.5s;
}

.slider-enter, .slider-leave-to
/* .slide-fade-leave-active below version 2.1.8  */
{
  transform: translateX(100px);
}


/* ANIMATIONS */

@keyframes slide-in {
    0% {
        transform: translateY(-30px);
        opacity: 0;
    }
    100% {
        transform: translateY(0);
        opacity: 1;
    }
}

@keyframes pageLoad {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Firefox < 16 */
@-moz-keyframes pageLoad {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Safari, Chrome and Opera > 12.1 */
@-webkit-keyframes pageLoad {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Internet Explorer */
@-ms-keyframes pageLoad {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Opera < 12.1 */
@-o-keyframes pageLoad {
    from { opacity: 0; }
    to   { opacity: 1; }
}
</style>
