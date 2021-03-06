# React Livestamp [![npm package][npm-badge]][npm]
A simple and html date countdown component for React

### Installation

```shell
npm install react-livestamp --save
```

### Install via Bower
```shell
bower install react-livestamp
```

## Basic Usage (start counting!)
```js
import React from 'react';
import Livestamp from 'react-livestamp';

// Dummy date
const end_date = new Date();

// add 5 hours.
end_date.setHours(end_date.getHours()+5);

class App extends React.Component {
  render() {
    return (
      <Livestamp end={end_date} />
    )
  }
}
```

## Props

* [`end`](#end)
* [`interval`](#interval)
* [`renderStamp`](#renderStamp)
* [`renderExpired`](#renderExpired)

<a name="end"></a>
##### end (required)
Accepts a **Date** object, a **String** format, or a **Number** `timestamp`.

```js

const end_time = new Date(); // Object instanceof date
const str_end = end_date.toString() // Tue Jun 14 2016 21:25:41 GMT+0300 (EEST)
const timestamp_end = end_date.getTime() // 1465928741178

<Livestamp end={end_time} />
<Livestamp end={str_end} />
<Livestamp end={timestamp_end} />
```

<a name="interval"></a>
##### interval (optional)
The second parameter for **setInterval** is optional with default value of `1000`.

<a name="renderStamp"></a>
##### renderStamp (optional)

```js
class App extends React.Component {
  renderStamp({ days, hours, minutes, seconds }) {
    return (
      <div className="react-livestamp">
        <b>{days} g {hours} s { minutes } dk {seconds} sn</b>
      </div>
    )
  }
  
  render() {
  
    return (
    
      // Default renderStamp template
      <Livestamp end={end_time} renderStamp={({ days, hours, minutes, seconds }) => (
        <div className="react-livestamp">
          <b>{days} g {hours} s { minutes } dk {seconds} sn</b>
        </div>
      )}/>

      // or may be in this way:
      <Livestamp renderStamp={this.renderStamp}>
    )
  }
}
```

<a name="renderExpired"></a>
##### renderExpired (optional)

If the livestamp ends it run this.

```js

class App extends React.Component {
  renderExpired({ days, hours, minutes, seconds }) {
    return (
      <div className="react-livestamp">
        Date Expired
      </div>
    )
  }
  
  render() {
  
    return (
    
      // Default renderStamp template
      <Livestamp end={end_time} renderExpired={() => (
        <div className="react-livestamp">
          Date Expired
        </div>
      )}/>

      // or may be in this way:
      <Livestamp renderExpired={this.renderExpired}>
    )
  }
}
```


## Development

```shell
npm install
npm start # watch and build.
```

[npm-badge]: https://img.shields.io/npm/v/react-livestamp.svg?style=flat-square
[npm]: https://www.npmjs.org/package/react-livestamp
