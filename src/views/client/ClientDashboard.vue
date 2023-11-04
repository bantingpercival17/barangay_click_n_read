<template>
    <div v-if="isLoading">
        <LessonLoading />
    </div>
    <div v-else>
        <p class='display-6 fw-bolder text-primary'>BOOK LIST</p>
        <div class="form-sort row">
            <div class="col-md">
                <small class="fw-bolder">SEARCH BOOK NAME</small>
                <input type="text" class="form-control form-control-sm border border-primary">
            </div>
        </div>
        <div class="row mt-5">
            <div class="col-lg-4 col-md-6 col-xs-12" v-for="(data, index) in subjectLists" :key="index">
                <router-link :to="{ name: 'student-layout.book-view', params: { book: encrypt(data.id) } }">
                    <div class="card">
                        <img :src="data.bookCover" alt="" class="card-img-top">
                        <div class="card-body p-3">
                            <label for="" class="fw-bolder text-primary h4">
                                {{ data.bookName }}
                            </label> <br>

                            <span class="text-muted">
                                Progress <span class="fw-bolder">{{ data.numberOfReaders }}</span>
                            </span>
                            <br>
                            <small class="text-muted">
                                {{ data.bookDescription }}
                            </small>
                        </div>
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
import LessonLoading from '@/views/student/classroom/loading-view/LessonLoading.vue'
import axios from 'axios'
export default {
    name: 'DashboardView',
    components: {
        LessonLoading
    },
    data() {
        return {
            isLoading: true,
            subjectLists: [
                {
                    id: 1,
                    bookCover: '/assets/books/ENGLISH_GR2.png',
                    bookName: 'ENGLISH 2',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.',
                    bookLink: '@/assets/books/ENGLISH_BOOK_GRADE_2.pdf',
                    numberOfReaders: '50%'
                },
                {
                    id: 2,
                    bookCover: '/assets/books/ENGLISH_GR1.png',
                    bookName: 'ENGLISH 1',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. ',
                    bookLink: '@/assets/books/Grade_G1_G1.pdf',
                    numberOfReaders: '70%'
                }
            ]
        }
    },
    computed: {
        ...mapGetters('auth', {
            token: GET_USER_TOKEN,
            isAuth: IS_USER_AUTHENTICATE_GETTER
        })
    },
    mounted() {
        setInterval(() => {
            this.isLoading = false
        }, 2000)
        console.log('DashboardView')
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