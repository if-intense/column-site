<template>
  <div class="flex-container">
    
   
    <div class="container">
      <div class="row">
        <div class="col-lg-9 col-md-9 sm-order-2">
          <div class="banner">
            i-column
          </div>
          <div class="main-area">
            <div class="column-list">
              <h6>COLUMN<span>コラム</span></h6>
              <ul>
                <li v-for="content in contents" :key="content.id">
                  <nuxt-link :to="`${content.id}`">
                    {{ content.title }}
                  </nuxt-link>
                </li>
              </ul>

            </div>            
          </div>
        </div>
        <div class="col-lg-3 col-md-3 sm-order-1">
         <h3> List Up</h3>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>



export default {
  async asyncData ({ $microcms }) {
    const data = await $microcms.get({
      endpoint: 'column'
    })
    return data
  }
}
</script>

<style lang="scss" scoped>


.flex-container {
    width:100%;
    background:url('https://res.cloudinary.com/rfujiwar23/image/upload/v1628067950/ifing/dummy-bg.jpg') no-repeat;
    background-position: center;
    background-size: cover;
    height: 100vh;
}

.nav {
  background: #333333;
  height: 60px;
}
main {
    width: 85%;
    margin: 0 auto;
    background:rgba(233,233,233,0.7);
   
    // background:red;
    height:100vh;
}

.title {
    color:red;
}

.post {
    background: rgb(255, 255, 255);
    box-shadow: 3px 3px 6px #9a9a9a;
    width: 90%;
    margin:50px auto;
    p {
        padding: 10px 20px;
    }
}
.container .banner {
  aspect-ratio: 16/6;
  // background:url();
  background-color: antiquewhite;
}

.main-area {
  background: crimson;
  height: 50vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.column-list {
  background: #F0F3F5;
  // height: 100%;
  width: 95%;
}



</style>