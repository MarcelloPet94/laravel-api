<template>
<div class="bg_blog">
    <div class="article_container">

        <div class="article" v-for="(article,index) in allArticle" :key="index">
            <h2>{{article.title}}</h2>
            <div class="media_cont"><img :src="'storage/' + article.image"></div>
            <div class="argument_cont">
                <p>{{article.content}}</p>
            </div>    
        </div>              
    </div>
</div>
</template>

<script>

export default{

    name: "App",
    data(){
        return{
            allArticle : []
        }    
    },
    created(){
        axios
        .get('/api/posts')
        .then((response)=> {
         this.allArticle = response.data;
        })
    }
    
}

</script>

<style lang="scss" scoped>
*
{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.bg_blog
{
    background-color: rgb(177, 204, 255);

    .article_container
    {
        background-color: #fff;
        margin: 0 auto;
        width: 800px;
        padding: 24px;

        .article
        {
            padding: 24px 0;
            border-bottom: 1px solid lightgray;
        }
    }

    .media_cont
    {
        img
        {
            width: 100%;
        }
    }
}
</style>