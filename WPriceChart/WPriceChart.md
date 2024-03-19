# Price Chart

## New Widget

```js
var priceChart = window.fdc__widgets__.WPriceChart.init(
  selector,
  initialConfig,
  initialLanguage,
  localeMessages,
  themeName
);

var priceChart = window.fdc__widgets__.WPriceChart.init('.price-chart-widget' /* optional parameters */);
```

- **selector** (_String_|_HTML Element_): Any valid querySelector or actual dom element
- **initialLanguage** (_String_): Language Code
- **initialConfig** (_Object_): All options can be passed here initially
  - **ric** (_String_): Exchange Symbol
  - **showVolume** (_Boolean_): Toggles the volume chart visibility
  - **intradayEnabled** (_Boolean_): Enable or disable intraday timeseries in the chart. Defaults to true
  - **showCompareRics** (_Boolean_): Toggles the comparison feature in the chart. Defaults to true
  - **showDatePicker** (_Boolean_): Toggles the date-picker in the chart. Defaults to true
  - **tradingHours** (_Object_): Trading hours and time zone based on which chart data will be shown
    - **openTime** (_String_): Market opening time
    - **closeTime** (_String_): Market closing time
    - **timeZone** (_String_): Market time zone
- **themeName** (_String_): Theme of the widget in the format _UserName-ThemeName_
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set instrument code

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

```js
priceChart.setRic('BMWG.DE');
```

### `setShowVolume(showVolume)`

Set the default view on init

- **showVolume** (_Boolean_): Toggle the volume chart on or off. Defaults to 'true'.
- **Returns** (_void_): void

```js
priceChart.setShowVolume(false);
```

### `enableIntraday(isIntradayEnabled)`

To enable or disable intraday

- **isIntradayEnabled** (_Boolean_): Toggles the intraday option as enabled or disabled. Defaults to 'true'.
- **Returns** (_void_): void

```js
priceChart.enableIntraday(false);
```

### `showDatePicker(isDatePickerDisplayed)`

To display or hide the date-picker

- **isDatePickerDisplayed** (_Boolean_): Toggle the date-picker on or off. Defaults to 'true'.
- **Returns** (_void_): void

```js
priceChart.showDatePicker(false);
```

### `setTradingHours(tradingHours)`

Set trade start time, end time and time zone based on which the chart data for intraday options will be filtered.
Only base RIC data will be filtered based on `tradingHours`.  
Note: The time zone should used from the IANA time zone database.

- **tradingHours** (_Object_): Trading hours and time zone based on which chart data will be shown
  - **openTime** (_String_): Market opening time
  - **closeTime** (_String_): Market closing time
  - **timeZone** (_String_): Market time zone
- **Returns** (_void_): void

```js
priceChart.setTradingHours({ openTime: '9:00', closeTime: '16:00', timeZone: 'Europe/Berlin' });
```

### `setCustomEventsCallback(callbackFunction)`

Set a callback function `callbackFunction(fromDate, toDate, periodicity, ric)` which is called with

- **fromDate** (_Date_): From date of the chart
- **toDate** (_Date_): To date of the chart
- **periodicity** (_Object_): Contains the periodicity setting
- **ric** (_String_): Reuters Instrument Code (RIC)

during rendering and should return a series of custom events. Please adjust timestamps according to the given periodicity (sample rate) and aggregate multiple events that fall into the same sample interval to a single one, to avoid bandwidth and performance issues as well as excessive overdraw and overflowing tooltip messages.

- **Returns** (Array): Array of custom events. Example:

```js
[{
  timestamp: 1667579100000,
  price: 82.782,
  label: 'custom events',
  colorIndex: 5
}, {}, {}, ..];
```

### `setLocale(locale)`

Set new locale for widget instance using a BCP 47 ISO language tag. (Norwegian is 'nb' or 'nb-NO', english is 'en', 'en-US' or 'en-GB')

- **locale** (_String_): country code
- **Returns** (_void_): void

```js
priceChart.setLocale('nb-NO');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
priceChart.getLocale('no');
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
priceChart.setLocaleMessages('en', {
  formatterLanguage: 'en', // Language used for date, time and number formatting
  messageLanguage: 'en', // Language used for messages
  controls: {
    placeholder: 'Compare with',
    buttons: {
      D: 'D',
      '2D': '2D',
      W: 'W',
      '2W': '2W',
      M: 'M',
      '3M': '3M',
      YTD: 'YTD',
      Y: 'Y',
      '2Y': '2Y',
      '10Y': '10Y',
      Max: 'Max',
    },
  },
  tooltip: {
    Price: 'Price : {VALUE}',
    Volume: 'Volume : {VALUE}',
  },
  labels: {
    shortMonths: {
      January: 'Jan',
      February: 'Feb',
      March: 'Mar',
      April: 'Apr',
      May: 'May',
      June: 'Jun',
      July: 'Jul',
      August: 'Aug',
      September: 'Sep',
      October: 'Oct',
      November: 'Nov',
      December: 'Dec',
    },
    shortDays: {
      Sunday: 'Sun',
      Monday: 'Mon',
      Tuesday: 'Tue',
      Wednesday: 'Wed',
      Thursday: 'Thu',
      Friday: 'Fri',
      Saturday: 'Sat',
    },
    inputLabel: {
      day: 'Day',
      month: 'Month',
      year: 'Year',
    },
    inputPlaceholder: {
      day: 'DD',
      month: 'MM',
      year: 'YYYY',
    },
  },
  messages: {
    nodata: 'No data available.',
    error: 'There was an error. We will try to get the data again in a few moments...',
  },
  numberFormats: {
    compact: [
      '0.00',
      '00',
      '000',
      '0K',
      '00K',
      '000K',
      '0.0M',
      '00M',
      '000M',
      '0.0B',
      '00B',
      '000B',
      '0.0T',
      '00T',
      '000T',
    ],
  },
  dateTimeFormats: {
    time: {
      hour: '2-digit',
      minute: '2-digit',
      second: '2-digit',
      hour12: true,
    },
    date: {
      year: 'numeric',
      month: '2-digit',
      day: '2-digit',
      a11y: {
        month: 'long',
        day: 'numeric',
        year: 'numeric',
      },
    },
  },
  a11y: {
    fromDatePicker: {
      day: 'Day in from date',
      month: 'Month in from date',
      year: 'Year in from date',
    },
    toDatePicker: {
      day: 'Day in to date',
      month: 'Month in to date',
      year: 'Year in to date',
    },
    fromDatePickerLabel: 'Select From Date',
    toDatePickerLabel: 'Select To Date',
    timeRangeButtons: 'This is a group of radio buttons for selecting the time range of the chart',
    compareWithLabel:
      'This is an input box to enter upto four rics that you want to compare with the base ric.{SELECTED_ITEMS}',
    chartContainerLabel: 'This is a chart representing the changes in prices',
    dropDownOptionDeselect: 'Deselect {OPTION}',
    selectedItemsLabel: '{ITEMS} selected. Press left/right arrow keys to deselect an item.',
    baseRicPointDescription: 'Price of base ric is {VALUE}',
    compareRicPointDescription: 'Price of {NAME} is {VALUE}',
    volumePointDescription: 'Volume of base ric is {VALUE}',
  },
});
```

**If the fields formatterLanguage and messageLanguage are not provided, the value of locale is used for those fields**

### Usage of dateTimeFormats option in setLocaleMessages API:

- **time** : Used for formatting time in tooltip and screen reader description of tooltip
- **date** : Used for formatting date in tooltip of chart
- **date.a11y** : Used for screen reader description of date in tooltip of chart

Note: All the list of options that could be given for dateTimeFormats can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat)

### `getSettings()`

Get the current settings of the widget instance.

- **Returns** (_Object_): _widgetSettings_

```js
priceChart.getSettings();
```

### `setSettings(widgetSetting)`

Sets the settings for the widget instance.

- **widgetSetting** (_Object_): _widgetSettings_
- **Returns** (_Object_): _widgetSettingResponse_

```js
const settings = { compareRics: [{ id: 'HDBK.NS', text: 'HDFC BANK' }] };
priceChart.setSettings(settings);
```

### `onSettingsChange(callbackFunc)`

Sets a callback function that gets called whenever a widget setting changes. The function accepts an argument of type _widgetSettings_

- **callbackFunc** (_Object_): Callback function
- **Returns** (_void_): void

```js
priceChart.onSettingsChange((setting) => console.log(setting));
```

#### Widget Settings

The _widgetSettings_ argument passed to `setSettings` API and returned from `getSettings` API has the following properties

- **interval** (_Object_): Contains relative range, date range and intradayEnabled settings
  - **relativeRange** (_String_): The relative date range of chart. Supported values are 1D, 2D, 1W, 2W, 1M, 3M, YTD, 1Y, 2Y, 10Y, 20Y and Other
  - **dateRange** (_Object_): Contains to date and from date settings. **While using `setSettings`, this property will be considered only if relativeRange is not present or its value is Other**
    - **fromDate** (_Date_): From date of the chart
    - **toDate** (_Date_): To date of the chart
  - **intradayEnabled** (_Boolean_): Enable/Disable intraday
- **showVolume** (_Boolean_): Show volume chart for base ric
- **showCompareRics** (_Boolean_): Enable users to add/remove compare rics
- **showDatePicker** (_Boolean_): Show the date picker.
- **compareRics** (_Array_): Array of rics to compare with base ric.
  - **id** (String): Reuters Instrument Code (RIC)
  - **text** (String): Name of the benchmark

If a setting is not given during `setSettings` API call, the setting currently present in the widget will be retained. So while constructing the _widgetSetting_ argument, make sure the properties doesn't conflict with the existing ones.
For example, if the _widgetSetting_ property has only the compareRics setting and the widget currently has showCompareRics set to false, then the API will return an error since compare rics can be added only when showCompareRics is true.

For mandatory settings, the `setSettings` API will always return an error if the setting value is invalid. No other settings given as part of that call will be set for the widget in that case.

For non mandatory settings, the `setSettings` API will neglect it if the value given is invalid. The remaining valid settings will be set for the widget.

**Mandatory settings for Price Chart: interval**

#### Widget Setting Response

The `setSettings` returns an object _widgetSettingResponse_ with the following properties

- **status** (_String_): status of API call. Possible values are OK (all settings were applied), ERROR (a fatal error occured and no settings were applied), and PARTIAL (only the valid settings were applied).
- **error** (_Array_): Array of error messsages when status is either ERROR or PARTIAL
  - **code** (_Number_): Error code
  - **message** (_String_): Error message
  - **key** (_String_): Property that caused the error. (This is only present when the property that caused the error cannot be identified by error code)

#### Error Codes

| Error code | Message                                                                                               | Description                                                   |
| ---------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| 1000       | Cannot call API to get config while widget is initializing                                            | API was called before widget was initialized                  |
| 1001       | 'SETTING' is not valid for this widget                                                                | An unsupported setting was given                              |
| 1002       | Invalid value for setting 'SETTING', Invalid value for setting 'SETTING'. Possible values are 'VALUE' | An invalid value was given for a setting                      |
| 1003       | One of the 'SETTING' is of invalid format                                                             | A sub item has an invalid field value (Ex: id in compareRics) |
| 1004       | 'SETTING' should be of type boolean                                                                   | A non boolean value was given for a boolean setting           |
| 1005       | 'SETTING' should be an instance of Date                                                               | A non date value was given for a date setting                 |
| 1006       | 'SETTING' should be of type Array                                                                     | A non Array value was given for a Array setting               |
| 1018       | 'compareRics' should be empty when 'showCompareRics' is false                                         | Compare rics where added when showCompareRics was false       |
| 1020       | 'interval.relativeRange' should be one of {VALUES} when 'interval.intradayEnabled' is false           | An intraday range was given intradayEnabled was false         |

### `destroy()`

Destroy widget instance and remove it from DOM

- **Returns** (_void_): void

```js
priceChart.destroy();
```

## CSS

Most common classes to overwrite/customize

```css
.price-chart-widget .w-price-chart-widget {
  height: 450px; // set height for the chart section
}

.price-chart-widget .w-price-chart-widget .highcharts-tooltip-box {
  //
}

.price-chart-widget .v-widget-control-bar {
  //
}

.price-chart-widget .v-widget-control-bar .v-widget-input-radio {
  //
}

.price-chart-widget .v-widget-control-bar .v-widget-input-date-range {
  //
}

.price-chart-widget .v-widget-control-bar .v-widget-input-tag {
  //
}
```
