<template>
    <div class="container position-relative">
        <div class="row">
            <div class="col-lg-12">
                <div class="row mar-top justify-content-center align-items-center banner-container">
                    <div class="col-lg-7 banner-item order-lg-first order-last mt-lg-0 mt-5">
                        <span class="rectangle">
                            <svg width="85" viewBox="0 0 110 110" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <rect width="84.9997" height="85" rx="8"
                                    transform="matrix(0.883521 -0.468393 0.468328 0.883555 -2.49609 37.5596)"
                                    fill="#3b5e08" />
                            </svg>
                        </span>
                        <div class="banner-text">
                            <h2 class="mb-5 banner-text" id="hero-title">
                                YOUR FIRST STEP IN REACHING YOUR MARITIME DREAM
                            </h2>
                        </div>
                        <span class="ellipse">
                            <svg width="79" viewBox="0 0 79 79" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <ellipse rx="38.7296" ry="38.7296"
                                    transform="matrix(0.938441 0.345441 -0.345486 0.938424 39.7266 39.7235)"
                                    fill="#FDDA5F" />
                            </svg>
                        </span>
                        <span class="ellipse1">
                            <svg width="35" viewBox="0 0 79 79" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <ellipse rx="38.7296" ry="38.7296"
                                    transform="matrix(0.938441 0.345441 -0.345486 0.938424 39.7266 39.7235)"
                                    fill="#FDDA5F" />
                            </svg>
                        </span>
                        <div class="d-flex hero-serch flex-wrap" id="hero-row">

                            <router-link :to="{ name: 'app-layout.admission' }" class="btn btn-primary" id="Admission"
                                data-title="Admission" @click="changename('Admission')"> Inquire Now
                                <svg width="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <circle cx="11.7669" cy="11.7666" r="8.98856" stroke="currentColor" stroke-width="1.5"
                                        stroke-linecap="round" stroke-linejoin="round"></circle>
                                    <path d="M18.0186 18.4851L21.5426 22" stroke="currentColor" stroke-width="1.5"
                                        stroke-linecap="round" stroke-linejoin="round"></path>
                                </svg>
                            </router-link>


                        </div>
                    </div>
                    <div class="col-lg-5 banner-img">
                        <div class="img text-end" id="hero-img">
                            <img src="@/assets/resources/banner/BANNER2.png" class="img-fluid bg-img" alt="banner">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="editors position-relative">
        <div class="container" data-iq-gsap="onStart" data-iq-position-y="70" data-iq-rotate="0" data-iq-trigger="scroll"
            data-iq-ease="power.out" data-iq-opacity="0">
            <div class="row">
                <section class="editors mar-top mar-bot">
                    <div class="header-title d-flex justify-content-between">
                        <h4 class="title-bt fw-bolder">COURSES OFFERED</h4>
                    </div>

                    <span class="ellipse3">
                        <svg width="45" viewBox="0 0 79 79" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <ellipse rx="38.7296" ry="38.7296"
                                transform="matrix(0.938441 0.345441 -0.345486 0.938424 39.7266 39.7235)" fill="#FDDA5F" />
                        </svg>
                    </span>
                    <div class="row row-cols-1 row-cols-md-2 row-cols-lg-2 row-cols-xl-3 list-inline">
                        <div class="col">
                            <div class="card bg-white iq-service-card">
                                <router-link :to="{ name: 'app-layout.admission', query: { course: '2' } }" id="Admission"
                                    data-title="Admission" @click="changename('Admission')">
                                    <div class="iq-image position-relative">
                                        <div class="img">
                                            <img src="@/assets/resources/banner/BSMT.png" alt="image"
                                                class="img-fluid height1 radius-our w-100">
                                        </div>
                                        <!-- <div class="app badge-2 btn btn-sm btn-primary">$2000</div> -->
                                        <div class="app badge-1 btn btn-sm btn-primary">COLLEGE</div>
                                        <div class="app badge-3 ms-3 btn btn-sm text-white btn-info">BSMT</div>

                                    </div>
                                    <div class="card-body pb-3">
                                        <div class="border-bottom mt-3">
                                            <h5 class=" mb-3 fw-bolder">BS in Marine Transportation</h5>
                                        </div>
                                        <div class="d-flex justify-content-between flex-wrap mt-3">
                                            <div>

                                                <span class="text-dark ms-2">BS Marine Transportation - is a
                                                    maritime education program that covers the mandatory education
                                                    and training for a Navigational Watch required under Regulation
                                                    II/I of the STCW Convention, 1978, as amended.

                                                    The BSMT program shall cover the study of navigation, cargo
                                                    handling, and storage, and controlling the safe operation of the
                                                    ship, and care for persons on board the ship at the operational
                                                    level.</span>
                                            </div>

                                        </div>
                                    </div>
                                </router-link>

                            </div>
                        </div>


                        <div class="col">
                            <div class="card bg-white iq-service-card">
                                <router-link :to="{ name: 'app-layout.admission', query: { course: '1' } }" id="Admission"
                                    data-title="Admission" @click="changename('Admission')">
                                    <div class="iq-image position-relative">
                                        <div class="img">
                                            <img src="@/assets/resources/banner/BSMARE.png" alt="image"
                                                class="img-fluid height1 radius-our w-100">
                                        </div>
                                        <!-- <div class="app badge-2 btn btn-sm btn-primary">$2000</div> -->
                                        <div class="app badge-1 btn btn-sm btn-primary">COLLEGE</div>
                                        <div class="app badge-3 ms-3 btn btn-sm text-white btn-info">BSMARE</div>

                                    </div>
                                    <div class="card-body pb-3">
                                        <div class="border-bottom mt-3">
                                            <h5 class="mb-3 fw-bolder">BS in Marine ENGINEERING</h5>
                                        </div>
                                        <div class="d-flex justify-content-between flex-wrap mt-3">
                                            <div>

                                                <span class="text-dark ms-2">BS Marine Engineering - is a maritime
                                                    education program that covers the mandatory education and
                                                    training for Officers in Charge of an Engineering Watch required
                                                    under Regulation III/I of the STCW Convention, 1978, as amended

                                                    The BSMarE program shall cover the study of marine engineering
                                                    including but not limited to the propulsion system and its
                                                    auxiliaries, electrical, electronic, and control engineering,
                                                    maintenance, and repair, controlling the operation of the ship,
                                                    and care for persons on board the ship at the operational
                                                    level.he study of navigation, cargo handling, and storage, and
                                                    controlling the safe operation of the ship, and care for persons
                                                    on board the ship at the operational level.</span>
                                            </div>

                                        </div>
                                    </div>
                                </router-link>
                            </div>
                        </div>


                        <div class="col">
                            <div class="card bg-white iq-service-card">
                                <router-link :to="{ name: 'app-layout.admission', query: { course: '3' } }" id="Admission"
                                    data-title="Admission" @click="changename('Admission')">
                                    <div class="iq-image position-relative">
                                        <div class="img">
                                            <img src="@/assets/resources/banner/SHS.png" alt="image"
                                                class="img-fluid height1 radius-our w-100">
                                        </div>
                                        <!-- <div class="app badge-2 btn btn-sm btn-primary">$2000</div> -->
                                        <div class="app badge-1 btn btn-sm btn-primary">SENIOR HIGHSCHOOL</div>

                                    </div>
                                    <div class="card-body pb-3">
                                        <div class="border-bottom mt-3">
                                            <h5 class=" mb-3">Pre-Baccalaureate Maritime</h5>
                                        </div>
                                        <div class="d-flex justify-content-between flex-wrap mt-3">
                                            <div>

                                                <span class="text-dark ms-2">Senior High School - covers the
                                                    mandatory education for the last two years of the K to 12
                                                    Program and includes Grade 11 and 12 required by the Department
                                                    of Education and Marina.


                                                    The BMA SHS program offers a unique track of Pre-Baccalaureate
                                                    Maritime (PBM) aims to equip students with knowledge and skills
                                                    that will help them prepare better for their chosen field in
                                                    maritime education and training.</span>
                                            </div>

                                        </div>
                                    </div>

                                </router-link>
                            </div>

                        </div>
                    </div>


                </section>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'HomePage',
    mounted() {
        this.userToken()
    },
    methods: {
        async userToken() {
            axios.get('csrf-token').then((response) => {
                console.log(response)
            }).catch((error) => {
                console.log(error)
            })
        }
    }
}

</script>