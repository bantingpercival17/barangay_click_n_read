<template>
    <div>
        <!-- <button class="btn btn-primary btn-sm">Initialize SCORM</button>
        <button class="btn btn-primary btn-sm">Initialize SCORM</button> -->
        <div v-if="showContent" class="display-scorm">
            <iframe :src="contentUrl" width="100%" height="500"></iframe>
        </div>
    </div>
</template>
<script>
/* import SCORM from 'pipwerks-scorm-api-wrapper' */
export default {
    data() {
        return {
            showContent: true
        }
    },
    mounted() {
        /* SCORM.init() */
    },
    props: {
        contentUrl: String
    }
}
</script>