<template>
<div>
    <nav class="flex items-center justify-between flex-wrap bg-blue-700 p-6">
        <div class="flex items-center flex-shrink-0 text-white mr-6">
            <span class="font-semibold text-xl tracking-tight">Welcome!!</span>
        </div>
        <div>
            <a href="#" class="flex justify-endinline-block text-sm px-4 py-2 leading-none border rounded text-white border-white hover:border-transparent hover:text-teal-500 hover:bg-white mt-4 lg:mt-0">
                <nuxt-link to="Login">Logout</nuxt-link>
            </a>
        </div>
    </nav>
    <div class="m-8">
        <h6 align="center"><b><u>Please choose items to your bucket</u></b></h6>
        <div class="grid grid-cols-3 gap-5 mt-14">
            <div class="p-6  max-w-sm bg-red-800 rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700  apple">
                <div class="mb-2 text-2xl text-center font-bold tracking-tight text-gray-900 dark:text-white">{{apple.name}}</div>
                <div class="flex flex-1 justify-center p-9 text-4xl">{{apple.count}}</div>
                <div class="flex flex-1 justify-center"><button @click="per? addApple() : alert()" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">+</button><button @click="per? removeApple() : alert()" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">-</button></div>

            </div>
            <div class="p-6 max-w-sm bg-red-800 rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700 orange">
                <div class="mb-2 text-2xl text-center font-bold tracking-tight text-gray-900 dark:text-white">{{orange.name}}</div>
                <div class="flex flex-1 justify-center p-9 text-4xl">{{orange.count}}</div>
                <div class="flex flex-1 justify-center"><button @click="per? addOrange() : alert()" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">+</button><button @click="per? removeOrange() : alert()" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">-</button></div>

            </div>
            <div class="p-6 max-w-sm bg-red-800 rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700 grape">
                <div class="mb-2 text-2xl text-center font-bold tracking-tight text-gray-900 dark:text-white">{{grapes.name}}</div>
                <div class="flex flex-1 justify-center p-9 text-4xl">{{grapes.count}}</div>
                <div class="flex flex-1 justify-center"><button @click="per? addGrape() : alert()" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">+</button><button @click="per? removeGrape() : alert()" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">-</button></div>

            </div>
        </div>
    </div>
    <div class="m-8">
        <div class="mx-32">
            <h4 align="center"><b>Basket stack</b></h4>
        </div>
        <center>
            <table class="w-64 mx-20 items-cener text-center justify-center">
                <tr class="border-solid border-2 border-indigo-600 w-10" v-for="(basket, index) in basket.slice().reverse()" :key="index">
                    <td :class="classes[basket]">{{basket}}</td>
                </tr>
            </table>
        </center>
    </div>
</div>
</template>

<script> 
export default {


    data() {
        return {
            "apple": {
                name: "Apple",
                count: 10,
            },
            "orange": {
                name: "Orange",
                count: 10,
            },
            "grapes": {
                name: "Grapes",
                count: 10,
            },
            basket: [],
            classes: {
                "Apple": 'apple',
                'Orange': "orange",
                "Grapes": "grape"
            },
            per: false,
        }

    },
    created() {
        this.per = this.$route.params.per;
        if (this.per === "all") {
            this.per = true;
        } else {
            this.per = false
        }
        //   console.warn(this.per)
    },
    methods: {

        addApple() {
            if (this.apple.count !== 0) {
                if (this.apple.count === 0) {
                    this.apple.count = 0;
                } else {
                    this.apple.count = this.apple.count - 1;
                    this.basket.push(this.apple.name)
                }
            } else {
                alert("Sorry!You ran out of Apples")
            }
        },
        removeApple() {
            if (this.basket.at(-1) == this.apple.name) {
                if (this.apple.count === 10) {
                    this.apple.count = 10;
                } else {
                    this.apple.count = this.apple.count + 1;
                    this.basket.pop()
                }
            } else {
                alert("Please select the correct item to remove")
            }
        },
        addOrange() {
            if (this.orange.count !== 0) {
                if (this.orange.count === 0) {
                    this.orange.count = 0;
                } else {
                    this.orange.count = this.orange.count - 1;
                    this.basket.push(this.orange.name)
                }
            } else {
                alert("Sorry!You ran out of Oranges")
            }
        },
        removeOrange() {
            if (this.basket.at(-1) == this.orange.name) {
                if (this.orange.count === 10) {
                    this.orange.count = 10;
                } else {
                    this.orange.count = this.orange.count + 1;
                    this.basket.pop()
                }
            } else {
                alert("Please select the correct item to remove")
            }
        },
        addGrape() {
            if (this.grapes.count !== 0) {
                if (this.grapes.count === 0) {
                    this.grapes.count = 0;
                } else {
                    this.grapes.count = this.grapes.count - 1;
                    this.basket.push(this.grapes.name)
                }
            } else {
                alert("Sorry!You ran out of Grapes")
            }
        },
        removeGrape() {
            if (this.basket.at(-1) == this.grapes.name) {
               if (this.grapes.count === 10) {
                    this.grapes.count = 10;
                } else {
                    this.grapes.count = this.grapes.count + 1;
                    this.basket.pop()
                }
            } else {
                alert("Please select the correct item to remove")
            }
        },
        alert() {
            alert("Sorry!You dont have access")
        },
        accessData(){
            
        }
    }
}
</script>

<style scoped>
.apple {
    background-color: rgb(55, 0, 255);
}

.orange {
    background-color: rgb(255, 0, 0);
}

.grape {
    background-color: rgb(200, 255, 0);
}
</style>
