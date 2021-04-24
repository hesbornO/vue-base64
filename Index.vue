<template>
<div>
    <div class="container mt-10">
        <div class="card bg-white">
            <img style="" :src="image" alt="">
            <input type="file" @change="handleImage" class="custom-input" accept="image/*">

        </div>

    </div>
</div>
</template>
<style>
    @import '@/assets/style/main.css';
</style>
<script>
export default {
    name: 'home',
    data(){
        return {
            image: ''
        }
    },
    methods: {
        handleImage(e){
            const selectedImage = e.target.files[0];
            this.createBase64Image(selectedImage);            
        },
        createBase64Image(fileObject) {
            const reader = new FileReader();
            reader.onload = (e) => {
                this.image = e.target.result;
            };
            reader.readAsBinaryString(fileObject);
        }
    }
}
</script>
