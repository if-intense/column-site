<template>
   <div class="flex-container">
        <main>
        <!-- <img :src="thumbnail && thumbnail.url"> -->
        <picture v-if="thumbnail"> 
        <source media="(min-width: 768px)" type="image/webp" :srcset="`${thumbnail.url}?w=600&fm=webp, ${thumbnail.url}?w=1200&fm=webp 2x`" /> 
        <source media="(max-width: 768px)" type="image/webp" :srcset="`${thumbnail.url}?w=375&fm=webp, ${thumbnail.url}?w=750&fm=webp 2x`" /> 
        <img :src="`${thumbnail.url}?w=1200`" class="thumbnail" alt /> 
        </picture>
        <h1 class="title">{{ title }}</h1>
        <p class="publishedAt">{{ publishedAt }}</p>
        <p class="category">{{ category && category.name }}</p>
        <!-- <div class="post" v-html="body"></div> -->
        <div class="post">
            <h6>投稿内容</h6>
                <p v-html="body"></p>
            
        </div>
    </main>
   </div>
</template>

<<script>

export default {
    async asyncData({ $microcms, params }) {
        const data = await $microcms.get({
            endpoint: 'column',
            contentId: params.slug
        })
        return data
    }
}
</script>

<style lang="scss" scoped>


.flex-container {
    width:100%;
   
}
main {
    width: 85%;
    margin: 0 auto;
    background:rgba(233,233,233,0.7);
    background:url('https://res.cloudinary.com/rfujiwar23/image/upload/v1628067950/ifing/dummy-bg.jpg') no-repeat;
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


</style>