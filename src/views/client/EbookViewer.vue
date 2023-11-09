<template>
    <div v-if="isLoading">
        <LessonLoading />
    </div>
    <div v-else>
        <p class='display-6 fw-bolder text-primary'>{{ bookName }}</p>
        <p class="text-muted">{{ bookDescription }}</p>
        <div class="row">
            <div class="col-lg-8 col-md-12">
                <div v-if="contentLink !== null">
                    <ScormViewer :contentUrl="contentLink" />
                </div>
                <div v-else>
                    <p class="text-warning fw-bolder">NO DATA</p>
                </div>
            </div>
            <div class="col-lg-4 col-md-12">
                <label for="" class="fw-bolder text-muted">OTHER BOOKS</label>
                <div class="mt-2" v-for="(data, index) in subjectLists" :key="index">
                    <router-link :to="{ name: 'student-layout.book-view', params: { book: encrypt(data.id) } }">
                        <div class="card">
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

    </div>
</template>
<script>
import Swal from 'sweetalert2'
import { LOGOUT_ACTION, GET_USER_TOKEN, IS_USER_AUTHENTICATE_GETTER, SHOW_LOADING_MUTATION } from '@/store/storeConstants'
import { mapActions, mapGetters, mapMutations } from 'vuex'
import LessonLoading from '@/views/student/classroom/loading-view/LessonLoading.vue'
import ScormViewer from './widget/ScormViewer.vue'
import axios from 'axios'
export default {
    name: 'DashboardView',
    components: {
        LessonLoading,
        ScormViewer
    },
    data() {
        return {
            isLoading: true,
            bookName: 'Book Name',
            bookDescription: 'Book Description',
            contentLink: null,
            subjectLists: [
                {
                    id: 1,
                    bookCover: '/assets/books/ENGLISH_GR2.png',
                    bookName: 'ENGLISH 2',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.',
                    bookLink: '/assets/scorm/ENGLISH_BOOK_GR2/res/index.html',
                    numberOfReaders: '50%'
                },
                {
                    id: 2,
                    bookCover: '/assets/books/ENGLISH_GR1.png',
                    bookName: 'ENGLISH 1',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. ',
                    bookLink: '/assets/scorm/ENGLISH_GR1/index.html',
                    numberOfReaders: '70%'
                },
                {
                    id: 3,
                    bookCover: '/assets/books/Alternative Medicine October 2023.jpg',
                    bookName: 'Alternative Medicine',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. ',
                    bookLink: '/assets/scorm/Alternative Medicine October 2023/res/index.html',
                    numberOfReaders: '70%'
                },
                {
                    id: 4,
                    bookCover: '/assets/books/Elon Musk Walter Isaacson.jpg',
                    bookName: 'Elon Musk Walter Isaacson',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. ',
                    bookLink: '/assets/scorm/Elon Musk Walter Isaacson/res/index.html',
                    numberOfReaders: '70%'
                }, {
                    id: 5,
                    bookCover: '/assets/books/Hbrs 10 Must Reads Ultimate Boxed Set By Misc Authors.jpg',
                    bookName: 'Hbrs 10 Must Reads Ultimate Boxed Set',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. ',
                    bookLink: '/assets/scorm/Hbrs 10 Must Reads Ultimate Boxed Set By Misc Authors/res/index.html',
                    numberOfReaders: '70%'
                },
                {
                    id: 6,
                    bookCover: '/assets/books/Mit Sloan Management Review.jpg',
                    bookName: 'Mit Sloan Management Review',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. ',
                    bookLink: '/assets/scorm/Mit Sloan Management Review/res/index.html',
                    numberOfReaders: '70%'
                },
                {
                    id: 7,
                    bookCover: '/assets/books/My Herbs Issue 24 2023.jpg',
                    bookName: 'My Herbs Issue',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. ',
                    bookLink: '/assets/scorm/My Herbs Issue 24 2023/res/index.html',
                    numberOfReaders: '70%'
                },
                {
                    id: 8,
                    bookCover: '/assets/books/Snip Burn Solder Shred 2011.jpg',
                    bookName: 'Snip Burn Solder Shred 2011',
                    bookDescription: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. ',
                    bookLink: '/assets/scorm/Snip Burn Solder Shred 2011/res/index.html',
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
        this.setContent()
        this.isLoading = false
    },
    methods: {
        ...mapMutations({
            showLoading: SHOW_LOADING_MUTATION
        }),
        ...mapActions('auth', {
            logout: LOGOUT_ACTION
        }),
        encrypt(data) {
            return btoa(data)
        },
        decrypt(data) {
            return atob(data)
        },
        setContent() {
            const viewID = this.decrypt(this.$route.params.book)
            let foundIndex = null
            this.subjectLists.forEach((element, index) => {
                if (parseInt(viewID) === element.id) {
                    foundIndex = index
                }
            })
            // const foundIndex = this.subjectLists.find(item => item.id === viewID)
            if (foundIndex !== null) {
                this.bookName = this.subjectLists[foundIndex].bookName
                this.bookDescription = this.subjectLists[foundIndex].bookDescription
                this.contentLink = this.subjectLists[foundIndex].bookLink
            }
        }
    }
}
</script>