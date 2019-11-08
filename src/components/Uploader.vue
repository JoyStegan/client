<template>
    <div>
        <p class="text-center my-2 pt-5">Upload your picture here and get translated text instantly!</p>
        
        <form @submit.prevent="uploadImage">
            <div class="container">
                <div class="row">
                <div class="col-md-12">
                    <div class="form-group">
                    <div class="dropzone-wrapper">
                        <div class="dropzone-desc">
                        <i class="glyphicon glyphicon-download-alt"></i>
                        <p>Choose an image file or drag it here.</p>
                        </div>
                        <b-form-file v-model="file" class="mt-3 dropzone" plain></b-form-file>
                    </div>
                    <div class="mt-3">Selected file: {{ file ? file.name : '' }}</div>
                    </div>
                </div>
                <div class="row ml-1" style="width: 100%">
                    <div class="col-md-8">
                    <label class="control-label mr-2">Select language</label>
                    <b-form-select v-model="langImg" :options="options" style="width: 300px;"></b-form-select>
                    </div>
                    <div class="col-md-4 d-flex flex-row-reverse">
                    <div>
                        <button type="submit" class="btn btn-primary pull-right ml-3">Upload</button>
                    </div>
                    </div>
                </div>
                </div>
            </div>
            </form>
    </div>
</template>

<script>
import axios from "../../config/axios";
import Swal from 'sweetalert2'

export default {
  name: "Uploader",
  data() {
    return {
      file: null,
      langImg: null,
      options: [
        { value: null, text: "Please select image language" },
        { value: "Arabic", text: "Arabic" },
        { value: "Japanese", text: "Japanese" },
        { value: "Korean", text: "Korean" },
        { value: "Russian", text: "Russian" },
        { value: "English", text: "English" },
        { value: "French", text: "French" },
        { value: "German", text: "German" },
        { value: "Spanish", text: "Spanish" }
      ]
    };
  },
  methods: {
    uploadImage() {
      Swal.fire({
        title: 'Uploading ...',
        onBeforeOpen: () => {
          Swal.showLoading()
        }
      })
      const formData = new FormData();
      formData.append("url", this.file);
      formData.append("lang", this.langImg)
      axios({
        method: "POST",
        url: "/translations",
        headers: {
          "Content-Type": "multipart/form-data"
        },
        data: formData
      })
        .then(({ data }) => {
          this.file = null;
          this.langImg = null;
          console.log(data);
          Swal.close()
          this.$emit('go', 'home')
        })
        .catch(({ response }) => {
          console.log(response.data);
          Swal.close()
        })
    }
  }
};
</script>

<style>
.container {
  padding: 50px 200px;
}
.dropzone-wrapper {
  border: 2px dashed #91b0b3;
  color: #92b0b3;
  position: relative;
  height: 150px;
}
.dropzone-desc {
  position: absolute;
  margin: 0 auto;
  left: 0;
  right: 0;
  text-align: center;
  width: 40%;
  top: 50px;
  font-size: 16px;
}
.dropzone,
.dropzone:focus {
  position: absolute;
  outline: none !important;
  width: 100%;
  height: 150px;
  cursor: pointer;
  opacity: 0;
}
.dropzone-wrapper:hover,
.dropzone-wrapper.dragover {
  background: #ecf0f5;
}
</style>