<template>
    <!-- <div style="{ backgroundImage: `url(${banner})` }" > -->
      
  <!-- <section></section> -->
  <!-- <br/> -->
  <!-- <h2>
    EXPLORE DATASET
  </h2> -->
  <div class="overlay-text">
            <h2>Ten Years of VIS Art Program</h2>
</div>

  <img src="@/assets/images/first/home.png" style="height:30vh; width:100%;object-fit: cover;">
  <br/>
  <br/>
  <!-- <button
                 class="filter-button"
                 @click="toggleAllFilters"
                 :class="{ 'selected': isAllSelected() }"
             >
                 Select All
             </button> -->
         <div class="filter-bar">
             
             <div class="filter-label" :style="{'margin-top': '-0.7%'}">Filter by year:</div>
             <div class="filter-options">
                 <button
                     class="filter-button"
                     v-for="(time, index) in times"
                     :key="index"
                     @click="toggleFilter('time', index)"
                     :class="{ 'selected': isSelected('time', index) }"
                 >
                     {{ time }}
                 </button>
             </div>
 
 
         <!-- 添加其他属性的筛选栏 -->
         <!-- 这里以 'art/paper' 为例，你可以继续添加其他属性的筛选栏 -->
   
             <div class="filter-label">Filter by submission type:</div>
             <div class="filter-options">
                 <button
                     class="filter-button"
                     v-for="(artPaper, index) in artPapers"
                     :key="index"
                     @click="toggleFilter('artPaper', index)"
                     :class="{ 'selected': isSelected('artPaper', index) }"
                 >
                     {{ artPaper }}
                 </button>
             </div>
     
             <div class="filter-label">Filter by design genre:</div>
             <div class="filter-options">
                 <button
                     class="filter-button"
                     v-for="(category, index) in designCategories"
                     :key="index"
                     @click="toggleFilter('designCategory', index)"
                     :class="{ 'selected': isSelected('designCategory', index) }"
                 >
                     {{ category }}
                 </button>
             </div>
 
         <!-- <div class="filter-bar">
             <div class="filter-label">Filter by Design Paradigm:</div>
             <div class="filter-options">
                 <button
                     class="filter-button"
                     v-for="(paradigm, index) in designParadigms"
                     :key="index"
                     @click="toggleFilter('designParadigm', index)"
                     :class="{ 'selected': selectedFilters.designParadigm === index }"
                 >
                     {{ paradigm }}
                 </button>
             </div>
         </div> -->
 
         <!-- <div class="filter-bar">
             <div class="filter-label">Filter by Design Technique:</div>
             <div class="filter-options">
                 <button
                     class="filter-button"
                     v-for="(technique, index) in designTechniques"
                     :key="index"
                     @click="toggleFilter('designTechnique', index)"
                     :class="{ 'selected': selectedFilters.designTechnique === index }"
                 >
                     {{ technique }}
                 </button>
             </div>
         </div> -->
 
             <div class="filter-label">Filter by design task:</div>
             <div class="filter-options">
                 <button
                     class="filter-button"
                     v-for="(purpose, index) in whatPurpose"
                     :key="index"
                     @click="toggleFilter('whatPurpose', index)"
                     :class="{ 'selected': isSelected('whatPurpose', index) }"
                 >
                     {{ purpose }}
                 </button>
             </div>
             <div class="filter-label">Filter by design field:</div>
             <div class="filter-options">
                 <button
                     class="filter-button"
                     v-for="(field, index) in whereField"
                     :key="index"
                     @click="toggleFilter('whereField', index)"
                     :class="{ 'selected':isSelected('whereField', index)  }"
                 >
                     {{ field }}
                 </button>
             </div>

         </div>
 
       
             
        
 
         <!-- 在这里添加其他属性的筛选栏 -->
 
         <!-- <div class="data-container">
             <div v-for="(item, index) in filteredData" :key="index">
                
                 <h2>{{ item.name }}</h2>
                 <p>Time: {{ item.time.join(', ') }}</p>
                 <p>Art/Paper: {{ item.artPaper.join(', ') }}</p>
                 <p>Design Category: {{ item.designCategory.join(', ') }}</p>
                 <p>Design Paradigm: {{ item.designParadigm.join(', ') }}</p>
                 <p>Design Technique: {{ item.designTechnique.join(', ') }}</p>
                 <p>What Purpose: {{ item.whatPurpose.join(', ') }}</p>
                 <p>Where Field: {{ item.whereField.join(', ') }}</p>
           
             </div>
         </div> -->
         <section class="Articles" id="Articles" :style="{ 'padding': '0px'}">
         <!-- <p>{{data0.areaAbstact[Language]}}</p> -->
         <ul class="cards" >
             <li class="card" v-for="(item, index) in filteredData" :key="index" >
             <!-- <img :src="item.img" alt="img"  style="aspect-ratio: 16 / 12;"> -->
             <img v-if="item.images" :src="require('@/assets/images/each/'+item.images )"  alt="img"   style="aspect-ratio: 16 / 9;"> 
             <p>
                <div class="text-container">
                    <div class="left-block"><span style="text-align: left;font-size: 1.2rem;font-weight: bolder;">{{ item.name  }}</span>
                    </div>
                    <div class="right-block">
                            <span style="float: right;">{{ item.time ? item.time.join(', ') : '' }}</span>
                            <!-- <span style="float: right;">2013</span> -->
                        </div>
                </div></p>
             
             <p style="line-height:1.2 ;font-size: 0.9rem;">{{ item.author ? item.author  : '' }} </p>
                 <p style="line-height: 1.2 ;font-size: 0.9rem;">{{ item.artPaper? item.artPaper.join(', ')  : '' }}</p>
                 <p :style="{'margin-top':'15px','margin-left':'-6px'}">
                    <table class="table1">
                    <tbody style=" vertical-align: top;width:100%;">
                        <tr :style="{'margin-top':'15px'}" v-if="item.designCategory.length > 0">
                            <td><span class="custom1-tag">Design genre:</span></td>
                            <td style="text-align: right;"><span class="custom-tag" :style="{'background-color':'#FCC400'}" v-for="(item1, index1) in item.designCategory" :key="index" >{{ item1 }}</span></td>
                        </tr>
                        <tr :style="{'margin-top':'1px'}" v-if="item.designTechnique.length > 0">
                            <td><span class="custom1-tag">Design technique:</span></td>
                            <td style="text-align: right;"><span class="custom-tag" :style="{'background-color':'#FC8800'}" v-for="(item1, index1) in item.designTechnique" :key="index" >{{ item1 }}</span></td>
                        </tr>
                        <tr :style="{'margin-top':'1px'}" v-if="item.whatPurpose.length > 0">
                            <td><span class="custom1-tag">Design task:</span></td>
                            <td style="text-align: right;"><span class="custom-tag" :style="{'background-color':'#55B8FF'}" v-for="(item1, index1) in item.whatPurpose" :key="index" >{{ item1 }}</span></td>
                        </tr>
                        <tr :style="{'margin-top':'1px'}" v-if="item.whereField.length > 0">
                            <td><span class="custom1-tag">Design field:</span></td>
                            <td style="text-align: right;"><span class="custom-tag" :style="{'background-color':'#1987e9'}" v-for="(item1, index1) in item.whereField" :key="index" >{{ item1 }}</span></td>
                        </tr>

                        <tr :style="{'margin-top':'1px'}" v-if="item.datatype.length > 0">
                            <td><span class="custom1-tag">Special input:</span></td>
                            <td style="text-align: right;"><span class="custom-tag" :style="{'background-color':'#B1B1B1','color':'#414141'}" v-for="(item1, index1) in item.datatype" :key="index" >{{ item1 }}</span></td>
                        </tr>
                        
                    </tbody>
                 </table>
                </p>




                 <!-- <p :style="{'margin-top':'15px','margin-left':'-4px'}" v-if="item.designCategory">
                    <span class="custom1-tag">Art/Paper:</span><span class="custom-tag" :style="{'background-color':'#FCC400'}" v-for="(item1, index1) in item.designCategory" :key="index" >{{ item1 }}</span>
                </p>
                 <p :style="{'margin-top':'1px','margin-left':'-4px'}" v-if="item.designTechnique">
                    <span class="custom1-tag">DesignTechnique:</span><span class="custom-tag" :style="{'background-color':'#FC8800'}" v-for="(item1, index1) in item.designTechnique" :key="index" >{{ item1 }}</span>
                 </p>
                 <p :style="{'margin-top':'1px','margin-left':'-4px'}" v-if="item.whatPurpose">
                    <span class="custom1-tag">WhatPurpose:</span><span class="custom-tag" :style="{'background-color':'#55B8FF'}" v-for="(item1, index1) in item.whatPurpose" :key="index" >{{ item1 }}</span>
                 </p> -->
                 <!-- <p :style="{'margin-top':'1px','margin-left':'-4px'}" v-if="item.whereField">
                    <span class="custom-tag" :style="{'background-color':'#0478CD'}" v-for="(item1, index1) in item.whereField" :key="index" >{{ item1 }}</span>
                 </p>
                 <p :style="{'margin-top':'1px','margin-left':'-4px'}" v-if="item.designParadigm">
                    <span class="custom-tag" :style="{'background-color':'#0D9B13'}" v-for="(item1, index1) in item.designParadigm" :key="index" >{{ item1 }}</span>
                 </p> -->
                 <!-- <p :style="{'margin-top':'1px','margin-left':'-4px'}" v-if="item.datatype">
                    <span class="custom1-tag">DataType:</span><span class="custom-tag" :style="{'background-color':'#B1B1B1','color':'#414141'}" v-for="(item1, index1) in item.datatype" :key="index" >{{ item1 }}</span>
                 </p> -->
                 
                  
                  <!-- <p style="line-height:1.2 ;font-size: 0.9rem;">{{ item.author ? item.author  : '' }} </p>
                 <p style="line-height: 1.2 ;font-size: 0.9rem;">{{ item.artPaper? item.artPaper.join(', ')  : '' }}</p>
                 <p :style="{'margin-top':'15px'}" v-if="item.designCategory">
                    <span class="custom-tag" :style="{'background-color':'#FCC400'}" v-for="(item1, index1) in item.designCategory" :key="index" >{{ item1 }}</span>
               
                 <span  :style="{'margin-top':'1px'}" v-if="item.designTechnique">
                    <span class="custom-tag" :style="{'background-color':'#FC8800'}" v-for="(item1, index1) in item.designTechnique" :key="index" >{{ item1 }}</span>
                 </span >
                 <span  :style="{'margin-top':'1px'}" v-if="item.whatPurpose">
                    <span class="custom-tag" :style="{'background-color':'#55B8FF'}" v-for="(item1, index1) in item.whatPurpose" :key="index" >{{ item1 }}</span>
                 </span >
                 <span  :style="{'margin-top':'1px'}" v-if="item.whereField">
                    <span class="custom-tag" :style="{'background-color':'#0478CD'}" v-for="(item1, index1) in item.whereField" :key="index" >{{ item1 }}</span>
                 </span >
                 <span  :style="{'margin-top':'1px'}" v-if="item.designParadigm">
                    <span class="custom-tag" :style="{'background-color':'#0D9B13'}" v-for="(item1, index1) in item.designParadigm" :key="index" >{{ item1 }}</span>
                 </span >
                 <span :style="{'margin-top':'1px'}" v-if="item.datatype">
                    <span class="custom-tag" :style="{'background-color':'#B1B1B1','color':'#414141'}" v-for="(item1, index1) in item.datatype" :key="index" >{{ item1 }}</span>
                 </span>
                </p> -->
                 





                
                 <!-- <p>{{ item.designParadigm?item.designParadigm.join(', ')  : '' }}</p> -->
                 <!-- <p> {{ item.designTechnique?item.designTechnique.join(', ')  : '' }}</p>
                 <p> {{ item.whatPurpose?item.whatPurpose.join(', ')  : '' }}</p>
                 <p> {{item.whereField? item.whereField.join(', ')  : '' }}</p> -->
           </li>
         </ul>
       </section>
   
<!-- </div> -->
    
    
 
 </template>
 
 <script>
 import "@/assets/css/style.css";
 import  axios from 'axios'
 export default {
    computed:{
        imgPath(name){
            return '@/assets/images/each/'+name +'.png'
        }
    },
   
   data(){
    
    return{
        // t:"XEPA", 
        banner:require('@/assets/images/first/a.jpg'),        
        times:['2013', '2014', '2015', '2016', '2017', '2018', '2019', '2020', '2021', '2022'],
        artPapers:['art show', 'paper', 'pictorial/annotated portfolio'],
        designCategories:['installation', 'interactive interface', 'static image', 'artifact', 'algorithm/tool', 'video', 'event'],
        designParadigms: ['data sonification', 'generative art', 'ambient display', 'speculative design', 'digital humanism', 'algorithmic art', 'data physicalization', 'computational aesthetic evaluation', 'neuroaesthetics', 'physical computing', 'computer art', 'graphic art', 'abstract cinema/cinematography', 'experimental animation', 'digital photograph', 'electronic art', 'digital fabrication', 'spatial narrative', 'neo-concrete art', 'aministic design', 'glitch art', 'data humanization', 'parametric design', 'experimental media archeology', 'abstract animation', 'evolutionary algorithm', 'digital art', 'generative artifact', 'data manifestation', 'wearable art'],
        // designTechniques: ["Technique 1", "Technique 2", "Technique 3"],
        whatPurpose:[ 'experiment', 'inform', 'engage', 'provoke', 'reveal', 'criticize', 'equip', 'analyze', 'advocate', 'socialize', 'witness', 'archive', 'empower', 'commemorate','not specified'],
        whereField:['environmental sciences & ecology', 'urban studies', 'social issues', 'biology', 'news & media', 'art', 'computer science', 'language & literature', 'health & well-being', 'physics', 'astronomy', 'business', 'daily life', 'psychology', 'politics', 'education', 'math', 'history','not specified'],
        // 添加其他属性的选项数组
        selectedFilters: {
            time: [],
            artPaper: [],
            designCategory: [],
            designParadigm: [],
            designTechnique: [],
            whatPurpose: [],
            whereField: [],
            // 添加其他属性的选中状态
        },
        jsonData: [
            {
                // id: 1,
                name: "Item 1",
                time: ["Time 1", "Time 2"],
                artPaper: ["Art/Paper 1"],
                designCategory: ["Category 1"],
                designParadigm: ["Paradigm 1"],
                designTechnique: ["Technique 1"],
                whatPurpose: ["Purpose 1"],
                whereField: ["Field 1"],
                // 添加其他属性的数据
            },
            {
                // id: 2,
                name: "Item 2",
                time: ["Time 2"],
                artPaper: ["Art/Paper 2", "Art/Paper 3"],
                designCategory: ["Category 2"],
                designParadigm: ["Paradigm 2"],
                designTechnique: ["Technique 2"],
                whatPurpose: ["Purpose 2"],
                whereField: ["Field 2"],
                // 添加其他属性的数据
            },
            // 添加更多数据项
            {
                // id: 2,
                name: "Item 2",
                time: ["Time 2"],
                artPaper: ["Art/Paper 2", "Art/Paper 3"],
                designCategory: ["Category 2","Category 1"],
                designParadigm: ["Paradigm 2"],
                designTechnique: ["Technique 2"],
                whatPurpose: ["Purpose 2"],
                whereField: ["Field 2"],
                // 添加其他属性的数据
            },
        ],
        filteredData: [] // 存储筛选后的数据
    } 
   },
             created() {
                 // 初始化时默认全选
                 this.selectAllFilters();
                 // 一开始默认展示所有数据
                //  const jsonFilePath = '../output.json';
                // const jsonFilePath = '/Collection/output.json'
                const jsonFilePath = '/output.json'
                // const jsonFilePath = `${process.env.BASE_URL}output.json`;
                console.log(jsonFilePath)
                 axios
                   .get(jsonFilePath)
                   .then((response) => {
                    
                     console.log( response.data[0])
                     console.log(this.jsonData)
                     this.jsonData = response.data;
                     this.filteredData = this.jsonData;
                     // this.jsonData=[response.data]
                     console.log(this.jsonData)
                     
                   })
                   .catch((error) => {
                     console.error('Error reading local JSON file:', error);
                   });
                   
                 
             },
             methods: {
                isSelected(filterType, index) {
                    // 根据filterType和index检查按钮是否选中
                    return this.selectedFilters[filterType].includes(index);
                },
                 toggleAllFilters() {
                     // 切换全选状态
                     if (this.isAllSelected()) {
                         this.deselectAllFilters();
                     } else {
                         this.selectAllFilters();
                     }
                     this.applyFilters(); // 应用筛选
                 },
                 selectAllFilters() {
                     // 选中所有筛选条件
                     this.selectedFilters.time = [];
                     this.selectedFilters.artPaper = [];
                     this.selectedFilters.designCategory = [];
                     this.selectedFilters.designParadigm = [];
                     this.selectedFilters.designTechnique = [];
                     this.selectedFilters.whatPurpose = [];
                     this.selectedFilters.whereField = [];
                     // 添加其他属性的选中状态
                 },
                 deselectAllFilters() {
                     // 取消选中所有筛选条件
                     this.selectedFilters.time = -1;
                     this.selectedFilters.artPaper = -1;
                     this.selectedFilters.designCategory = -1;
                     this.selectedFilters.designParadigm = -1;
                     this.selectedFilters.designTechnique = -1;
                     this.selectedFilters.whatPurpose = -1;
                     this.selectedFilters.whereField = -1;
                     // 添加其他属性的选中状态
                 },
                 isAllSelected() {
                     // 检查是否所有筛选条件都已选中
                     return (
                         this.selectedFilters.time.length === 0 &&
                         this.selectedFilters.artPaper.length === 0 &&
                         this.selectedFilters.designCategory.length === 0 &&
                         this.selectedFilters.designParadigm.length === 0 &&
                         this.selectedFilters.designTechnique.length === 0 &&
                         this.selectedFilters.whatPurpose.length === 0 &&
                         this.selectedFilters.whereField.length === 0
                         // 检查其他属性的选中状态
                     );
                 },
                 toggleFilter(filterType, index) {
                     // 切换单个筛选条件
                    //  if (this.selectedFilters[filterType] === index) {
                    //      this.selectedFilters[filterType] = null;
                    //  } else {
                    //      this.selectedFilters[filterType] = index;
                    //  }
                    const selectedFilters = this.selectedFilters[filterType];
                    const selectedIndex = selectedFilters.indexOf(index);

                    if (selectedIndex === -1) {
                    // 如果未选中，则添加到已选中列表
                    selectedFilters.push(index);
                    } else {
                    // 如果已选中，则从已选中列表中移除
                    selectedFilters.splice(selectedIndex, 1);
                    }
                     this.applyFilters(); // 应用筛选
                 },
                 applyFilters() {
                     // 执行筛选操作
                     this.filteredData = this.jsonData.filter((item) => {
 
 // if (Array.isArray(item.designCategory)) {
 //   console.log('item.designCategory is an array',item);
 // } else {
 //   console.log('item.designCategory is not an array');
 // }
 
                         const timeFilter =
                             this.selectedFilters.time.length === 0 ||
                            //  item.time.some((time) => time === this.times[this.selectedFilters.time]);
                             this.selectedFilters.time.some((selectedIndex) => item.time.includes(this.times[selectedIndex]));
                         const artPaperFilter =
                             this.selectedFilters.artPaper.length === 0 ||
                             this.selectedFilters.artPaper.some((selectedIndex) => item.artPaper.includes(this.artPapers[selectedIndex]));
                         const designCategoryFilter =
                             this.selectedFilters.designCategory.length === 0 ||
                             this.selectedFilters.designCategory.some((selectedIndex) => item.designCategory.includes(this.designCategories[selectedIndex]));
                         const designParadigmFilter =
                             this.selectedFilters.designParadigm.length === 0 ||
                             this.selectedFilters.designParadigm.some((selectedIndex) => item.designParadigm.includes(this.designParadigms[selectedIndex]));
                         // const designTechniqueFilter =
                         //     this.selectedFilters.designTechnique === null ||
                         //     item.designTechnique.some((technique) =>
                         //         technique === this.designTechniques[this.selectedFilters.designTechnique]
                         //     );
                         const whatPurposeFilter =
                             this.selectedFilters.whatPurpose.length === 0 ||
                             this.selectedFilters.whatPurpose.some((selectedIndex) => item.whatPurpose.includes(this.whatPurpose[selectedIndex]));
                         const whereFieldFilter =
                             this.selectedFilters.whereField.length === 0 ||
                             this.selectedFilters.whereField.some((selectedIndex) => item.whereField.includes(this.whereField[selectedIndex]));
                         // 添加其他属性的筛选逻辑
                         return (
                             timeFilter &&
                             artPaperFilter &&
                             designCategoryFilter &&
                             designParadigmFilter &&
                             // designTechniqueFilter &&
                             whatPurposeFilter &&
                             whereFieldFilter
                             // 添加其他属性的筛选逻辑
                         );
                     });
                 }
               }
   
 }
 </script>
 
 <style scoped>
.overlay-text {
    position: absolute;
    top: 20%;
    left: 50%;
    transform: translate(-50%, -50%);
    /* background-color: rgba(0, 0, 0, 0.7); */
    color: white;
    /* padding: 10px; */
    text-align: center;
    line-height:50px;
    font-size: 30px;
    font-weight: bold;
    width:100%;
}
@media (max-width: 400px) {
  .overlay-text {
    font-size: 20px;
  }
}
 .table1{
    width:100%;
 }
 .table1 td{
    border: 1px solid transparent; 
 }
 .custom1-tag {

            padding: 3px 10px; /* 内边距，可根据需要调整 */
            font-size: 0.7rem;
            /* margin:3px; */
            margin-right:3px;
            margin-left: -4px;
            font-weight: normal;
            white-space: nowrap;
           
            }
 .custom-tag {
            text-align: right;
            background-color: #3498db; /* 背景颜色 */
            border-radius: 6px; /* 圆角 */
            color: white; /* 字体颜色 */
            padding: 3px 10px; /* 内边距，可根据需要调整 */
            font-size: 0.7rem;
            margin:3px;
            white-space: normal; /* 默认的 white-space 值，允许内容换行 */
            word-wrap: break-word; /* 当内容太长时，允许单词内换行 */
            display: inline-block; /* 使元素以内联块元素显示 */
            }
 .text-container {
            display: flex;
            justify-content: space-between;
        }
        .left-block {
            flex: 5;
        }
        .right-block {
            flex: 1;
            text-align: right;
        }
 .filter-bar {
             
             background-color: #ffffff;
             padding: 30px;
             /* border: 1px solid #ddd; */
             border-radius: 20px;
             margin-left: 6%;
             margin-right: 6%;
             box-shadow: 0px 5px 14px rgba(182, 182, 182, 0.2); /* 添加底部阴影，可以根据需要调整参数 */
             
         }
         .filter-label {
             font-weight: bold;
             text-align: left;
             margin-top: 1%;
             margin-bottom: 0.2%;
         }
         .filter-options {
             display: flex;
             gap: 10px;
             /* display: flex; */
            flex-wrap: wrap;
         }
         .filter-button {
             background-color: transparent;
             border: 1px solid #969696;
             border-radius: 5px;
             padding: 5px 10px;
             color: #969696;
             cursor: pointer;
         }
         .selected {
             background-color: #969696;
             color: #fff;
         }
         .data-container {
             border: 1px solid #ddd;
             padding: 10px;
             border-radius: 5px;
         }
 </style>
 