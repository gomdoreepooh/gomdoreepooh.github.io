---
title: DateRangePicker 사용하기
category: 개발
page : 3/3
---

## 개요

통계분석에는 [DateRangePicker](http://adphorus.github.io/react-date-range/)를 사용했으며, 한글화, 날짜 프리셋 추가, 테마를 위해 몇가지 수정사항을 추가했다. CSS는 통계분석 프로젝트에 대부분 추가했지만, table과 관련된 일부 CSS는 DateRangePicker 컴포넌트 원본 파일을 수정할 수 밖에 없었기 때문에 [별도의 브랜치](https://github.com/Jravvit/react-date-range)로 옮겼다.

## Calendar.js

39번째 줄에 한글화를 위한 Locale 코드를 추가했다. 최신 버전에서는 이 부분이 개선되어 코드에 직접 넣지 않고도 지역화를 할 수 있도록 업데이트된 것 같다.

```js
_moment.locale('ko')
```

## defaultRanges.js
기본 Preset을 한글로 변경하고, 어제, 분기, D-180 등 기존에 없던 프리셋을 추가했다. Moment.js를 사용하면 다른 프리셋도 쉽게 추가할 수 있다. 참고로 주간, 월간, 분기, 연간은 "오늘이 포함된 기간"을 의미한다. 즉, 월간이면 오늘(3/27)이 포함된 3월 전체를 의미하고, 30일은 오늘부터 30일 전까지를 의미한다.
```js
'use strict';

Object.defineProperty(exports, '__esModule', {
  value: true
});
exports['default'] = {
  '오늘': {
    startDate: function startDate(now) {
      return now;
    },
    endDate: function endDate(now) {
      return now;
    }
  },

  '어제': {
    startDate: function startDate(now) {
      return now.add(-1, 'days');
    },
    endDate: function endDate(now) {
      return now.add(-1, 'days');
    }
  },

  '주간': {
    startDate: function startDate(now) {
      return now.startOf('week');
    },
    endDate: function endDate(now) {
      return now.endOf('week');
    }
  },

  '월간': {
    startDate: function startDate(now) {
      return now.startOf('month');
    },
    endDate: function endDate(now) {
      return now.endOf('month');
    }
  },

  '분기': {
    startDate: function startDate(now) {
      return now.startOf('quarter');
    },
    endDate: function endDate(now) {
      return now.endOf('quarter');
    }
  },

  '연간': {
    startDate: function startDate(now) {
      return now.startOf('year');
    },
    endDate: function endDate(now) {
      return now.endOf('year');
    }
  },

  '':{},

  '7일': {
    startDate: function startDate(now) {
      return now.add(-6, 'days');
    },
    endDate: function endDate(now) {
      return now;
    }
  },

  '30일': {
    startDate: function startDate(now) {
      return now.add(-29, 'days');
    },
    endDate: function endDate(now) {
      return now;
    }
  },

  '90일': {
    startDate: function startDate(now) {
      return now.add(-89, 'days');
    },
    endDate: function endDate(now) {
      return now;
    }
  },

  '180일': {
    startDate: function startDate(now) {
      return now.add(-179, 'days');
    },
    endDate: function endDate(now) {
      return now;
    }
  },

  '365일': {
    startDate: function startDate(now) {
      return now.add(-364, 'days');
    },
    endDate: function endDate(now) {
      return now;
    }
  }
};
module.exports = exports['default'];
```

## styles.js

31번째 줄의 defaultTheme를 아래와 같이 변경한다.

```js
var defaultTheme = {
  DateRange: {
    boxSizing: 'border-box',
    background: '#ffffff',
    clear: 'both',
    padding:0,
  },

  Calendar: {
    background: '#ffffff',
    display: 'inline-block',
    boxSizing: 'border-box',
    letterSpacing: 0,
    color: '#000000'
  },

  Day: {
    boxSizing: 'border-box',
    display: 'inline-block',
    letterSpacing: 'initial',
    textAlign: 'center',
    fontSize: 11,
    cursor: 'pointer',
    transition: 'transform .1s ease',
    color: '#666'
  },

  DayPassive: {
    opacity: 0,
    cursor: 'normal'
  },

  DayHover: {
    background: '#bdc3c7'
  },

  DayToday: {},

  DayActive: {
    background: '#95a5a6',
    color: '#ffffff',
    transform: 'scale(0.9)'
  },

  DaySelected: {
    background: '#48B0F7',
    color: '#ffffff',
    fontWeight: 600
  },

  DayStartEdge: {},

  DayEndEdge: {},

  DayInRange: {
    background: '#eee',
    color: '#aaa'
  },

  Weekday: {
    boxSizing: 'border-box',
    display: 'inline-block',
    letterSpacing: 'initial',
    textAlign: 'center',
    fontSize: 12,
    fontWeight: '600',
    marginBottom: 1
  },

  MonthAndYear: {
    textAlign: 'center',
    boxSizing: 'border-box',
    fontSize: 12,
    padding: '10px 0',
    height: 38,
    lineHeight: '18px'
  },

  MonthButton: {
    display: 'block',
    boxSizing: 'border-box',
    height: 18,
    width: 18,
    padding: 0,
    margin: '0 10px',
    border: 'none',
    background: 'transparent',
    boxShadow: 'none',
    outline: 'none'
  },

  MonthArrow: {
    display: 'block',
    width: 0,
    height: 0,
    padding: 0,
    margin: 0,
    border: '4px solid transparent',
    textAlign: 'center'
  },

  MonthArrowPrev: {
    borderRightWidth: '6px',
    borderRightColor: '#34495e',
    marginLeft: 1
  },

  MonthArrowNext: {
    borderLeftWidth: '6px',
    borderLeftColor: '#34495e',
    marginLeft: 7
  },

  PredefinedRanges: {
    display: 'inline-block',
    verticalAlign: 'top',
    align: 'left',
    margin: 0
  },

  PredefinedRangesItem: {
    display: 'inline-block',
    fontSize: 12,
    color: '#2c3e50',
    padding: '6px 10px',
    textDecoration: 'none',
    marginBottom: 0,
    marginLeft:-1
  },

  PredefinedRangesItemActive: {
    color: '#48B0F7',
    fontWeight: 600
  }
};
```
