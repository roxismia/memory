<template>
    <div class="header">
        <div class="container">
            <div class="header__row">
                <div v-if="logo" class="logo">
                    <p>Логотип</p>
                </div>
                <div class="menu">
                    <ul>
                        <li v-for="(v, k) in arr" :key="k">{{ k }}</li>
                    </ul>
                </div>
                <input v-model="message">
            </div>
            <div class="message">{{ message }}</div>
            <img v-if="img1 !== null" :src="img1" alt="">
            <!-- <img src="../assets/appel.jpg" alt=""> -->
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
        logo: true,
        arr:
        {
                "яблоко": "appel.jpg",
                "груша": "grusha.jpg",
                "лимон": "laim.jpg"
        },
        message: "привет",
        img2: ""
        }
    },

    computed: {
        img1 () {
            for(let [key, value] of Object.entries(this.arr)) {
                if (key === this.message) {
                    console.log(key)
                    return value
                }
            }
            return null
    },
}


    
}
</script>

<style>
.header {
    background: #e5cbcb;
}
.container {
    width: 70%;
}

.header__row {

    display: flex;
}

.logo {
    font-size: 50px;
}
</style>
{ image: 'appel.jpg', revealed:false, matched: false },
{ image: 'appel.jpg', revealed: false, matched: false},
{ image: 'grusha.jpg', revealed: false, matched: false },
{ image: 'grusha.jpg', revealed: false, matched: false },
{ image: 'appel.jpg', revealed: false, matched: false },
{ image: 'appel.jpg', revealed: false, matched: false },
{ image: 'grusha.jpg', revealed: false, matched: false },
{ image: 'grusha.jpg', revealed: false, matched: false },
{ image: 'grusha.jpg', revealed: false, matched: false },
{ image: 'grusha.jpg', revealed: false, matched: false },
{ image: 'grusha.jpg', revealed: false, matched: false },
{ image: 'grusha.jpg', revealed: false, matched: false },
