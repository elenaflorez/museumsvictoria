<template>
    <div class="content">
        <div class="parent">
            <img class="image1" src="@/Images/Simple_world_map.png" />
            <span @click="setValue" class="dot image2"></span>
        </div>
        <button @click="setValue">Set Value</button>{{ mapValue }}
    </div>
</template>


<script>
export default {
    //data will return an array
    data() {
        return {
            mapValue: ''
        }
    },

    methods: {
        async setValue () {
            this.mapValue = 'HAHA'
        }
    },
    computed: {
    }

}
</script>