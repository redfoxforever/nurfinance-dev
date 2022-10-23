<template>
    <section class="calculator__section">
        <div class="container">
            <div class="row">

                <h2 class="calculator__title">{{ title }}</h2>

                <div class="calculator__dashboard">

                    <div class="deposit__controls-dashboard">

                        <div class="deposit__inp-box">
                            <p class="deposit__text">
                                Сумма вклада

                                <span class="deposit-num">{{ data.depositNum }} ₽</span>
                            </p>

                            <input type="range" class="deposit__inp" v-model="data.depositNum" max="2500000" min="10000">
                        </div>

                        <div class="deposit__inp-box">
                            <p class="deposit__text">
                                Срок инвестирования

                                <span class="deposit-num">{{ data.depositDate }} месяца</span>
                            </p>

                            <input type="range" class="deposit__inp" v-model="data.depositDate" max="36" min="1">
                        </div>

                        <div class="deposit__inp-box">
                            <p class="deposit__text">
                                Порядок выплаты дохода
                            </p>

                            <div class="deposit__gave-controls">
                                <button class="gave-period-btn" v-for="(btn, idx) in data.givePeriod" :key="idx" :class="{'selected': btn.selected}" @click="selectedPeriod(idx)">
                                    <span class="tick-icon">
                                        <transition name="fade-check">
                                            <i class="far fa-check" v-show="btn.selected"></i>
                                        </transition>
                                    </span>
                                    

                                    {{ btn.name }}
                                </button>
                            </div>
                        </div>

                        <div class="deposit__inp-box">
                            <p class="deposit__text">
                                Пополнение вклада

                                <span class="deposit-num">{{ data.depositGave }} ₽ /в месяц</span>
                            </p>

                            <input type="range" class="deposit__inp" v-model="data.depositGave" max="100000" min="1000">
                        </div>

                    </div>

                    <div class="deposit__chart-dashboard">

                    </div>

                    <div class="deposit__info-dashboard">
                        <div class="deposit__info-box">
                            <p class="deposit__info-text">
                                <span class="deposit__info-num">{{ Math.round((data.depositNum / data.depositGave) / data.depositDate * 2) }}</span>
                                Доходность
                            </p>
                        </div>

                        <div class="deposit__info-box">
                            <p class="deposit__info-text">
                                <span class="deposit__info-num">{{ Math.round(data.depositNum - (data.depositGave * data.depositDate)) ? Math.round(data.depositNum - (data.depositGave * data.depositDate)) : 0 }}</span>
                                Сумма доходности
                            </p>
                        </div>
                    </div>

                </div>
            </div>
        </div>
    </section>
</template>

<script>

export default {
    name: 'Calculator',
    data() {
        return {
            title: 'Рассчитай свои накопления и доход',
            data: {
                depositNum: 10000,
                depositDate: 1,
                depositGave: 1000,
                givePeriod: [
                    {
                        name: 'Ежемесячно',
                        selected: true
                    },
                    {
                        name: 'В конце срока',
                        selected: false
                    }
                ]
            }
        }
    },
    mounted() {
        const myDepositSlider = document.querySelectorAll('.deposit__inp');


        myDepositSlider.forEach(slider => {
            slider.addEventListener('input', () => {
                let valPercent = (slider.value / slider.max) * 100
                slider.style.background = `linear-gradient(to right, #355DFB ${valPercent}%, #CFDBE8 ${valPercent}%)`
            })
        });
    },
    methods: {
        selectedPeriod(id) {
            this.data.givePeriod.forEach(period => {
                period.selected = false
            })
            this.data.givePeriod[id].selected = true
        }
    }
}

</script>

<style lang="scss" scoped>

.calculator__section {
    width: 100%;

    .row {
        flex-direction: column;
        row-gap: 45px;
        padding: 70px 60px;
        background: #F0F4F8;
        border-radius: 64px 6px;
    }

    .calculator__title {
        font-size: 34px;
        font-weight: 400;
    }

    .calculator__dashboard {
        width: 100%;
        display: flex;
        justify-content: space-between;
        gap: 40px;

        .deposit__controls-dashboard {
            max-width: 460px;
            width: 100%;
            display: flex;
            flex-direction: column;
            row-gap: 45px;

            .deposit__inp-box {
                width: 100%;
                display: flex;
                flex-direction: column;
                row-gap: 15px;

                .deposit__text {
                    width: 100%;
                    display: flex;
                    justify-content: space-between;
                    align-items: center;
                    font-size: 16px;
                    font-weight: 500;

                    .deposit-num {
                        font-size: 18px;
                        font-weight: 800;
                    }
                }

                .deposit__inp {
                    -webkit-appearance: none;
                    appearance: none;
                    width: 100%;
                    height: 6px;
                    outline: none;
                    background: #CFDBE8;
                    border-radius: 8px;

                    &::-webkit-slider-thumb {
                        -webkit-appearance: none;
                        appearance: none;
                        width: 25px;
                        height: 25px;
                        cursor: pointer;
                        border-radius: 50%;
                        background: var(--nfc-white);
                        border: 5px solid var(--nfc-blue);
                        transition: .3s;
                    }

                    &::-ms-thumb {
                        -webkit-appearance: none;
                        appearance: none;
                        width: 25px;
                        height: 25px;
                        cursor: pointer;
                        border-radius: 50%;
                        background: var(--nfc-white);
                        border: 5px solid var(--nfc-blue);
                        transition: .3s;
                    }

                    &::-moz-range-thumb {
                        -webkit-appearance: none;
                        appearance: none;
                        width: 25px;
                        height: 25px;
                        cursor: pointer;
                        border-radius: 50%;
                        background: var(--nfc-white);
                        border: 5px solid var(--nfc-blue);
                        transition: .3s;
                    }

                    &:active::-webkit-slider-thumb {
                        border-width: 8px;
                    }
                }
            }

            .deposit__gave-controls {
                width: 100%;
                display: flex;
                gap: 12px;
                align-items: center;

                .gave-period-btn {
                    width: 50%;
                    border: 2px solid #C6D9E9;
                    border-radius: 20px 0px;
                    background: transparent;
                    padding: 15px 17px;
                    cursor: pointer;
                    font-size: 15px;
                    color: #6E9BB8;
                    font-weight: 500;
                    text-transform: capitalize;
                    transition: .4s;
                    display: flex;
                    column-gap: 14px;
                    align-items: center;
                    outline: none;

                    &.selected {
                        background: var(--nfc-white);
                        color: var(--nfc-black);
                        border-radius: 20px 20px 0 0;
                    }

                    & > .tick-icon {
                        width: 20px;
                        height: 20px;
                        border: 2px solid #C6D9E9;
                        border-radius: 4px;
                        display: block;
                        position: relative;

                        & > i {
                            font-size: 23px;
                            position: absolute;
                            top: -5px;
                            right: -10px;
                            color: var(--nfc-blue);
                        }
                    }
                }
            }

        }

        .deposit__chart-dashboard {
            max-width: 400px;
            width: 100%;
        }

        .deposit__info-dashboard {
            max-width: 300px;
            width: 100%;
            display: flex;
            flex-direction: column;
            row-gap: 20px;
            padding: 25px 30px;
            background: var(--nfc-white);
            border-radius: 10px 10px 120px 10px;
        }
    }
}

.fade-check-enter-active,
.fade-check-leave-active {
  transition: .4s ease;
}

.fade-check-enter-from,
.fade-check-leave-to {
  opacity: 0;
}

</style>