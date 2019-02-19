# Time Until

A single purpose javascript module that compares two dates and reports the distance in user friendly years, months, weeks, days, hours, and seconds.

## Interface

### timeUntil(*date*, *context*)
- ***date***: the input date, as a valid javascript *`Date`* object
- ***context***: a comparison date, defaults to the current time using *`new Date()`*

Basic usage:
```js
const { unit, value, string, past } = timeUntil(date)

console.log('Unit', unit) // /(now)|((second|minute|hour|day|week|month|year)s?)/
console.log('Value', value) // /(d+)/
console.log('String', string) // 10 weeks ago, 5 days time, 2 hours, 1 minute ago, now
console.log('Past', past) // true|false
```

Calling `timeUntil(date)` returns an object; the `.string` property can be displayed straight the user, but if you want the break down, then the `.unit`, `.value`, and `.past` / future status is available as well.

## Sample output

If assuming *now* as being *Sun Feb 12 2017 23:08:56 GMT*:
```
Time Until
  No change
    √ should interpret 'Sun, 12 Feb 2017 23:08:56 GMT' as now
  Seconds
    √ should interpret 'Sun, 12 Feb 2017 23:09:01 GMT' as 5 seconds
    √ should interpret 'Sun, 12 Feb 2017 23:09:58 GMT' as 62 seconds
  Minutes
    √ should interpret 'Sun, 12 Feb 2017 23:13:56 GMT' as 5 minutes
    √ should interpret 'Sun, 13 Feb 2017 01:07:56 GMT' as 119 minutes
  Hours
    √ should interpret 'Sun, 13 Feb 2017 04:08:56 GMT' as 5 hours
    √ should interpret 'Sun, 14 Feb 2017 22:08:56 GMT' as 47 hours
  Days
    √ should interpret 'Sun, 17 Feb 2017 23:08:56 GMT' as 5 days
    √ should interpret 'Sun, 20 Feb 2017 23:08:56 GMT' as 8 days
    √ should interpret 'Sun, 04 Mar 2017 23:08:56 GMT' as 20 days
  Weeks
    √ should interpret 'Sun, 05 Mar 2017 23:08:56 GMT' as 3 weeks
    √ should interpret 'Sun, 12 Mar 2017 23:08:56 GMT' as 4 weeks
    √ should interpret 'Sun, 22 Mar 2017 23:08:56 GMT' as 5 weeks
    √ should interpret 'Sun, 12 Apr 2017 23:08:56 GMT' as 8 weeks
  Months
    √ should interpret 'Sun, 22 May 2017 23:08:56 GMT' as 3 months
    √ should interpret 'Sun, 12 Jul 2017 23:08:56 GMT' as 5 months
    √ should interpret 'Sun, 12 Feb 2018 23:08:56 GMT' as 12 months
    √ should interpret 'Sun, 12 Jan 2019 23:08:56 GMT' as 23 months
    √ should interpret 'Sun, 12 Feb 2019 23:08:56 GMT' as 24 months
  Years
    √ should interpret 'Sun, 13 Feb 2019 23:08:56 GMT' as 2 years
    √ should interpret 'Sun, 13 Feb 2022 23:08:56 GMT' as 5 years
```

## Usage

As a node module, use `npm install time-until` to bring the module into your repository, and then require the module into your code:

```js
const timeUntil = require('time-until')

const dateToCheck = Date.parse('Sun, 17 Feb 2017 23:08:56 GMT')
console.log(timeUntil(dateToCheck), 'until', dateToCheck)
```

For use on a web page, include `time-until.js` into your project using a script tag, for example:

```html
<!DOCTYPE html>
<html>
  <head>
    <script type="text/javascript" src="js/time-until.js"></script>
  </head>
  <body>
  ...
  <script>
    const dateToCheck = Date.parse('Sun, 17 Feb 2017 23:08:56 GMT')
    document.write(window.timeUntil(dateToCheck) + ' until ' + dateToCheck)
  </script>
  </body>
</html>
```

## Development

This project uses `nodejs` and `mocha` for testing. The project uses `standard` for linting.

To run the tests locally, checkout this repo using git, then run:

```js
npm install
npm test
```
