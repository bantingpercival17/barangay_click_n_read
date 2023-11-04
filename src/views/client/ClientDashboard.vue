<template>
    <div v-if="isLoading">
        <SubjectLoading />
    </div>
    <div v-else>
        <p class='display-6 fw-bolder text-primary'>BOOK LIST</p>
        <div class="form-sort row">
            <div class="col-md">
                <small class="fw-bolder">SEARCH BOOK NAME</small>
                <input type="text" class="form-control form-control-sm border border-primary">
            </div>
        </div>
        <div class="row">
            <div class="col-lg-4 col-md-6 col-xs-12" v-for="(data, index) in subjectLists" :key="index">
                <router-link :to="{ name: 'student-layout.subject-view-lesson', params: { subject: encrypt(data.id) } }">
                    <div class="card bg-primary">

                    </div>
                </router-link>

            </div>
        </div>
    </div>
</template>
<script>
import Swal from 'sweetalert2'
import { LOGOUT_ACTION, GET_USER_TOKEN, IS_USER_AUTHENTICATE_GETTER, SHOW_LOADING_MUTATION } from '@/store/storeConstants'
import { mapActions, mapGetters, mapMutations } from 'vuex'
import SubjectLoading from './loading-view/SubjectsLoading.vue'
import axios from 'axios'
export default {
    name: 'DashboardView',
    components: {
        SubjectLoading
    },
    data() {
        return {
            isLoading: true,
            subjectLists: []
        }
    },
    computed: {
        ...mapGetters('auth', {
            token: GET_USER_TOKEN,
            isAuth: IS_USER_AUTHENTICATE_GETTER
        })
    },
    mounted() {
        console.log("DashboardView")
    },
    methods: {
        ...mapMutations({
            showLoading: SHOW_LOADING_MUTATION
        }),
        ...mapActions('auth', {
            logout: LOGOUT_ACTION
        }),
        teacherImage(staff) {
            /* const teacherImage = 'http://one.bma.edu.ph/assets/img/staff/percival_banting.jpg' */
            let teacherImage = 'http://one.bma.edu.ph/assets/img/staff/'
            let name = staff.user.name
            name = name.toLowerCase()
            name = name.replace(/\s+/g, '_')
            console.log(name)
            teacherImage = teacherImage + name + '.jpg'
            return teacherImage
        },
        encrypt(data) {
            return btoa(data)
        }
    }
}
</script>