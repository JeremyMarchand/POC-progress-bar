<template>
    <div class="hello">
        <div class="progress-bar">

            <h4>Configuration: {{ value }}%</h4>
            <div @mouseover="hover = true"
                 @mouseleave="hover = false">
                <VueSlideBar
                        v-model="value"
                        :data="data"
                        :range="slider.range"
                        :isDisabled="true"
                        :draggable="false"
                        :showTooltip="true"
                        :processStyle="slider.processStyle"
                        :lineHeight="slider.lineHeight"
                >
                    <template slot="tooltip">
                        <div class="legend-progress">
                            <img class="img-progress-bar" src="../assets/check.png">
                            <div v-if="hover" class="hover-div">
                                <div class="arrow"></div>
                                <span>
                                <ul class="tasks-list">
                                     <li class="title-task">Etapes à compléter :</li>
                                    <li><img class="img-task task-done" src="../assets/check.png"> - Item 1</li>
                                     <li><img class="img-task task-done" src="../assets/check.png"> - Item 2</li>
                                    <li><img class="img-task task-done" src="../assets/check.png"> - Item 3</li>
                                    <li class="title-task optional-task">Optionnel :</li>
                                    <li class="task-todo">Item 4</li>
                                    <li class="task-todo">Item 5</li>
                                    <li class="task-todo">Item 6</li>
                                </ul>
                            </span>
                            </div>
                        </div>


                    </template>
                </VueSlideBar>
            </div>

        </div>
    </div>
</template>

<script>
    import VueSlideBar from 'vue-slide-bar'

    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        components: {
            VueSlideBar
        },
        data() {
            return {
                hover: true,
                value: 30,
                data: [0, 10, 20, 30, 45, 60, 75, 85, 100],

                slider: {
                    lineHeight: 10,
                    processStyle: {
                        backgroundColor: 'green'
                    },
                    range: [{
                        label: '0%'
                    }, {
                        label: '10%'
                    }, {
                        label: '20%'
                    }, {
                        label: '30%'
                    }, {
                        label: '45%'
                    }, {
                        label: '60%'
                    }, {
                        label: '75%'
                    }, {
                        label: '85%'
                    }, {
                        label: '100%'
                    }]
                }
            }
        }

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    * {
        box-sizing: border-box;
    }

    .legend-progress {
        position: relative;
        left: 500px;
    }

    .vue-slide-bar-tooltip-container, .vue-slide-bar-always {
        -webkit-transform: none !important;
        -moz-transform: none !important;
        -ms-transform: none !important;
        -o-transform: none !important;
        transform: none !important;
    }

    .progress-bar {
        width: 50%;
        flex: left;
    }

    .vue-slide-bar-tooltip-container span img {
        margin-top: 20px;
    }

    .img-progress-bar {
        background-color: black;
        border-radius: 50%;
        width: 120%;
        position: relative;
        left: 8px;
    }

    .img-task {
        width: 25px;
    }

    .hover-div {
        background-color: grey;
        width: 500px;
        position: absolute;
        left: 40px;
        top: 13px;
        border-radius: 10px;
    }

    .tasks-list li {
        text-align: left;
    }

    .task-done {
        margin: 10px 0px;
    }

    .task-todo {
        margin: 20px 0px;
    }

    .optional-task {
        margin-top: 30px;
    }

    .title-task {
        font-weight: bold;
    }

    li {
        list-style-type: none;
    }

    .tasks-list li img {
        position: relative;
        top: 15px;
    }

    .arrow {
        width: 0;
        height: 0;
        border-top: 10px solid transparent;
        border-bottom: 10px solid transparent;
        border-right: 10px solid red;
        position: relative;
        right: 10px;
        top: 10px;
    }
</style>
