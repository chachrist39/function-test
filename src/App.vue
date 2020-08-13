<template>
    <div>
        <div v-for="(item,i) in test" :key="i">
            <div>{{item}}</div>
        </div><br>
        <hr><br>
        <div>
            <input v-model="min" placeholder="Min:" type="number"><br><br>
            <input v-model="max" placeholder="Max:" type="number"><br><br>
            <button @click="calculation(min, max)">OK</button>
        </div><br>
        <div v-for="(el,i) in sumCount" :key="i.i">
            <div>{{el}}</div>
        </div>
        <div>{{sumTotal}}</div>
    </div>
</template>
<script>
export default {
    data(){
        return{
            min: '',
            max: '',
            sumCount: [],
            sumTotal: '',
            test: [],
        }
    },
    methods:{
        calculation(min, max){
            this.sumCount = []
            let count = max - min
            let sum = 0
            let totalCount = ""
            for (let i = 1; i <= count; i++) {
                if(sum == 0){
                    sum = (min*1) + ((min * 1) + i)
                    this.sumCount.push(min + " + " + ((min * 1) + i) + " = " + sum)
                }
                else{
                    sum += ((min * 1) + i)
                    this.sumCount.push((sum - ((min * 1) + i)) + " + " + ((min * 1) + i) + " = " + sum)
                }
                totalCount += (i < count ? ((min * 1) + i) + " + " : ((min * 1) + i) + " = ")
            }
            this.sumTotal = (count == 0 ? "Summary : 0" : "Summary : " + min + " + " + totalCount + sum)
        },

        checkPalindrome(word) {
                let l = word.length
                for (let i = 0; i < l / 2; i++) {
                    if (word.charAt(i) !== word.charAt(l - 1 - i)) {
                        return false
                    }
                }
                return true
        },
    },
    mounted(){
        
        let arrStr = ["saippuakivikauppias","Never odd or even","Expecto Patronum","level"]
        arrStr.forEach(el=>{
            let char = el.split(" ")
            let newChar = ""
            char.forEach(e=>{
                newChar += e.toLowerCase()
            })
            if (this.checkPalindrome(newChar)) {
                this.test.push(el + " is a palindrome")
            }
            else{
                this.test.push(el + " is not a palindrome")
            }
        })
    }
}
</script>