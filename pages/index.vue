<template>
  <div>
    <div class="body">
      <div class="container">
        <div class="result">
          <p class="text title">Your Result</p>
          <div class="result-circle">
            <div class="result-circle__item">
              <h1>76</h1>
              <p class="text">of 100</p>
            </div>
          </div>
          <div class="result-body text">
            <h3>Great</h3>
            <p>You scored higher than 65% of the people who have taken these tests.</p>
          </div>
        </div>
        <div class="summary ">
          <p class="summary-title text title">Summary</p>
          <div v-for="(item, index) in items" :key="index" :class="`summary-component` + ` ` + item.class">
            <div>
              <img :src="require(`~/static/${item.icon}`)" alt="Icon" />
              <p>{{ item.category }}</p>
            </div>
            <p class="result-number">{{ item.score }} <span class="result-number__max">/ 100</span></p>
          </div>
          <div class="continue-btn">
            <p class="relative">Continue</p>
          </div>
        </div>
      </div>
    </div>
    <br class="clearBoth" />

    <attribution />
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      items: [
        {
          "category": "Reaction",
          "class": "reaction",
          "score": 80,
          "icon": "images/icon-reaction.svg"
        },
        {
          "category": "Memory",
          "class": "memory",
          "score": 92,
          "icon": "images/icon-memory.svg"
        },
        {
          "category": "Verbal",
          "class": "verbal",
          "score": 61,
          "icon": "images/icon-verbal.svg"
        },
        {
          "category": "Visual",
          "class": "visual",
          "score": 72,
          "icon": "images/icon-visual.svg"
        }
      ]
    }
  },
}
</script>

<style scoped>
.body {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 50px;
  margin-bottom: 0px
}

/* .clearBoth {
  clear: both;
} */

.container {
  /* width: 736px; */
  height: 100%;
  background-color: white;
  display: flex;
  border-radius: 50px;
}


.result {
  /* float: left; */
  display: grid;
  place-items: center;
  align-content: center;
  gap: 25px;
  width: 368px;
  height: 512px;
  padding-left: 50px;
  padding-right: 50px;
  border-radius: 30px;
  color: var(--white);
  background: linear-gradient(to bottom, var(--lightSlateBlue), var(--lightRoyalBlue)59.72%);
}

.title {
  font-weight: var(--fwMedium);
  font-size: 24px;
}

.result-circle {
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 200px;
  height: 200px;
  background: linear-gradient(to bottom, var(--violetBlue), var(--lightRoyalBlue));
}

.result-circle__item h1 {
  font-size: 73px;
  font-weight: var(--fwExtraBold);
}

.result-circle__item p {
  color: var(--lightLavender);
}

p,
span {
  font-size: var(--forParagraph);
}

.text {
  text-align: center;
}

.result-body h3 {
  margin-bottom: 25px;
}

.result-body p {
  color: var(--lightLavender);
}

.summary {
  display: flex;
  gap: 20px;
  width: 368px;
  height: 512px;
  padding-left: 50px;
  padding-right: 50px;
  border-radius: 30px;
  background: var(--white);
  flex-direction: column;
  flex-wrap: wrap;
  align-content: center;
  align-items: flex-start;
  justify-content: center
}
/*  */

.summary-component {
  display: flex;
  align-items: center;
  padding: 10px;
  flex-wrap: nowrap;
  justify-content: space-between;
  width: 289px;
  height: 55px;
  border-radius: 10px;
}

.continue-btn {
  padding: 10px;
  width: 289px;
  height: 55px;
  border-radius: 50px;
  color: var(--white);
  background-color: var(--darkGreyBlue);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.3s ease-in-out;
  position: relative;

}

.continue-btn::after {
  color: var(--white);
  content: "";
  position: absolute;
  left: 0;
  border-radius: 50px;
  top: 0;
  width: 100%;
  height: 100%;
  transition: opacity 0.5s;
  background: linear-gradient(to bottom, var(--violetBlue), var(--lightRoyalBlue));
  opacity: 0;
}

.continue-btn:hover::after {
  opacity: 1;
}

.continue-btn .relative {
  z-index: 10;
  position: relative;
}

.reaction {
  background-color: var(--lightRedOpt);
  color: var(--lightRed);

}

.memory {
  background-color: var(--orangeYellowOpt);
  color: var(--orangeYellow);
}

.verbal {
  background-color: var(--greenTealOpt);
  color: var(--greenTeal);
}

.visual {
  background-color: var(--cobaltBlueOpt);
  color: var(--cobaltBlue);
}


.result-number {
  font-weight: var(--fwExtraBold);
  color: var(--darkGreyBlue);
}

.result-number__max {
  color: var(--pureGrey);
  font-weight: 400;
}


.summary-component div {
  display: flex;
  align-items: center;
  gap: 10px
}


@media screen and (max-width: 375px) {
  .body {
    margin: 0px;
  }
  .container {
    flex-direction: column;
  }
  .result {
    border-radius: 0px 0px 30px 30px;
  }

  .summary {
    border-radius: none;
  }
  
}
</style>


