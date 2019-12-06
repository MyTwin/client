<template>
    <div>
        <div class="box-image">
            <div class="image-wrapper">
                <img :src="gcs">
            </div>
            <div class="image-wrapper">
                <img :src="resultImage">
                <div class="celeb-name">
                    <h2>{{ name }}</h2>
                    <h3>{{ confidence }}%</h3>
                </div>
            </div>
        </div>
        <div class="button-wrapper">
            <containerForm @getData="setImage"></containerForm>
            <button class="btn" @click="postTimeline">Post Timeline</button>
        </div>
    </div>
</template>

<script>
    import containerForm from './containerForm'
    import axios from 'axios'

export default {
    data() {
        return {
            userImage: '',
            resultImage: '',
            name: '',
            confidence: '',
            gcs: '',
            baseUrl: 'http://localhost:3000'
        }
    },
    components:{
      containerForm
    },
    props: ['srcUser', 'srcResult'],
    methods: {
        setImage(v) {
            console.log(v)
            this.resultImage = v.celebImg
            this.name = v.celebName
            this.confidence = v.celebConfidence
            this.gcs = v.gcs
        },
        postTimeline() {
            let access_token = localStorage.getItem('token')
            axios({
                url: `${this.baseUrl}/post`,
                method: 'post',
                data: {
                    image: this.gcs,
                    resultImage: this.resultImage,
                    caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Optio maiores odit omnis harum recusandae non necessitatibus quam tempora laborum! Ipsa cupiditate natus ducimus culpa nostrum sequi voluptatem voluptatum atque quae!'
                },
                headers: {
                    access_token
                }
            })
                .then(({data}) => {
                    this.$emit('dataCreate')
                    this.$emit('goTimeline', true)
                })
                .catch(err => {
                    Swal.fire({
                        icon: 'error',
                        title: 'Oops...',
                        text: `${err.response.data.message}`
                    })
                })
        }
    }
}
</script>

<style scoped>
    .box-image {
        width: 80vw;
        height: calc(100vh - 3rem);
        margin: 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .image-wrapper {
        position:relative;
        width: 400px;
        height: 500px;
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        box-shadow: 0px 8px 10px rgba(0, 0, 0, 0.6);
        cursor: pointer;
    }
    .celeb-name {
        position: absolute;
        z-index: 2;
        width: 100%;
        padding: 1rem 0;
        background-color: rgba(0, 0, 0, 0.4);
        bottom: 0;
        text-align: center;
        color: #fff;
    }
    .image-wrapper img {
        flex-shrink: 0;
        min-width: 100%;
        min-height: 100%;
    }

    .upload-btn-wrapper {
        position: relative;
        overflow: hidden;
        display: inline-block;
    }

    .button-wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
  .btn {
    width: 200px;
    border: 2px solid gray;
    color: gray;
    background-color: white;
    padding: 8px 20px;
    border-radius: 8px;
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 2rem;
  }

</style>