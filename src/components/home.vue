<!-- <template>
  <div
    class="wrap transform d-flex justify-content-center align-items-center"
    :style="checkStyleByTheme('wrap')"
  >
    <div class="home" :style="checkStyleByTheme('home')">
      <div
        class="header d-flex justify-content-between align-items-end"
        :style="checkStyleByTheme('header')"
      >
        <span style="font-size: 30px; line-height: 1">calc</span>
        <div class="header-theme d-flex align-items-end">
          <span style="font-weight: 400">THEME</span>
          <div class="toggle">
            <div class="nums">
              <div
                class="num d-flex justify-content-center"
                v-for="i in 3"
                @click="setTheme(i)"
              >
                {{ i }}
              </div>
            </div>
            <div class="switch" :style="checkStyleByTheme('switch')">
              <div
                class="circle transform"
                :class="checkCircleTheme(currentTheme)"
                :style="checkStyleByTheme('circle')"
              ></div>
            </div>
          </div>
        </div>
      </div>

      <div
        class="result d-flex flex-column justify-content-end"
        :style="checkStyleByTheme('result')"
      >
        <span class="previous-factor">{{ calculus }}</span>
        <span class="current-factor">{{ currentFactor }}</span>
      </div>
      <div class="keyboard" :style="checkStyleByTheme('keyboard')">
        <div
          v-for="(item, index) in keyboardItems"
          :key="index"
          class="keyboard-item d-flex align-items-center justify-content-center"
          :class="`${item.value} ${
            item.label === clickedNum ? 'keyboard-item-checked' : ''
          }`"
          :style="
            item.label === hoverNum
              ? checkStyleByHover(checkKeyboardForCss(item.value))
              : checkStyleByTheme(checkKeyboardForCss(item.value))
          "
          @click="clickNum(item.label)"
          @mouseover="hoverOnNum(item.label)"
          @mouseleave="hoverOnNum('')"
        >
          {{ item.label }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const currentTheme = ref<number>(1);
const clickedNum = ref<string>("");
const hoverNum = ref<string>("");
const currentFactor = ref<string>("0");
const previousFactor = ref<string>("");
const constFactor = ref<string>("");
const operation = ref<string>("");
const calculus = ref<string>("");

const hoverOnNum = (val: string) => {
  hoverNum.value = val;
};

const checkCircleTheme = (val: number) => {
  switch (val) {
    case 1:
      return "circle-theme1";
    case 2:
      return "circle-theme2";
    case 3:
      return "circle-theme3";
    default:
      return "";
  }
};
const setTheme = (val: number) => {
  currentTheme.value = val;
};

const keyboardItems: any[] = [
  {
    label: "7",
    value: 7,
  },
  {
    label: "8",
    value: 8,
  },
  {
    label: "9",
    value: 9,
  },
  {
    label: "del",
    value: "del",
  },
  {
    label: "4",
    value: 4,
  },
  {
    label: "5",
    value: 5,
  },
  {
    label: "6",
    value: 6,
  },
  {
    label: "+",
    value: "add",
  },
  {
    label: "1",
    value: 1,
  },
  {
    label: "2",
    value: 2,
  },
  {
    label: "3",
    value: 3,
  },
  {
    label: "-",
    value: "sub",
  },
  {
    label: ".",
    value: ".",
  },
  {
    label: "0",
    value: "0",
  },
  {
    label: "/",
    value: "div",
  },
  {
    label: "*",
    value: "mul",
  },
  {
    label: "reset",
    value: "reset",
  },
  {
    label: "=",
    value: "resolve",
  },
];

const checkKeyboardForCss = (val: string) => {
  switch (val) {
    case "resolve":
      return "resolve";
    case "reset":
      return "reset";
    case "del":
      return "del";
    default:
      return "keyboard-item";
  }
};

const checkKeyboardForLogic = (val: string) => {
  switch (val) {
    case ".":
      return ".";
    case "/":
      return "operation";
    case "*":
      return "operation";
    case "-":
      return "operation";
    case "+":
      return "operation";
    case "del":
      return "del";
    case "reset":
      return "reset";
    case "=":
      return "=";
    default:
      return "numberkey";
  }
};

const checkStyleByTheme = (className: string) => {
  if (currentTheme.value === 1) {
    switch (className) {
      case "wrap":
        return "background-color: hsl(222, 26%, 31%);";
      case "header":
        return "color: #fff;";
      case "switch":
        return "background-color: hsl(223, 31%, 20%);";
      case "circle":
        return "background-color: hsl(6, 63%, 50%);";
      case "result":
        return "background-color: hsl(224, 36%, 15%);  color: hsl(0, 0%, 100%);";
      case "keyboard":
        return "background-color: hsl(223, 31%, 20%);";
      case "keyboard-item":
        return "background-color: hsl(30, 25%, 89%); box-shadow: 2px 5px hsl(28, 16%, 65%); color: hsl(221, 14%, 31%)";
      case "del":
        return "background-color: hsl(225, 21%, 49%); box-shadow: 2px 5px hsl(224, 28%, 35%); color: white;";
      case "reset":
        return "background-color: hsl(225, 21%, 49%); box-shadow: 2px 5px hsl(224, 28%, 35%); color: white;";
      case "resolve":
        return "background-color: hsl(6, 63%, 50%);  box-shadow: 2px 5px hsl(6, 70%, 34%);";
      default:
        return "";
    }
  } else if (currentTheme.value === 2) {
    switch (className) {
      case "wrap":
        return "background-color: hsl(0, 0%, 90%);";
      case "header":
        return "color: hsl(60, 10%, 19%)";
      case "switch":
        return "background-color: hsl(0, 5%, 81%);";
      case "circle":
        return "background-color: hsl(25, 98%, 40%);";
      case "result":
        return "background-color: hsl(0, 0%, 93%);  color: hsl(60, 10%, 19%);";
      case "keyboard":
        return "background-color: hsl(0, 5%, 81%);";
      case "keyboard-item":
        return "background-color: hsl(30, 25%, 89%); box-shadow: 2px 5px hsl(28, 16%, 65%); color: hsl(60, 10%, 19%)";
      case "del":
        return "background-color: hsl(185, 42%, 37%); box-shadow: 2px 5px hsl(185, 58%, 25%);  color: white;";
      case "reset":
        return "box-shadow: 2px 5px hsl(185, 58%, 25%);  background-color: hsl(185, 42%, 37%);  color: white;";
      case "resolve":
        return "background-color: hsl(25, 98%, 40%);  box-shadow: 2px 5px hsl(25, 99%, 27%);";
      default:
        return "";
    }
  } else {
    switch (className) {
      case "wrap":
        return "background-color: hsl(268, 75%, 9%);";
      case "header":
        return "color: hsl(52, 100%, 62%)";
      case "switch":
        return "background-color: hsl(268, 71%, 12%);";
      case "circle":
        return "background-color: hsl(176, 100%, 44%);";
      case "result":
        return "background-color: hsl(268, 71%, 12%);  color: hsl(52, 100%, 62%)";
      case "keyboard":
        return "background-color: hsl(268, 71%, 12%);";
      case "keyboard-item":
        return "background-color: #331b4d; box-shadow: 2px 5px #891e9c; color: hsl(52, 100%, 62%)";
      case "del":
        return "background-color: hsl(281, 89%, 26%); box-shadow: 2px 5px hsl(285, 91%, 52%); color: white;";
      case "reset":
        return "background-color: hsl(281, 89%, 26%); box-shadow: 2px 5px hsl(285, 91%, 52%); color: white;";
      case "resolve":
        return "background-color: hsl(176, 100%, 44%);  box-shadow: 2px 5px hsl(177, 92%, 70%);";
      default:
        return "";
    }
  }
};

const checkStyleByHover = (className: string) => {
  if (currentTheme.value === 1) {
    switch (className) {
      case "del":
        return "background-color: #a2b3e1; box-shadow: 2px 5px hsl(224, 28%, 35%); color: white;";
      case "reset":
        return "background-color: #a2b3e1; box-shadow: 2px 5px hsl(224, 28%, 35%); color: white;";
      case "resolve":
        return "background-color: #f96c5b; ox-shadow: 2px 5px hsl(224, 28%, 35%);";
      default:
        return "background-color: white; box-shadow: 2px 5px hsl(28, 16%, 65%);";
    }
  } else if (currentTheme.value === 2) {
    switch (className) {
      case "del":
        return "background-color: #61b5bd; box-shadow: 2px 5px hsl(185, 58%, 25%);; color: white;";
      case "reset":
        return "background-color: #61b5bd; box-shadow: 2px 5px hsl(185, 58%, 25%);; color: white;";
      case "resolve":
        return "background-color: #ff8b38; box-shadow: 2px 5px hsl(25, 99%, 27%);";
      default:
        return "background-color: white; box-shadow: 2px 5px hsl(28, 16%, 65%); color: hsl(60, 10%, 19%)";
    }
  } else {
    switch (className) {
      case "del":
        return "background-color: #8631b0; box-shadow: 2px 5px hsl(290, 70%, 36%); color: white;";
      case "reset":
        return "background-color: #8631b0; box-shadow: 2px 5px hsl(290, 70%, 36%); color: white;";
      case "resolve":
        return "background-color: #94fff9; box-shadow: 2px 5px hsl(177, 92%, 70%); color: hsl(198, 20%, 13%)";
      default:
        return "background-color: #6b34ac; box-shadow: 2px 5px #891e9c; color: hsl(52, 100%, 62%)";
    }
  }
};

const countDot = () => {
  const splitArr = currentFactor.value.split(/\./);
  return splitArr.length - 1;
};

const checkFinishedCal = () => {
  const splitArr = calculus.value.split(/\=/);
  return splitArr.length - 1;
};

const clickNum = (val: string) => {
  // CSS part
  clickedNum.value = val;
  setTimeout(() => {
    clickedNum.value = "";
  }, 150);

  //Logic part
  if (currentFactor.value === "0") {
    currentFactor.value = "";
    handleClickLogic(val);
  } else {
    handleClickLogic(val);
  }
};

const handleClickLogic = (val: string) => {
  switch (checkKeyboardForLogic(val)) {
    case ".":
      const dot = countDot();
      if (currentFactor.value === "") {
        currentFactor.value = "0";
      }
      if (!dot) {
        currentFactor.value += val;
      }
      return;
    case "operation":
      operation.value = val;
      if (!calculus.value) {
        calculus.value = currentFactor.value + operation.value;
        previousFactor.value = currentFactor.value;
        currentFactor.value = "0";
        return;
      }

      if (checkFinishedCal()) {
        calculus.value = "";
        calculus.value = currentFactor.value + operation.value;
        previousFactor.value = currentFactor.value;
        currentFactor.value = "0";
        return;
      }
      if (!/^\d+$/.test(calculus.value)) {
        calculus.value = calculus.value.slice(0, -1) + operation.value;
        currentFactor.value = "0";
        return;
      }
      return;
    case "del":
      if (checkFinishedCal()) {
        currentFactor.value = "0";
        previousFactor.value = "";
        operation.value = "";
        calculus.value = "";
        constFactor.value = "";
      } else {
        currentFactor.value = "0";
      }
      return;
    case "reset":
      currentFactor.value = "0";
      previousFactor.value = "";
      operation.value = "";
      constFactor.value = "";
      calculus.value = "";
      return;
    case "=":
      handleCalLogic();
      return;
    default:
      if (checkFinishedCal()) {
        calculus.value = "";
        currentFactor.value = val;
      } else if (currentFactor.value.length < 15) {
        currentFactor.value += val;
      }
      return;
  }
};

const handleCalLogic = () => {
  // if (!operation.value) return;
  if (previousFactor.value && currentFactor.value && !constFactor.value) {
    switch (operation.value) {
      case "+":
        const addResult =
          parseFloat(previousFactor.value) + parseFloat(currentFactor.value);
        previousFactor.value = currentFactor.value;
        calculus.value += currentFactor.value + "=";
        currentFactor.value = addResult.toString();
        operation.value = "+";
        return;
      case "-":
        const subResult =
          parseFloat(previousFactor.value) - parseFloat(currentFactor.value);
        previousFactor.value = currentFactor.value;
        calculus.value += currentFactor.value + "=";
        currentFactor.value = subResult.toString();
        operation.value = "-";
        return;
      case "*":
        const mulResult =
          parseFloat(previousFactor.value) * parseFloat(currentFactor.value);
        previousFactor.value = currentFactor.value;
        calculus.value += currentFactor.value + "=";
        currentFactor.value = mulResult.toString();
        operation.value = "*";
        return;
      case "/":
        const divResult =
          parseFloat(previousFactor.value) / parseFloat(currentFactor.value);
        previousFactor.value = currentFactor.value;
        calculus.value += currentFactor.value + "=";
        currentFactor.value = divResult.toString();
        operation.value = "/";
        return;
      default:
        return;
    }
  } else {
    if (!constFactor.value) {
      constFactor.value = previousFactor.value;
    }
    switch (operation.value) {
      case "+":
        const addResult =
          parseFloat(previousFactor.value) + parseFloat(constFactor.value);
        calculus.value = previousFactor.value + "+" + constFactor.value + "=";
        currentFactor.value = addResult.toString();
        previousFactor.value = currentFactor.value;
        operation.value = "+";
        return;
      case "-":
        const subResult =
          parseFloat(previousFactor.value) - parseFloat(constFactor.value);
        calculus.value = previousFactor.value + "-" + constFactor.value + "=";
        currentFactor.value = subResult.toString();
        previousFactor.value = currentFactor.value;
        operation.value = "-";
        return;
      case "*":
        const mulResult =
          parseFloat(previousFactor.value) * parseFloat(constFactor.value);
        calculus.value = previousFactor.value + "*" + constFactor.value + "=";
        currentFactor.value = mulResult.toString();
        previousFactor.value = currentFactor.value;
        operation.value = "*";
        return;
      case "/":
        const divResult =
          parseFloat(previousFactor.value) / parseFloat(constFactor.value);
        calculus.value = previousFactor.value + "/" + constFactor.value + "=";
        currentFactor.value = divResult.toString();
        previousFactor.value = currentFactor.value;
        operation.value = "/";
        return;
      default:
        return;
    }
  }
};

const calFunc = (firtsAgr: any, secondAgr: any, val:
) => {
  const result =
};
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=League+Spartan:wght@300;400;600;700&display=swap");
.transform {
  transition: all 0.3s ease;
  background-color: hsl(281, 59%, 56%);
}
.wrap {
  height: 100vh;
  width: 100vw;
}
.home {
  width: 500px;
  font-family: "League Spartan", sans-serif;
  font-weight: 700;
}

.header {
  height: 40px;
}
.header-theme {
  gap: 20px;
  position: relative;
  height: 100%;
}
.toggle {
  width: 80px;
}
.nums {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  height: 100%;
  width: 80px;
  z-index: 2;
  position: absolute;
  top: 0;
  cursor: pointer;
}
.switch {
  height: 20px;
  border-radius: 10px;
  width: 100%;
  z-index: 1;
  display: flex;
  align-items: center;
}
.circle {
  height: 14px;
  width: 14px;
  border-radius: 50%;
}
.circle-theme1 {
  margin-left: 6px;
}
.circle-theme2 {
  margin-left: 33px;
}
.circle-theme3 {
  margin-left: 59px;
}

/* screen */
.result {
  font-size: 50px;
  text-align: center;
  line-height: 1;
  padding: 20px;
  border-radius: 8px;
  margin-top: 20px;
}
.previous-factor {
  font-size: 25px;
  text-align: right;
  padding-bottom: 5px;
  min-height: 30px;
}
.current-factor {
  text-align: right;
}
.operation {
  font-size: 40px;
}
/* keyboard */
.keyboard {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(5, 1fr);
  gap: 25px;
  text-transform: uppercase;
  padding: 20px;
  margin-top: 20px;
  border-radius: 8px;
  height: 380px;
}
.keyboard-item {
  font-size: 30px;
  cursor: pointer;
  border-radius: 8px;
}
.keyboard .keyboard-item-checked {
  box-shadow: none !important;
  margin-top: 2px;
  margin-left: 2px;
}
.reset {
  grid-column-start: 1;
  grid-column-end: 3;
}
.resolve {
  grid-column-start: 3;
  grid-column-end: 5;
  color: white;
}
</style> -->

<template>
  <div class="wrap">
    <div v-if="!isopen" class="wrap-card">
      <div class="card">
        <div class="heart">
          <img
            src="../design/Screenshot 2023-11-20 160959.png"
            alt=""
            @click="open"
          />
        </div>
      </div>
      <div class="text">NHẤP EM ĐI ANH</div>
    </div>
    <div v-else class="letter">
      <h1>THANKS YOU - SIN TRÂN THÀNH CỦM ƠNK</h1>
      <el-icon :size="100" style="color: rgb(11, 255, 11); margin-top: -60px"
        ><Select />
      </el-icon>
      <p>
        Không biết nói chi ngoài cảm ơn anh - người thầy đầu tiên trên trường
        đời cụa em.
      </p>
      <p>Anh Vinh mãi iu, mãi đỉnk</p>
      <div class="dot">
        <div class="line">
          <img
            src="../design/Screenshot 2023-11-20 165041.png"
            style="margin-right: 30px"
            alt=""
          />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
        </div>
        <div class="line">
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
        </div>
        <div class="line">
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
        </div>
        <div class="line">
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
        </div>
        <div class="line">
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
        </div>
        <div class="line">
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
        </div>
        <div class="line">
          <img src="../design/Screenshot 2023-11-20 165041.png" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const isopen = ref(false);
const open = () => {
  isopen.value = true;
};
</script>

<style scoped>
.dot {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
.dot img {
  height: 50px;
}
.letter {
  color: #fff;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
svg {
  width: 100px;
}

.heart img {
  width: 200px;
  aspect-ratio: 1;
  object-fit: cover;
  --_m: radial-gradient(#000 69%, #0000 70%) 84.5%/50%;
  -webkit-mask-box-image: var(--_m);
  mask-border: var(--_m);
  clip-path: polygon(-41% 0, 50% 91%, 141% 0);
  /* box-shadow: 5px 10px 18px red; */
}

/* fallback until better support for mask-border */
@supports not (-webkit-mask-box-image: var(--_m)) {
  img {
    --_m: radial-gradient(at 70% 31%, #000 29%, #0000 30%),
      radial-gradient(at 30% 31%, #000 29%, #0000 30%),
      linear-gradient(#000 0 0) bottom/100% 50% no-repeat;
    -webkit-mask: var(--_m);
    mask: var(--_m);
  }
}

.wrap {
  height: 100vh;
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: gray;
  flex-direction: column;
}
.wrap-card {
  position: relative;
}
.card {
  width: 0;
  height: 0;
  border-top: 200px solid #fff;
  border-right: 250px solid #eee;
  border-bottom: 200px solid #ddd;
  border-left: 250px solid #eee;
  border-radius: 10px;
  position: relative;
}

.heart {
  transform: translate(-50%, -50%) rotate(45deg);
  position: absolute;
  animation: heartbeat 1.4s linear infinite;
  filter: drop-shadow(0 0 10px #ff3e60);
  cursor: pointer;
}
.text {
  font-size: 20px;
  font-weight: 700;
  color: #fff;
  display: flex;
  justify-content: center;
}
@keyframes heartbeat {
  0% {
    transform: translate(-50%, -50%) rotate(0) scale(0.5);
  }
  25% {
    transform: translate(-50%, -50%) rotate(0) scale(1);
  }
  30% {
    transform: translate(-50%, -50%) rotate(0) scale(1.2);
  }
  50% {
    transform: translate(-50%, -50%) rotate(0) scale(1.4);
  }
  70% {
    transform: translate(-50%, -50%) rotate(0) scale(1.2);
  }
  100% {
    transform: translate(-50%, -50%) rotate(0) scale(0.5);
  }
}
</style>
