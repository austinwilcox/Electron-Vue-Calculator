<template>
  <div class="calculator">
      <v-row>
          <v-col cols="12">
              <v-banner
                :model="operation"
                elevation=8
                min-height=150
              >
                  {{`${operation.leftSide} ${operation.operand} ${operation.rightSide} ${operation.answer}`}}
              </v-banner>
          </v-col>
      </v-row>
      <v-row>
          <v-col cols="3">
               <v-btn
                outlined
                color="warning"
                rounded
                style="width: 100%"
                @click='clear'
              >
                  C
              </v-btn>
          </v-col>
          <v-col cols="3">
               <v-btn
                outlined
                color="warning"
                rounded
                style="width: 100%"
                @click="operandClick('+/-')"
              >
                  +/-
              </v-btn>
          </v-col>
          <v-col cols="3">
               <v-btn
                outlined
                color="warning"
                rounded
                style="width: 100%"
                @click="operandClick('%')"
              >
                  %
              </v-btn>
          </v-col>
          <v-col cols="3">
              <v-btn
                outlined
                color="warning"
                rounded
                style="width: 100%"
                @click="operandClick('/')"
              >
                  /
              </v-btn>
          </v-col>
      </v-row>
      <v-row>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(7)"
              >
                  7
              </v-btn>
          </v-col>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(8)"
              >
                  8
              </v-btn>
          </v-col>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(9)"
              >
                  9
              </v-btn>
          </v-col>
          <v-col cols="3">
               <v-btn
                outlined
                color="warning"
                rounded
                style="width: 100%"
                @click="operandClick('x')"
              >
                  x
              </v-btn>
          </v-col>
      </v-row>
      <v-row>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(4)"
              >
                  4
              </v-btn>
          </v-col>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(5)"
              >
                  5
              </v-btn>
          </v-col>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(6)"
              >
                  6
              </v-btn>
          </v-col>
          <v-col cols="3">
               <v-btn
                outlined
                color="warning"
                rounded
                style="width: 100%"
                @click="operandClick('-')"
              >
                  -
              </v-btn>
          </v-col>
      </v-row>
      <v-row>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(1)"
              >
                  1
              </v-btn>
          </v-col>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(2)"
              >
                  2
              </v-btn>
          </v-col>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="numberClick(3)"
              >
                  3
              </v-btn>
          </v-col>
          <v-col cols="3">
               <v-btn
                outlined
                color="warning"
                rounded
                style="width: 100%"
                @click="operandClick('+')"
              >
                  +
              </v-btn>
          </v-col>
      </v-row>
      <v-row>
          <v-col cols="6">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                value="0"
                @click="numberClick(0)"
              >
                  0
              </v-btn>
          </v-col>
          <v-col cols="3">
              <v-btn
                outlined
                color="primary"
                rounded
                style="width: 100%"
                @click="operandClick('.')"
              >
                  .
              </v-btn>
          </v-col>
          <v-col cols="3">
               <v-btn
                outlined
                color="warning"
                rounded
                style="width: 100%"
                @click="solve"
              >
                  =
              </v-btn>
          </v-col>
      </v-row>
  </div>
</template>

<script>
export default {
    data () {
        return {
            results: '',
            operation: {
                'leftSide': '',
                'rightSide': '',
                'operand': '',
                'answer': ''
            },
            pastOperations: []
        }
    },
    methods: {
        numberClick(number){
            if(this.operation.answer === '')
            {
                if(this.operation.operand === '')
                {
                    this.operation.leftSide += `${number}`
                }
                else
                {
                    this.operation.rightSide += `${number}`
                }
            }
            else
            {
                this.clear()
                this.operation.leftSide += `${number}`
            }
        },
        operandClick(operand){
            this.operation.operand = operand
        },
        solve()
        {
            this.operation.answer = ' = '

            switch(this.operation.operand){
                case 'x': this.operation.answer += Number(this.operation.leftSide) * Number(this.operation.rightSide); break;
                case '/': this.operation.answer += Number(this.operation.leftSide) / Number(this.operation.rightSide); break;
                case '+': this.operation.answer += Number(this.operation.leftSide) + Number(this.operation.rightSide); break;
                case '-': this.operation.answer += Number(this.operation.leftSide) - Number(this.operation.rightSide); break;
            }
            this.pastOperations.push(this.operation)
        },
        clear(){
            this.operation.leftSide = ''
            this.operation.rightSide = ''
            this.operation.answer = ''
            this.operation.operand = ''
        }
    }
}
</script>

<style>
    .calculator{
        background-color: lightgreen;
        padding: 10px;
    }
</style>