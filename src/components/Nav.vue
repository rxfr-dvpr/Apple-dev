<template>
  <nav class="nav">
    <div class="container">
        <div class="row">
            
            <Transition name="nav">
                <ul class="nav__list" v-if="windowSize >= 850">
                    <li class="nav__list-item" v-for="(link, idx) in navLinks" :key="idx" :class="`nav__item-${link.className}`">
                        <a href="" class="nav__list-link" v-html="link.name" ></a>
                    </li>
                </ul>

                <div class="nav-mb" v-else>
                    <button class="nav-btn-mb" @click="navMbOpened = !navMbOpened" :class="{'opened': navMbOpened}">
                        <span class="nav-btn-line" v-for="(line, id) in 2" :key="id"></span>
                    </button>

                    <div class="nav__mb-collapse" :class="{'opened': navMbOpened}">
                        <form action="" class="nav__form-mb" @submit.prevent>
                            <input type="text" class="search-inp" placeholder="Search apple.com" v-model.trim="searchInp">
                        </form>

                        <ul class="nav__list-mb">
                            <li class="nav__list-item-mb" v-for="(link, idx) in navLinksMb" :key="idx">
                                <a :href="link.url" class="nav__list-link-mb">{{ link.name }}</a>
                            </li>
                        </ul>
                    </div>

                    
                    <a href="/" class="apple-logo">
                        <i class="fab fa-apple"></i>
                    </a>

                    <button class="shop-btn">
                        <i class="fal fa-shopping-bag"></i>
                    </button>
                </div>
            </Transition>
            
        </div>
    </div>
  </nav>
</template>

<script>

export default {
    name: 'Nav',
    data() {
        return {
            navLinks: [
                {
                    name: '<i class="fab fa-apple"></i>',
                    url: '',
                    className: 'logo'
                },
                {
                    name: 'Store',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Mac',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'iPad',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'iPhone',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Watch',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'AirPods',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'TV & Home',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Only on Apple',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Accessories',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Support',
                    url: '',
                    className: 'link'
                },
                {
                    name: '<i class="fal fa-search"></i>',
                    url: '',
                    className: 'search'
                },
                {
                    name: '<i class="fal fa-shopping-bag"></i>',
                    url: '',
                    className: 'shop'
                }
            ],
            navLinksMb: [
                {
                    name: 'Store',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Mac',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'iPad',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'iPhone',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Watch',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'AirPods',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'TV & Home',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Only on Apple',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Accessories',
                    url: '',
                    className: 'link'
                },
                {
                    name: 'Support',
                    url: '',
                    className: 'link'
                }
            ],
            windowSize: window.innerWidth,
            searchInp: '',
            navMbOpened: false,
        }
    },
    mounted() {
        window.addEventListener('resize', () => {
            this.windowSize = window.innerWidth
        })
    }
}

</script>

<style lang="scss" scoped>

.nav {
    width: 100%;
    background: rgba(0,0,0,0.8);
    position: fixed;
    top: 0;
    left: 0;
    backdrop-filter: saturate(180%) blur(20px);
    z-index: 999;

    .nav__list {
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        
        &-link {
            height: 45px;
            display: grid;
            place-items: center;
            font-size: 13px;
            color: #f5f5f7;
            padding: 0 8px;
            opacity: .8;
            letter-spacing: -.01em;
            transition: .4s;
            font-weight: 300;

            &:hover {
                opacity: 1;
            }
        }

        .nav__item-logo {
            .nav__list-link {
                font-size: 17px;
            }
        }

        .nav__item-search {
            .nav__list-link {
                font-size: 14px;
                padding-top: 1px;
            }
        }

        .nav__item-shop {
            .nav__list-link {
                font-size: 15px;
            }
        }

    }

    .nav-mb {
        width: 100%;
        height: 48px;
        display: flex;
        justify-content: space-between;
        align-items: center;

        .apple-logo {
            font-size: 22px;
            color: #fff;
            z-index: 4;
            transition: .4s; 
            opacity: .8;
            
            &:hover {
                opacity: 1;
            }
        }

        .nav-btn-mb {
            width: 48px;
            height: 100%;
            border: 0;
            background: transparent;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            row-gap: 7px;
            z-index: 4;
            cursor: pointer;
            transition: .4s; 
            opacity: .8;
            
            &:hover {
                opacity: 1;
            } 

            .nav-btn-line {
                width: 20px;
                height: 1px;
                background: #fff;
                transition: .4s;
            }

            &.opened {
                row-gap: 0;
                opacity: .8;

                & > span:first-of-type {
                    transform: rotate(-45deg);   
                }

                & > span:last-of-type {
                    transform: translateY(-1px) rotate(45deg);   
                }
            }
        }

        .shop-btn {
            width: 48px;
            height: 100%;
            display: grid;
            place-items: center;
            background: transparent;
            font-size: 18px;
            color: #fff;
            cursor: pointer;
            border: 0;     
            transition: .4s; 
            opacity: .8;
            
            &:hover {
                opacity: 1;
            }
        }

        .nav__mb-collapse {
            width: 100%;
            height: 0;
            position: absolute;
            top: 0;
            left: 0;
            background: #000;
            z-index: 3;
            padding-top: 48px;
            transition: .5s ease-in-out;
            visibility: hidden;
            opacity: 0;
            pointer-events: none;

            .nav__form-mb {
                width: 100%;
                margin: 0 auto;
                border-bottom: 1px solid #424245;
                display: flex;
                justify-content: center;
                transition: .5s;
                padding-left: 10px;
                padding-right: 10px;

                .search-inp {
                    max-width: 585px;
                    width: 100%;
                    margin: 0 auto;
                    background: #1d1d1f;
                    outline: none;
                    height: 0;
                    border: 0;
                    border-radius: 10px;
                    padding: 0 10px;
                    font-size: 17px;
                    color: #c5c5c7;
                    transition: height .5s;

                    &::placeholder {
                        font-size: 17px;
                        font-weight: 500;
                    }
                }
            }

            .nav__list-mb {
                max-width: 585px;
                width: 100%;
                height: 100%;
                display: flex;
                flex-direction: column;
                margin: 0 auto;
                overflow-y: auto;
                padding-left: 15px;
                padding-right: 15px;
                transition: .5s;

                .nav__list-link-mb {
                    font-size: 18px;
                    color: #f5f5f7;
                    height: 45px;
                    display: flex;
                    align-items: center;
                    opacity: .8;
                }

                li {
                    border-bottom: 1px solid #424245;

                    &:last-of-type {
                        border-bottom: 0;
                    }
                }
            }

            &.opened {
                height: 100vh;
                visibility: visible;
                padding-bottom: 48px;
                opacity: 1;
                pointer-events: all;

                .nav__form-mb {
                    padding-top: 10px;
                    padding-bottom: 10px;
                }

                .search-inp {
                    height: 35px;
                }

                .nav__list-mb {
                    padding-top: 10px;
                    padding-bottom: 15px;
                }
            }
        }
        
    }
}



</style>