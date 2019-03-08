<template>

  <div class="main">
      <div class="container">
        <div class="slider" id="sld">

        <transition-group name="slider">
          <div class="timelineItem" :key="currentContent">
              <!-- <p>
                <a @click="prev()">Previous</a> || <a @click="next()">Next</a>
              </p> -->

                <h3 class="title" v-if="!currentContent.textMain">{{ currentContent.title }}</h3>

                  <img :src="currentContent.img" class="container__image image"/>
                <span
                  class="textMain">{{ currentContent.textMain }}
                  <p>
                    <strong v-if="!currentContent.title">&#8592; {{ currentContent.arrowText }} </strong>
                  </p>
              </span>
              <span class="first__text">{{ currentContent.first__text }}</span>

              </p>
          </div>
        </transition-group>
      </div>
    </div>

<transition name="slide-fade">
        <div class="textAppear" :key="currentContent.shortText">
        {{ currentContent.shortText }}
        </div>
</transition>


<div class="container2">
 <ul class="progressbar">
   <li class="white" @click="goToIndex(0)">
     <a @click="goToIndex(0)">Uvod</a></li>
   <li class="orange" @click="goToIndex(1)">
     <a @click="goToIndex(1)">Pred 100 000 leti</a></li>
   <li class="green" @click="goToIndex(2)">
     <a @click="goToIndex(2)">Leto 100</a></li>
   <li class="violet" @click="goToIndex(3)">
     <a @click="goToIndex(3)">Leto 1000</a></li>
   <li class="red" @click="goToIndex(4)">
     <a @click="goToIndex(4)">Leto 1850</a></li>
   <li class="blue" @click="goToIndex(5)">
     <a @click="goToIndex(5)">Danes</a></li>
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
      sld: 1200,
      show:false,
      content: [
        {
        title: "Družina nekoč in danes",
        shortText: "Družina nekoč in danes...",
        first__text: "Družina se je od nastanka človeka do danes neprestano spreminjala. Spreminjala se je velikost družine, pa tudi odnosi med družinskimi člani. Nekoč so prevladovale družine z veliko otroki, starši, starimi starši in drugimi sorodniki. Danes prevladujejo majhne družine."
        },
        {
        img: "/static/photo1.jpg",
        arrowText: "Prve skupnosti",
        textMain: 'Ljudje so živeli v večjih skupinah, ki so poleg staršev in otrok vključevale tudi stare starše in bljižnje sorodnike. Delo v družini je bilo razdeljeno. Moški so lovili živali in izdelovali orožje in orodje. Ženske so nabirale sadeže, pripravljale hrano, varovale ogenj in skrbele za otroke. Ženske so zaradi materinstva zelo cenili. Otoci so že od najzgodnješih let pomagali pri družinskih opravilih. Marsikje po svetu se je tak način življenja ohranil skoraj do danes.',
        shortText: "V času prvih skupnosti..."
        },
        {
         img: "/static/photo2.jpg",
         arrowText:"Rimljanska družina",
         textMain: "V družini so odločali moški. Ženske so podrejene očetu, po poroki pa možu. Največ ljudi se je preživljalo z obdelovanjem zemlje., zato je vsa družina večino časa preživela na polju. Glavna naloga žensk je bila rojevanje otrok in njihova vzgoja. Ženske v bogatih družinah so se udeleževale družabnih srečanj s svojimi prijateljicami, medtem ko so ženske na kmetijah opravljale kmečka in gospodinjska dela.",
         shortText: "V času Grkov in Rimljanov..."
        },
        {
         img: "/static/photo3.jpg",
         arrowText:"Družina na polju",
         textMain: "Poroke so bile največkrat dogovorjene med starši ko sta bila bodoča zakonca še otroka. V družini je imel oče neomejeno oblast nad vsemi člani družine. Dečke so že zgodaj vzgajali za vojake, dekleta pa za vodenja gospodinjstva. Kmečke družine, ki so prevladovale, so dneve preživljale ob delu na polju.",
         shortText: "V času gradnje gradov..."
        },
        {
         img: "/static/photo4.jpg",
         arrowText:"Družina za mizo",
         textMain: "V družinah meščnov so veliko pozornosti namenili vzgoji in izobraževanju otrok. Oče je bil glavna oseba v družini, odgovorna za varnost in premoženje družine. Bil je zgled svojim sinovom. Žene so bile podrejene možem, njihova dolžnost je bila vodonje gospodinjstva in vzgoja hčera. Kmečke in delavske družine so živele skromno. Na polju in v tovarjah so delali vsi družinski člani, tudi otroci.",
         shortText: "V času gradnje prvih tovarn..."
        },
        {
         img: "/static/photo5.jpg",
         arrowText:"Družina na počitnicah",
         textMain: "Položaj moškega in ženske v družbi je v večini po svetu enakopraven. Večina žensk je zaposlenih. Partnerji se za skupno življenje in otroke odločijo skoraj deset let kasneje kot nekoč. Otroci namenimo največ časa šoli, šolskim in obšolskih obveznostim.",
         shortText: "Danes..."
       }
     ],
    }
  },
        methods: {
          goToIndex: function(index) {
            this.showed_box = index
          },

          next: function() {
            this.showed_box += 1
          },
          prev: function() {
            this.showed_box -= 1
          }
        },
          computed: {
            currentContent: function() {
              return this.content[Math.abs(this.showed_box) % this.content.length];

          }
      }
   }
</script>

<style scoped>

* {
  box-sizing: border-box;
  font-family: sans-serif;
  color: grey;
  line-height: 1.6;
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
  /* margin-top: 30px; */
}

.image {
    display: inline-block;
    vertical-align: top;
    width: 45%;
    margin: 0px 70px 0 0px;
}


.textMain {
    display: inline-block;
    text-align: left;
    font-size: 25px;
    /* margin-top: 5%; */
    width: 30%;
    @media (max-width: 1400px) {
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
   margin-top: 7%;
 }

.timelineItems {
  display: inline-flex;
}

/* .timelineItem {
  background-color: #fdd530;
  width: 100%;
  display: block;
} */


.container{
  width: 1400px;
  height: 800px;
  margin: 20px auto;
  /* border: 20px solid #FDD530; */
  position: relative;
  overflow: hidden;
  background-color: #FDD530;
}

.container .slider{
  width: 8400px;
  height: 800px;
  position: absolute;
  transition: all 1s ease-in-out;
}

.container .slider{
  float: left;
  width: 1400px;
  height: 100%;
}

/* .container__image {
    display: inline-block;
    vertical-align: top;
    width: 50%;
    margin: 35px 50px 0 30px;
} */


/* BUTTONS */

.container2 {
  padding: 20px 40px 40px;
  width: 1500px;
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

a:focus {
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

/* .fade {
  animation: slide-in 2s ease-in-out forwards;
} */

.slide-fade-enter-active {
  transition: all 2s ease;
}

.slide-fade-leave-active {
  display: none;
  /* transition: all 1s cubic-bezier(1.0, 0.5, 0.8, 1.0); */

}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateY(-20px);
  opacity: 0;
}

.slider-enter-active {
  transition: 1s;
}

.slider-enter, .slider-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(200px);
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
