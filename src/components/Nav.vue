<template>
  <nav class="nav">
    <div class="container">
        <div class="row">

            <div class="nav__top-links">
                <ul class="nav__top-list">
                    <li class="nav__top-item" v-for="(link, idx) in navTopLinks" :key="idx">
                        <router-link :to="link.url" class="nav__top-link"
                         active-class="active">
                            {{ link.name }}
                        </router-link>
                    </li>
                </ul>
            </div>

            <div class="nav__bottom-links">
                <router-link to="/" class="nav-logo">
                    <img :src="logoImg" alt="" class="logo-img">
                </router-link>

                <ul class="nav__bottom-list">
                    <li class="nav__bottom-item" v-for="(link, id) in navBottomLinks" :key="id">
                        <router-link class="nav__bottom-link" :to="link.url">{{ link.name }}</router-link>
                    </li>
                </ul>

                <div class="nav__bottom-controls">
                    <button class="bottom-control-btn profile-btn">Личный Кабинет</button>

                    <button class="bottom-control-btn online-require">Онлайн-заявка</button>
                </div>
            </div>

        </div>
    </div>
  </nav>
</template>

<script>
export default {
    name: "Nav",
    data() {
        return {
            navTopLinks: [
                {
                    name: 'Инвестиционно-финансовая компания',
                    url: ''
                },
                {
                    name: 'Город  Казань',
                    url: ''
                },
                {
                    name: 'О компании',
                    url: ''
                },
                {
                    name: 'Отзывы',
                    url: ''
                },
                {
                    name: 'Халяль подробно',
                    url: ''
                },
                {
                    name: 'Отчетность',
                    url: ''
                },
                {
                    name: 'Наши партнеры',
                    url: ''
                },
                {
                    name: 'Сотрудничество',
                    url: ''
                },
                {
                    name: 'Контакты',
                    url: ''
                },
            ],
            navBottomLinks: [
                {
                    name: 'Инвестиции',
                    url: ''
                },
                {
                    name: 'Рассрочка',
                    url: ''
                },
                {
                    name: 'Калькулятор',
                    url: ''
                }
            ],
            logoImg: require('@/assets/images/logo.svg')   
        }
    }
}
</script>

<style lang="scss" scoped>

.nav {
    width: 100%;
    padding: 20px 0;
    position: relative;
    background: #F0F4F8;

    .row {
        flex-direction: column;
        align-items: flex-start;
    }

    &__top-links {
        width: 100%;
        padding-bottom: 20px;
    }

    &__top-list {
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 15px;
    }

    &__top-link {
        font-size: 14px;
        color: var(--nfc-text-color);
        font-weight: 500;
        transition: .4s;

        &:hover {
            color: var(--nfc-blue);
        }
    }

    &__bottom-links {
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-top: 20px;
        border-top: 2px solid #CBD8E9;
        gap: 15px;

        & > .nav-logo {
            max-width: 200px;
            width: 100%;
            
            & > img {
                width: 100%;
                object-fit: cover;
            }
        }
    }

    &__bottom-list {
        max-width: 335px;
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 20px;
    }

    &__bottom-link {
        font-size: 18px;
        color: var(--nfc-blue);
        font-weight: 500;
        transition: .4s;

        &:hover {
            color: var(--nfc-text-color);
        }
    }

    &__bottom-controls {
        max-width: max-content;
        width: 100%;
        display: flex;
        align-items: center;
        gap: 15px;

        .bottom-control-btn {
            padding: 14px 20px;
            border: 0;
            border-radius: 20px 0;
            cursor: pointer;
            font-weight: 500;
            font-size: 14px;
            transition: .4s;

            &.profile-btn {
                background: var(--nfc-blue);
                color: var(--nfc-white);
            }

            &.online-require {
                background: var(--nfc-white);
                color: var(--nfc-blue);
                box-shadow: 0 0 10px rgba($color: #000000, $alpha: 0.2);
            }

            &:hover {
                border-radius: 10px 10px 0px 0px;
            }
        }
    }
}

</style>