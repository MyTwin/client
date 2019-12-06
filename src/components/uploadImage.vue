<template>
    <form @submit.prevent="startUpload">
        <div class="upload-btn-wrapper mx-4 my-4">
            <button class="btn">Upload Image</button>
            <input type="file" ref="file" name="myfile" @change.prevent="selectImage" />
        </div>
    </form>
</template>

<script>
import Swal from 'sweetalert2'
import axios from 'axios'

export default {
  data: function () {
    return {
      image: null  
      
    }
  },
  methods: {
    selectImage: function(e){
        Swal.showLoading()
        let formData = new FormData();
        this.image = this.$refs.file.files[0];
        formData.append('image', this.image);

        axios.post( 'http://localhost:3000/image/upload',
          formData,
          {
            headers: {
                'Content-Type': 'multipart/form-data'
            }
          }
        ).then(({data}) => {
          Swal.close()
          this.$emit('sendImage', data)
        })
        .catch(function(){
          Swal.close()
          Swal.fire({
              icon: 'error',
              title: 'Oops...',
              text: `${err.response.data.message}`
          })
        });
    }
  }
}
</script>

<style scoped>
  .upload-btn-wrapper {
    position: relative;
    overflow: hidden;
    display: inline-block;
  }

  .btn {
    border: 2px solid gray;
    color: gray;
    background-color: white;
    padding: 8px 20px;
    border-radius: 8px;
    font-size: 20px;
    font-weight: bold;
  }

  .upload-btn-wrapper input[type=file] {
    font-size: 100px;
    position: absolute;
    left: 0;
    top: 0;
    opacity: 0;
  }
</style>