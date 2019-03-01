# 法定节假日判断库

## 目的&用途

判断是否法定节假日，有几种用途：

1. 确定当天是否需要上班
1. 确定当天是“本来无需上班但调成上班”或“本来需要上班但调成无需上班”，用于日历上显示“休”和“班”
1. 确定当天是节日还是普通周末休息，用于确定加班是三倍工资，还是两倍工资

## 方案

按是否休息分类：

1. 休息
1. 上班

按日历上显示“休”或“班”分类：

1. 日历上不显示
1. 日历上显示“休”
1. 日历上显示“班”

按加班工资倍数分类：

1. 正常工作日
1. 周末，加班双倍工资
1. 节假日，加班三倍工资

## API

```javascript
// 判断当天是休息还是上班
const REST_REST = 0;
const REST_WORK = 1;

function isRest(date) {}

// 判断当天显示“休”或“班”
const DISPLAY_NONE = 0;
const DISPLAY_REST = 1;
const DISPLAY_WORK = 2;

function displayWork(date) {}

// 判断当天加班工资倍数
const SALARY_SINGLE = 1;
const SALARY_DOUBLE = 2;
const SALARY_TRIPLE = 3;

function salaryTimes(date) {}

// export
const chinaholiday = {
    REST_REST,
    REST_WORK,
    isRest,

    DISPLAY_NONE,
    DISPLAY_REST,
    DISPLAY_WORK,
    displayWork,

    SALARY_SINGLE,
    SALARY_DOUBLE,
    SALARY_TRIPLE
    salaryTimes
};

module.exports = chinaholiday;
```

## 扩展性

1. 如果要扩展到其他年份，只需根据国家出台的法定节假日信息简单配置json数据即可
1. 如果要推算其他节气或农历节日，需要有对应的节气或农历Calendar库
