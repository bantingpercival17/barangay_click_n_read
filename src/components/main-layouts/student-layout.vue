<template>
    <div id="loading">
        <loader />
    </div>
    <server-loader v-if="showLoading"></server-loader>
    <!-- loader END -->
    <!-- <sidebar :minisidebar="sidebarmini" @makeminisidebar="onsidebarmini" /> -->
    <main class="main-content">
        <div class="position-relative">
            <!--Nav Start-->
            <PageHeader :fullsidebar="sidebarmini" @makefullsidebar="onfullsidebar" :pageTitle="headerTitle" />
            <!--Nav End-->
        </div>
        <div class="conatiner-fluid content-inner mt-6 py-0">
            <router-view />
        </div>
    </main>
    <!-- Wrapper End-->
</template>
<script>
import loader from '@/components/main-layouts/components/student-loader.vue'
import PageHeader from '@/components/main-layouts/components/student-page-header.vue'
import serverLoader from '@/components/main-layouts/components/server-loader.vue'
import { mapState } from 'vuex'
export default {
    name: 'student-layout',
    components: {
        PageHeader,
        loader,
        serverLoader
    },
    data() {
        return {
            sidebarmini: false,
            user: null
        }
    },
    computed: {
        ...mapState({
            showLoading: state => state.showLoading
        }),
        headerTitle() {
            return this.$route.meta.name
        }
    },
    methods: {
        onsidebarmini(e) {
            this.sidebarmini = e
        },
        onfullsidebar(e) {
            this.sidebarmini = e
        }
    }
}
</script>
