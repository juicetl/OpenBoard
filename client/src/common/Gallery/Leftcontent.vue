<template>
  <div class="Leftcontent">
    <div
      class="item"
      v-for="index in this.covidkey"
      :key="index"
      @click="selectclick(index)"
    >
      <img :src="require('../../papers_img/' + index + '.jpg')" />
    </div>
  </div>
</template>
  
  <script>
import data from "../../../static/covid_data_e.json";
import layout from "../../../static/covid_data_layout.json";
import { mapState } from "vuex";
export default {
  name: "Leftcontent",
  components: {},
  data() {
    return {
      chartdata: [],
      datakey: [],
      flag  : 0
      // colorData: ["black", "pink", "blue"],
    };
  },
  computed: {
    ...mapState(["covidkey"]),
  },
  mounted() {
    console.log(data);
    let key = Object.getOwnPropertyNames(data);
    console.log(key);
    this.datakey = this.covidkey;
    console.log(this.flag)
  },
  methods: {
       createSubmitAllChartsDiv(){

    
        
    },
    selectclick(index) {
      //   console.log(data[index]["图形类"].split(','));
      let senddata = [];
      let layoutlist = [];
      layoutlist.push(layout[index]);
      senddata.push(data[index]["图形类"].split(","));
      senddata.push(layoutlist);
      let charts = data[index]["图形类"].split(",") 
      for( var key in charts){
        let temp = charts[key]
        if(this.chartdata.indexOf(temp) == -1)
        {
            this.chartdata.push(temp)
            // console.log(this.chartdata)
        }
      }
      this.$store.commit("setchartArray",this.chartdata)
      this.$store.commit("getimgkey", senddata);
      // var del = document.getElementById("below");
      // if (del) del.parentNode.removeChild(del);
      // let belowDiv = document.createElement("div")
      // belowDiv.setAttribute("id","below")
      // belowDiv.innerHTML = this.chartdata
      // let footer = document.getElementsByClassName("Listfooter")
      // footer.appendChild(belowDiv)
      // console.log(footer)
    },
 
  },
};
</script>
  
  
  <style scoped>
.Leftcontent {
  flex: 0.7 0 700px;
  display: flex;
  margin-left: 1vw;
  margin-right: 5px;
  /* background-color: rgba(239,246,253); */
   background-color: rgb(242,242,242);
  height:85%;
  flex-wrap: wrap;
  overflow: auto;
}
.item {
  width: 25%;
  height: 12vw;
  padding-bottom: 10px;
  padding-left: 10px;
}
img {
  width: 100%;
  height: 100%;
  border-radius:8px;
}
</style>
  