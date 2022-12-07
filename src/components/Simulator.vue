<template>

    <section class="simulator__section">
        <div class="container">
            <div class="row">

                <div class="iphone-14-pro">
                    <img :src="require(`@/assets/${iphoneMock}`)" alt="" class="phone__border">

                    <span class="dynamic-island" :class="{'active': islandFull}" @click="islandFully">
                        <span class="face-id"></span>
                        <span class="camera"><img :src="require(`@/assets/${camera}`)" alt="" class="camera-img"></span>
                    </span>

                    <button class="power-btn" @click="screenOn = !screenOn"></button>
                    <span class="black-screen" :class="{'active': !screenOn}"></span>

                    <div class="call__island" :class="{'calling': calling}">
                        <img :src="require(`@/assets/${contact.avatar}`)" alt="" class="contact-avatar">
                        <p class="contact-name"><span>iPhone</span> {{ contact.name }}</p>

                        <button class="cancel-btn" @click="calling = false"><i class="fas fa-phone-alt"></i></button>
                        <button class="agree-btn" @click="calling = false; startEndCall()"><i class="fas fa-phone-alt"></i></button>
                    </div>

                    <span class="talking__island" :class="{'active': talking}">
                        <span class="talking-time">
                            <i class="fas fa-phone-alt"></i>

                            <span class="time-num">
                                {{ minute < 10 ? `0${minute}` : minute }}:{{ secund < 10 ? `0${secund}` : secund }}
                            </span>
                        </span>

                        <span class="voice-wave">
                            <i class="fas fa-waveform-path wave-big"></i>
                            <i class="fas fa-waveform-path wave-md"></i>
                            <i class="fas fa-waveform-path wave-sm"></i>
                        </span>
                    </span>

                    <div class="charging__island" :class="{'charging': charging}">
                        <p class="charging-text">Charging</p>

                        <span class="battery-percent">75% <i class="fas fa-battery-bolt"></i></span> 
                    </div>

                    <span class="face-id__island" :class="{'checking': faceIdChecking}">
                        <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M7.97331 1.23828H4.76522C3.91438 1.23828 3.09839 1.57628 2.49676 2.17791C1.89512 2.77954 1.55713 3.59553 1.55713 4.44637V7.65446M24.0138 1.23828H27.2219C28.0727 1.23828 28.8887 1.57628 29.4903 2.17791C30.092 2.77954 30.4299 3.59553 30.4299 4.44637V7.65446M22.4097 9.25851V12.4666M9.57736 9.25851V12.4666M11.1814 22.0909C11.1814 22.0909 12.7854 23.6949 15.9935 23.6949C19.2016 23.6949 20.8057 22.0909 20.8057 22.0909M15.9935 9.25851V17.2787H14.3895M7.97331 30.1111H4.76522C3.91438 30.1111 3.09839 29.7731 2.49676 29.1715C1.89512 28.5698 1.55713 27.7538 1.55713 26.903V23.6949M24.0138 30.1111H27.2219C28.0727 30.1111 28.8887 29.7731 29.4903 29.1715C30.092 28.5698 30.4299 27.7538 30.4299 26.903V23.6949" :stroke="strokeColor" stroke-width="2.40607" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </span>

                    <span class="airpods__island" :class="{'active': airpods}">
                        <img :src="require(`@/assets/img/dynamicIsland/airpods.svg`)" alt="" class="airpods-img">

                        <span class="airpods-percent"></span>
                    </span>
                </div>

                <div class="dynamic-island-controls">
                    <button class="call-btn" @click="calling = !calling">
                        <i class="fas fa-phone-alt"></i>
                    </button>

                    <button class="charging-btn" @click="chargingActive"><i class="far fa-battery-bolt"></i></button>

                    <button class="face-id-btn" @click="faceId">face id</button>

                    <button class="airpods-btn" @click="airpodsActivate">airpods</button>
                </div>

            </div>
        </div>
    </section>
</template>

<script>

export default {
    name: 'Simulator',
    data() {
        return {
            iphoneMock: 'img/dynamicIsland/iphone-mock.svg',
            camera: 'img/dynamicIsland/camera.svg',
            islandFull: true,
            screenOn: true,
            calling: false,
            charging: false,
            contact: {
                avatar: 'img/dynamicIsland/avatar.svg',
                name: 'Yusef Kazemi'
            },
            talking: false,
            airpods: false,
            minute: 0,
            secund: 0,
            faceIdChecking: false,
            strokeColor: '#808080',
        }
    },
    methods: {
        chargingActive() {
            if (!this.screenOn) {
                setTimeout(() => {
                    this.screenOn = true
                }, 200);

                setTimeout(() => {
                    this.charging = true    
                }, 700);

                setTimeout(() => {
                    this.charging = false
                }, 4500);
                
            } else {
                this.islandFull = true
                this.talking ? this.talking = false : ''
                this.charging = true

                setTimeout(() => {
                    this.charging = false
                    this.secund ? this.talking = true : ''
                }, 2500);
            }
        },
        islandFully() {
            this.islandFull = false

            setTimeout(() => {
                this.islandFull = true
            }, 700);
        },
        startEndCall() {
            let interval = null

            if (this.talking && this.secund) {
                this.talking = false
                this.minute = 0
                this.secund = 0
                clearTimeout(interval)
            } else {
                this.talking = true
    
                this.minute = 0
                this.secund = 0

                let increaseSecund = () => {
                    this.secund++
    
                    if (this.secund == 60) {
                        this.secund = 0
                        this.minute++
                    }
                    
                    interval = setTimeout(() => {
                        increaseSecund()
                    }, 1000);
                }
                increaseSecund()
            }
        },
        faceId() {
            this.faceIdChecking = true

            setTimeout(() => {
                this.strokeColor = '#3EED50'   
            }, 700);

            setTimeout(() => {
                this.faceIdChecking = false

                setTimeout(() => {
                    this.strokeColor = '#808080'                
                },100);
            }, 2500);
        },
        airpodsActivate() {
            this.airpods = true

            setTimeout(() => {
                this.airpods = false
            }, 2000);
        }
    }
}

</script>

<style lang="scss" scoped>

.simulator__section {
    width: 100%;
    user-select: none;
    margin: 100px 0;

    .row {
        column-gap: 100px;
    }

    img {
        pointer-events: none;
    }

    .iphone-14-pro {
        max-width: 350px;
        width: 100%;
        position: relative;
        
        .phone__border {
            width: 100%;
        }

        .dynamic-island {
            width: 95px;
            height: 25px;
            background: transparent;
            border-radius: 14px;
            position: absolute;
            top: 28px;
            left: 128px;
            z-index: 6;
            transition: .4s;
            cursor: pointer;
            display: flex;
            column-gap: 8px;

            .face-id {
                width: 100%;
                height: 100%;
                display: block;
                background: #000;
                border-radius: 14px;
                transition: .4s;
            }

            .camera {
                width: 25px;
                min-width: 25px;
                height: 100%;
                border-radius: 14px;
                padding: 2px;
                overflow: hidden;
                background: #000;
                display: grid;
                place-items: center;
                transition: .4s;
                z-index: 5;

                img {
                    max-width: 15px;
                    width: 100%;
                    object-fit: cover;
                }
            }
            
            &::after {
                content: '';
                position: absolute;
                top: 0;
                left: 10px;
                width: 10px;
                height: 100%;
                display: block;
                background: #000;
                transition: .6s;
                z-index: -1;
                border-radius: 14px;
            }

            &.active {
                &::after {
                    width: 99%;
                    left: 0;
                }
            }
        }

        .power-btn {
            width: 8px;
            height: 65px;
            position: absolute;
            top: 185px;
            right: 0;
            cursor: pointer;
            border: 0;
            background: transparent;
            display: block;
            border-radius: 10px;
        }

        .black-screen {
            width: 87.8%;
            height: 94.3%;
            display: block;
            position: absolute;
            top: 15.5px;
            left: 22px;
            background: #000;
            border-radius: 48px;
            transition: .4s;
            opacity: 0;
            z-index: 5;
            pointer-events: none;

            &.active {
                opacity: 1;
                pointer-events: all;
            }
        }

        .call__island {
            position: absolute;
            top: 30px;
            left: 45%;
            width: 0;
            height: 0;
            background: #000;
            border-radius: 35px;
            display: flex;
            align-items: center;
            column-gap: 5px;
            color: #fff;
            z-index: 2;
            transition: .5s;
            overflow: hidden;

            img {
                height: 100%;
                display: block;
                border-radius: 50%;
                object-fit: cover;
            }

            .contact-name {
                font-size: 12px;
                display: flex;
                flex-direction: column;
                row-gap: 2px;
                font-weight: 500;
                transition: .3s;
                opacity: 0;

                span {
                    color: #808080;
                }
            }

            .cancel-btn {
                width: 0;
                margin-left: auto;
                height: 0;
                border: 0;
                border-radius: 50%;
                display: grid;
                place-items: center;
                background: #ED3E3E;
                cursor: pointer;
                color: #fff;
                font-size: 17px;
                padding-right: 2px;
                transition: .5s;
                opacity: 0;
                pointer-events: none;

                i {
                    transform: rotate(135deg);
                }
            }

            .agree-btn {
                width: 0;
                height: 0;
                border: 0;
                border-radius: 50%;
                display: grid;
                place-items: center;
                background: #3EED50;
                cursor: pointer;
                color: #fff;
                font-size: 17px;
                margin-left: 3px;
                padding-top: 3px;
                transition: .5s;
                opacity: 0;
                pointer-events: none;
            }

            &.calling {
                top: 28px;
                padding: 10px;
                left: 35px;
                width: 80%;
                height: 65px;

                .contact-name {
                    opacity: 1;
                }

                .cancel-btn {
                    opacity: 1;
                    width: 38px;
                    height: 38px;
                    pointer-events: all;
                }

                .agree-btn {
                    opacity: 1;
                    width: 38px;
                    height: 38px;
                    pointer-events: all;
                }
            }
        }

        .charging__island {
            position: absolute;
            top: 28px;
            left: 45%;
            width: 0%;
            height: 25px;
            background: #000;
            transition: .7s;
            border-radius: 18px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            pointer-events: none;

            .charging-text {
                font-size: 11px;
                font-weight: 500;
                color: #fff;
                opacity: 0;
                transition: .4s;
            }

            .battery-percent {
                color: #70FF00;
                font-size: 10px;
                font-weight: 500;
                display: flex;
                align-items: center;
                column-gap: 5px;
                opacity: 0;
                transition: .6s;
            }

            &.charging {
                width: 67%;
                left: 55px;
                pointer-events: all;
                padding: 0 12px;

                .charging-text {
                    opacity: 1;
                }

                .battery-percent {
                    opacity: 1;
                }
            }
        }

        .talking__island {
            width: 0;
            height: 25px;
            position: absolute;
            top: 28px;
            left: 45%;
            background: #000;
            border-radius: 14px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: .5s;

            .talking-time {
                color: #70FF00;
                font-size: 10px;
                display: flex;
                align-items: center;
                gap: 5px;
                transition: .6s;
                opacity: 0;

                .time-num {
                    font-weight: 500;
                }

                i {
                    font-size: 12px;
                    margin-top: 2px;
                }
            }

            .voice-wave {
                color: #70FF00;
                display: flex;
                align-items: center;
                gap: 2px;
                transition: .6s;
                opacity: 0;
                
                .wave-big {
                    font-size: 12.5px;
                }

                .wave-md {
                    font-size: 11px;
                    opacity: .7;
                }

                .wave-sm {
                    font-size: 9px;
                    opacity: .5;
                }
            }

            &.active {
                width: 60%;
                left: 70px;
                padding: 0 8px;

                .talking-time {
                    opacity: 1;
                }

                .voice-wave {
                    opacity: 1;
                }
            }
        }

        .face-id__island {
            width: 95px;
            height: 25px;
            background: #000;
            display: grid;
            place-items: center;
            position: absolute;
            top: 28px;
            left: 128px;
            border-radius: 14px;
            transition: .4s;
            visibility: hidden;

            svg {
                width: 0;
                opacity: 0;
                transition: .5s;
            }

            &.checking {
                width: 130px;
                left: 110px;
                height: 125px;
                border-radius: 30px;
                visibility: visible;

                svg {
                    width: 70px;
                    height: 70px;
                    opacity: 1;
                }
            }
        }

        .airpods__island {
            width: 0;
            height: 25px;
            background: #000;
            border-radius: 14px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: .6s;
            position: absolute;
            top: 28px;
            left: 50%;

            .airpods-img {
                width: 15px;
                transition: .4s;
                opacity: 0;
            }

            .airpods-percent {
                width: 15px;
                height: 15px;
                border-radius: 50%;
                background: #3EED50;
                position: relative;
                opacity: 0;
                transition: .4s;

                &::after {
                    content: '';
                    width: 13.5px;
                    height: 13px;
                    display: block;
                    background: #000;
                    border-radius: 50%;
                    position: absolute;
                    top: 1.4px;
                    left: 1.4px;
                    opacity: 0;
                    transition: .4s;
                }
            }

            &.active {
                width: 45%;
                left: 95px;
                padding: 0 8px;

                img {
                    opacity: 1;
                }

                .airpods-percent {
                    opacity: 1;

                    &::after {
                        opacity: 1;
                    }
                }
            }
        }
    }
    
    .dynamic-island-controls {
        max-width: max-content;
        width: 100%;
        display: flex;
        flex-direction: column;
        row-gap: 30px;
        padding: 30px 0;

        .call-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: #199b26;
            color: var(--main-color);
            border: 0;
            cursor: pointer;
            font-size: 20px;
            display: grid;
            place-items: center;
            transition: .4s;
        
            &:hover {
                transform: scale(1.1);
            }
        }

        .charging-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: #199b26;
            color: var(--main-color);
            border: 0;
            cursor: pointer;
            font-size: 20px;
            display: grid;
            place-items: center;
            transition: .4s;
        
            &:hover {
                box-shadow: 0 0 20px rgba($color: #000000, $alpha: .7);
            }
        }
    }
}

</style>