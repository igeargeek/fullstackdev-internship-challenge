/* eslint-disable */
<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-9">
        <div class="row container">
          <span class="item-container" v-for="items in drinkingList.data">
            <img :src="items.image" />
            <p class="item-description">{{items.name}} : ${{items.price}}</p>
            <button class="btn btn-danger" v-if="items.in_stock&&coinAmount < items.price" disabled>Select</button>
            <button class="btn btn-success" v-else-if="items.in_stock&&coinAmount >= items.price" @click="selectItem(items)">Select</button>
            <button class="btn btnItemOutOfStock" v-else disabled>Out of stock</button>
          </span>
        </div>
      </div>
      <div class="col-3 coin-centainer">
        <div class="row">
          <div class="col-12">
            <h1>Insert Bank</h1>
            <span v-for="bank in bankList">
              <button class="btn btn-light" @click="inputMoney(bank)">${{bank}}</button>
            </span>
          </div>
          <div class="col-12">
            <h1>Insert Coin</h1>
            <span v-for="coin in coinList">
              <button class="btn btn-light" @click="inputMoney(coin)">${{coin}}</button>
            </span>
          </div>
        </div>
        <div class="container">
          <div class="btn-group btn-group-justified">
            <a class="btn btn-warning">Coin: ${{coinAmount}}</a>
            <a class="btn btn-outline-warning" @click="Refund()">Refund</a>
          </div>
        </div>

        <div style="background-color:white">
          <span v-for="coinList in RefundCoinList">
            <h4>${{coinList}}</h4>
          </span>
        </div>
        <div class="jumbotron">
          <div v-for="recItem in recieveItems">
            <h4>{{recItem.name}} : ${{recItem.price}}</h4>
          </div>
          <button class="btn btn-outline-success btn-block" @click="recieveItem()">Get Item & Change</button>
        </div>
      </div>
    </div>


  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    props: {
      msg: String,
      drinkingList: Object,
      coinList: Array,
      bankList: Array
    },
    data() {
      return {
        coinAmountList: [],
        coinAmount: 0,
        RefundCoinList: [],
        RefundCoin: 0,
        recieveItems: [],
        moneyList: []
      }
    },
    beforeMount() {
      this.moneyList.push(this.bankList)
      this.moneyList.push(this.coinList)  
      console.log("beforeMount",this.moneyList)
      
    },
    methods: {
      inputMoney(coin) {
        console.log("input : ", coin)
        this.coinAmount += coin;
        this.coinAmountList.push(coin);
      },
      Refund() {
        this.RefundCoinList = this.coinAmountList;
        this.coinAmount = 0;
      },
      calculateRefund() {
        // console.log("//////////////calculateRefund//////////////////")
        // this.coinList.forEach(element => {
        //   if ((this.coinAmount - element) >= 0) {
        //     this.coinAmount -= element
        //     this.RefundCoinList.push(element)
        //     this.calculateRefund();
        //   }
        // });
        console.log("//////////////calculateRefund//////////////////")
        console.log("moneyList", this.moneyList)

        this.moneyList.forEach(outer_element => {
          outer_element.forEach(inner_element => {
            if ((this.coinAmount - inner_element) >= 0) {
              this.coinAmount -= inner_element
              this.RefundCoinList.push(inner_element)
              this.calculateRefund();
            }
          })

        });
        this.coinAmount = 0;
        // console.log("this.RefundCoinList:", this.RefundCoinList)
      },
      selectItem(item) {
        this.coinAmount -= item.price
        this.recieveItems.push(item);
        this.calculateRefund()
      },
      recieveItem() {
        console.log("Clear Page");
        this.coinAmount = 0;
        this.RefundCoinList = [];
        this.recieveItems = [];
      }
    }

  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1 {
    color: mintcream;
    font-size: 20px;
  }

  p {
    color: black;
  }

  .container {
    margin-top: 10px;
    margin-bottom: 10px;
    display: flex;
    justify-content: center;

  }

  .item-container {
    border: solid 1px #353b48;
    max-width: 295px;
    /* max-height: 252px; */
    /* border: solid 1px #404040; */
    padding: 10px;
    background-color: #f5f6fa;
    border-radius: 5px;
  }

  .item-description {
    background-color: #dcdde1;
    border-radius: 5px;
  }

  .container-fluid {
    background-color: #2f3640;
    /* width: 80%; */
    border-radius: 5px;
    margin-top: 10px;
    margin-left: 10px;
    margin-right: 10px;
    margin-bottom: 10px;
    max-width: 1325px;


  }


  .coin-centainer {
    margin-top: 50px;
  }


  .btnItemOutOfStock:hover {
    cursor: not-allowed;

  }

  .btn-danger:hover {
    cursor: not-allowed;

  }

  .btn-outline-warning {
    color: #FFC107 !important
  }

  .btn-outline-warning:hover {
    color: #2F3640 !important
  }
</style>