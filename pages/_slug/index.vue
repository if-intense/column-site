<template>
    <main>
        
        <h1 class="title">{{ title }}</h1>
        <p class="publishedAt">{{ publishedAt }}</p>
        <!-- <p class="category">{{ category }}</p> -->
        <!-- <div class="post" v-html="body"></div> -->
        <div class="post">
            <h6>投稿内容</h6>
                <p v-html="body"></p>
            
        </div>
    </main>
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

main {
    width: 85%;
    margin: 0 auto;
    background:rgba(233,233,233,0.7);
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