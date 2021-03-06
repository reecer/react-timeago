![React-TimeAgo](http://naman.s3.amazonaws.com/react-timeago.png)

A simple time-ago component for ReactJs.

## Usage:

React-timeago is a very simple component that takes a date prop and returns a span with live updating date in a time-ago format. The date will update every second for a minute, every minute for the next 5 minutes, Every 5 minutes for the hour, Every hour for a day, every day after that, and so on.

React-TimeAgo does the minimum amount of updates necessary.

```
<TimeAgo date="Aug 29, 2014" />

// OR in vanilla JS

React.createElement(TimeAgo, {date: 'Aug 29, 2014'})

```

#### Props

###### date (required)
Date is a date in the past or the future. This can be a Date Object, A UTC datestring or number of milliseconds since epoch time.

###### live (optional)
React-Timeago is live by default and will auto update it's value. However, if you don't want this behaviour, you can set live:false.

###### formatter (optional)
A function that takes four arguments:
  - value : An integer value, already rounded off
  - unit : A string representing the unit in english. This could be one of:
    - 'second'
    - 'minute'
    - 'hour'
    - 'day'
    - 'week'
    - 'month'
    - 'year'
  - suffux : A string. This can be one of
    - 'ago'
    - 'from now'
  - date: The actual date you are trying to represent. Use this for a more custom format for showing your date.

Here are some examples of what the formatter function will receive:

- '5 minutes ago' => formatter(5, 'minute', 'ago')
- '1 year from now' => formatter(1, 'year', 'from now')

The formatter function is a simple way to extend the functionality of React-Timeago to support any feature you may need from a fuzzy time display. The formatter function is expected to return a string. But it can also return any React component (or array of components) that would become the child of React-TimeAgo

I recommend using the fantastic [L10ns](http://l10ns.org) for internationalization needs.

###### component (optional) (default: 'span')
A string of ReactClass that is used to wrap the live updating string

###### minPeriod (optional) (default: 0)
The minimum number of seconds that the component should wait before updating. The component will still update if you pass new props.
Use this if, for example, you don't want to update every second for recent times.

###### maxPeriod (optional) (default: Infinity)
The opposite of minPeriod. Use this to force dates to update more often than the default behaviour.
For example, you can use this update a time every 5 minutes even after it is more than an hour old.

###### Anything Else? (optional)
As of v2.0 you can pass in any props. Any props not used by React-TimeAgo will be passed down to the resulting component.
This means that you can pass className, styles, id, title, aria-label, event handlers or anything else you want.

If you pass in a custom component as the component prop, you can also pass props that you want passed down to your custom component.
In such a case you can think of React-TimeAgo as a Higher-Order-Component.

## Why React-TimeAgo

React-TimeAgo focusses on speed, and simplicity. At about 100 lines of code, the file size is extremely small. There are many similar libraries, but most of them come with large dependencies that usually isn't worth such a simple use-case

Additionally, in the spirit of NPM and keeping libraries small, any additional features you may need from TimeAgo can be plugged-in using the formatter function.

In the future, I will be writing formatter functions for various languages, that can be required and passed-in as needed.
As you will only require the parts you actually use, there will be no need to bloat-up your javascript.

React-TimeAgo is also set apart from its competitors in that it is one of the only time-ago components that updates itself live.

If this is not for you, please looks at the alternatives out there.

## Contribution

While the code is complete and pretty stable, I welcome issues and pull requests.

React-TimeAgo is feature complete from my point of view. (discussions welcome)

For any additional functionality, a formatter function should do the job. I want to build a folder full of pre-built formatter functions. Contributions for languages and other ideas are welcome.

## SemVer

React-TimeAgo follows SemVer strictly.

## Changelog

#### v2.2.0
* FEATURE: New Props: `minPeriod` and `maxPeriod` to customize how often the Component updates.

#### v2.1.1

* BUG-FIX: Fixed an issue, where changing the date wouldn't correctly update the update timer.

#### v2.1.0

* FEATURE: Added PropType validation. It will now print a warning if you fail to pass in a date, instead of failing silently.
* BUG-FIX: Pending Timeouts are cleared when the Component is unmounted
* BUG-FIX: When new Props are passed in, the component will update itself correctly. Now you can flip the live switch on and off.
* FEATURE: The formatter function gets the original date as the fourth argument, for more custom date formats.
