<template lang="">
    <div class="container">
        <div class="rectangle"></div>
        <div class="card_container"> 
            <div class ="user_container">
                <div class ="image_container">
                    <img class="pfp" :src="props.user.avatar"/>
                </div>
                <div class ="info_container">
                    <span style="color: grey;">
                        #{{ props.user.id }} 
                        <!-- #1 -->
                    </span>
                    <span><h3><b>
                        {{props.user.first_name}}
                        {{props.user.last_name}}
                        <!-- Neymar Pai -->
                    </b></h3></span>
                    <span style="color: grey;">
                        {{props.user.email}}
                        <!-- akira.takiroto@gmail.com -->
                    </span>
                </div>  
            </div>
            <div class ="options_container">
                <RouterLink :to="'/userEdit/'+ props.user.id"><img src="\src\assets\edit_icon.svg"/></RouterLink>
                <img src="\src\assets\trash_icon.svg"/>
                <RouterLink :to="'/user/'+ props.user.id"><img src="\src\assets\view_icon.svg"/></RouterLink>
            </div>
        </div>
    </div>
</template>

<script setup>

const props = defineProps({ user: Object})

</script>

<style scoped>

* {
    font-family: Montserrat;
}

.container {
    display: flex;
    flex:1;
}

.card_container {
    display:flex;
    align-items: center;
    background-color: #F7F7F7;
    height: 120px;
    border-radius: 10px;
    justify-content: space-between;
    max-width: 588px;
    width: 100%;
}

.rectangle {
    margin-top: 20px;
    background-color: black;
    width: 4px;
    height: 20px;
}

.user_container {
    column-gap: 30px;
    display: flex;
}

.image_container {
    margin: 0px 0px 0px 30px;
    width: 80px;
    height: 80px;
    background-color: rgb(255, 255, 255);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.pfp {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 10px;
}

.info_container {
    display:flex;
    flex-direction: column;
    align-items: start;
}

.info_container span {
    padding: 5px;
}

.options_container {
    margin: 0px 30px 0px 0px;
    align-items: end;
}

.options_container img {
    height: 17px;
    padding: 8px;
}

</style>