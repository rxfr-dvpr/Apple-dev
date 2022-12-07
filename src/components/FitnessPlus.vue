<template>
  <section class="fitness-plus__section">
    <div class="container">
        <div class="row">

            <div class="fitness__desc">
                <h2 class="fitness-title" v-html="title">
                </h2>
                <p class="fitness-subtitle" v-html="subtitle"></p>

                <div class="fitness__links">
                    <a :href="link.url" class="fitness-link" v-for="(link, idx) in links" :key="idx">
                        {{ link.name }}

                        <i class="fas fa-chevron-right"></i>
                    </a>
                </div>
            </div>

            <img :src="image" alt="" class="fitness__img">

            <p class="fitness-sm-info">Available later fall for all iPhone Users.</p>

        </div>
    </div>
  </section>
</template>

<script>

export default {
    name: 'Fitness Plus',
    data() {
        return {
            title: '<i class="fab fa-apple"></i> Fitness+',
            subtitle: 'Fitness for everyone <span>Now all you need is iPhone</span>',
            links: [
                {
                    name: 'Learn more',
                    url: ''
                },
                {
                    name: 'Notify me',
                    url: ''
                }
            ],
            image: require('@/assets/img/fitnessPlus.png')
        }
    }
}

</script>

<style lang="scss" scoped>

@keyframes translateRight {
    from {
        transform: translateX(0);
    }
    to {
        transform: translateX(3px);
    }
}

.fitness-plus__section {
    width: 100%;
    background: #F5F5F7;
    padding-top: 60px;

    .container {
        padding: 0 !important;
    }

    .row {
        flex-direction: column;
        align-items: center;
        text-align: center;

        .fitness__desc {
            display: flex;
            flex-direction: column;
            align-items: center;

            .fitness-title {
                color: #000;
                font-size: calc(32px + 4 * (100vw / 1920));
                font-weight: 700;
            }

            .fitness-subtitle {
                font-size: calc(19px + 1 * (100vw / 1920));
                color: #000;
                font-weight: 500;
                display: flex;
                flex-direction: column;
                text-align: center;
                align-items: center;
            }

            .fitness__links {
                display: flex;
                align-items: center;
                column-gap: 45px;
                margin-top: 5px;

                .fitness-link {
                    font-size: calc(17px + 1 * (100vw / 1920));
                    color: #2997ff;
                    display: flex;
                    align-items: center;
                    column-gap: 10px;
                    font-weight: 500;

                    & > i {
                        font-size: 14px;
                        margin-top: 4px;
                        transition: .4s;
                    }

                    &:hover {
                        
                        & > i {
                            animation: translateRight .6s linear infinite;
                        }
                    }
                }
            }
        }

        .fitness__img {
            max-width: 370px;
            width: 100%;
            cursor: none;
            pointer-events: none;
            object-fit: cover;
            margin-top: auto;
        }

        .fitness-sm-info {
            font-size: 18px;
            color: #86868B;
            margin-bottom: 10px;
        }
    }
}

@media (min-width: 1920px) {
    .fitness-title {
        font-size: 36px !important;
    }

    .fitness-subtitle {
        font-size: 20px !important;
    }

    .fitness-link {
        font-size: 20px !important;
    }
}



@media (max-width: 662px) {
    .fitness-title {
        font-size: calc(32px + (4 + 4 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .fitness-subtitle {
        font-size: calc(19px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }

    .fitness__links {
        column-gap: 25px !important;
    }

    .fitness-link {
        font-size: calc(17px + (1 + 1 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }
}

</style>