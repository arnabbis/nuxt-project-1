<template>
    <div>
        <Navbar />
        <div class="">
            <h6 class="text-center text-lg bg-gray-700 text-gray-100 mx-32 rounded-lg mb-5">Please choose items to your bucket</h6>
            <div class="flex flex-row ">
                <div class="basis-1/4 bg-red-400">
                    <div>{{ apple.name }}</div>
                    <div>{{ apple.count }}</div>
                    <div><button v-on:click="add">+</button><button v-on:click="remove">-</button></div>
                </div>
                <div class="basis-1/4 bg-orange-500 h-80">
                    <div>{{ orange.name }}</div>
                    <div>{{ orange.count }}</div>
                    <div><button v-on:click="add1">+</button><button v-on:click="remove1">-</button></div>
                </div>
                <div class="basis-1/4 bg-blue-200">
                    <div>{{ grapes.name }}</div>
                    <div>{{ grapes.count }}</div>
                    <div><button v-on:click="add2" class="rounded-full">+</button><button
                            v-on:click="remove2">-</button></div>
                </div>
            </div>
        </div>
        <div class="m-8">
            <div>
                <h4>Basket stack</h4>
            </div>
            <div>{{ basket.join(",") }}</div><br />
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
                color: ""
            },
            "orange": {
                name: "Orange",
                count: 10,
                color: ""
            },
            "grapes": {
                name: "Grapes",
                count: 10,
                color: ""
            },
            basket: []
        }
    },
    methods: {
        add() {
            if (this.apple.count > 0) {
                this.apple.count = this.apple.count === 0 ? 0 : this.apple.count - 1;
                this.basket.push(this.apple.name)
            }
            else {
                alert("you already aaded 10 item")
            }
        },
        remove() {
            if (this.basket.at(-1) == this.apple.name) {
                this.apple.count = this.apple.count === 10 ? 10 : this.apple.count + 1;
                this.basket.pop()
            }
            else {
                alert("You have selected invalid item")
            }
        },
        add1() {
            if (this.orange.count > 0) {
                this.orange.count = this.orange.count === 0 ? 0 : this.orange.count - 1;
                this.basket.push(this.orange.name)
            }
            else {
                alert("You have selected 10 items")
            }
        },
        remove1() {
            if (this.basket.at(-1) == this.orange.name) {
                this.orange.count = this.orange.count === 10 ? 10 : this.orange.count + 1;
                this.basket.pop()
            }
            else {
                alert("You have selected invalid item ")
            }
        },
        add2() {
            if (this.grapes.count > 0) {
                this.grapes.count = this.grapes.count === 0 ? 0 : this.grapes.count - 1;
                this.basket.push(this.grapes.name)
            }
            else {
                alert("You have selected 10 items ")
            }
        },
        remove2() {
            console.warn(this.basket.at(-1))
            if (this.basket.at(-1) == this.grapes.name) {
                this.grapes.count = this.grapes.count === 10 ? 10 : this.grapes.count + 1;
                this.basket.pop()
            }
            else {
                alert("You have selected invalid item ")
            }
        },
    }
}
    </script>