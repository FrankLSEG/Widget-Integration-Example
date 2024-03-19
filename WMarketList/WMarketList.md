# Market List

## New Widget

```js
var marketList = window.fdc__widgets__.WMarketList.init(
  selector,
  initialConfig,
  initialLanguage,
  localMessages,
  themeName
);

// Example: Initialize widget with default settings
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget');

// Example: Initialize widget based on a specific index
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX' //when empty string is passed, it  will display the grid with no instruments in it
});

// Example: Hide filter menu
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  suppressMenu: true
});

// Example: Initialize widget based on a chain ric
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  chainRic: '0#GFB.OL' //when empty string is passed, it  will display the grid with no instruments in it
});

// Example: Initialize widget based on a custom (watch)list)
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  rics: ['AKER.OL', 'BAKKA.OL', 'DNB.OL', 'ELK.OL', 'GJFS.OL', 'LSG.OL', 'NEL.OL', 'NWC.OL'] //when empty list is passed, it  will display the grid with no instruments in it
});

// Example: Initialize widget with new columns (including a custom button column)
// Note: This example uses simple 'hardcoded' strings as headerNames.
// However we recommend to use localized headerNames as shown in the example below this one.
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'Ticker',
      field: 'x._TICKER'
    },
    {
      headerName: 'Name',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    },
    {
      headerName: '',
      field: 'q.RIC',
      type: 'button',
      buttons: [
        {
          id: 'btn_01',
          label: 'Buy',
          style: 'width: 40px; height: 20px; background-color: #e0e0ff; margin: 0 1px;'
        },
        {
          id: 'btn_02',
          label: 'Sell',
          style: 'width: 40px; height: 20px; background-color: #ffe0e0; margin: 0 1px;'
        },
        {
          id: 'btn_03',
          style:
            'width: 20px; height: 20px; background-image: url("http://www.financial.com/tmp/dnb_testicon.png"); background-size: 20px 20px; border: none; margin: 0 1px;'
        }
      ],
      width: 106
    },
    {
      headerName: 'Price',
      field: 'q._TRDPRC_1',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: '+/-',
      field: 'q._NETCHNG_1'
    },
    {
      headerName: '%',
      field: 'q._PCTCHNG'
    },
    {
      headerName: 'Bid',
      field: 'q._BID',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'Bid Sz.',
      field: 'q.BIDSIZE'
    },
    {
      headerName: 'Ask',
      field: 'q._ASK',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'Ask Sz',
      field: 'q.ASKSIZE'
    }
  ]
});

// Example: Initialize widget with new columns
// Note: In this example all headerNames point to the default localization strings (en).
// You can also provide your own localisation strings for other languages (see example below this one)
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'i18n(header.ticker)',
      field: 'x._TICKER'
    },
    {
      headerName: 'i18n(header.name)',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    },
    {
      headerName: 'i18n(header.price)',
      field: 'q._TRDPRC_1',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'i18n(header.change)',
      field: 'q._NETCHNG_1'
    },
    {
      headerName: 'i18n(header.changePercentage)',
      field: 'q._PCTCHNG'
    },
    {
      headerName: 'i18n(header.bid)',
      field: 'q._BID',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'i18n(header.ask)',
      field: 'q._ASK',
      cellStyle: { 'background-color': '#f7f2f4' }
    }
  ]
});

// Example: Filter menu disabaled for all the columns which is overriden by a particular column
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  suppressMenu: true
  columns: [
    {
      headerName: 'Ticker',
      field: 'x._TICKER',
      suppressMenu: false
    },
    {
      headerName: 'Name',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    }
  ]
});

// Example: Initialize widget with columns that could be shown or hidden using the 'hide' property
// (default value is false)
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'Ticker',
      field: 'x._TICKER',
      hide: true
    },
    {
      headerName: 'Name',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    },
    {
      headerName: 'i18n(header.price)',
      field: 'q._TRDPRC_1',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'i18n(header.change)',
      field: 'q._NETCHNG_1'
    },
    {
      headerName: 'i18n(header.changePercentage)',
      field: 'q._PCTCHNG'
    },
    {
      headerName: 'i18n(header.bid)',
      field: 'q._BID',
      cellStyle: { 'background-color': '#f7f2f4' },
      hide: true
    },
    {
      headerName: 'i18n(header.ask)',
      field: 'q._ASK',
      cellStyle: { 'background-color': '#f7f2f4' },
      hide: true
    }
  ]
});

// Example: Adding custom column with value formatted using client defined renderer funtion
// For custom columns it is mandatory to keep the 'type' value as 'custom' and the function name as 'renderFunction'
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'Ticker',
      field: 'x._TICKER',
    },
    {
      headerName: 'Name',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    },
    {
      headerName: 'Custom Formatter',
      field: 'q.RIC',
      type: 'custom',
      renderFunction: function (fieldValue, rowData, rowIndex) {
        var eDiv = document.createElement('div');
        eDiv.innerHTML = '<span class="my-css-class">[' + fieldValue + ']</span>';
        eDiv.style.overflow = 'hidden';
        eDiv.style['text-overflow'] = 'ellipsis';
        return eDiv;
      },
      headerClass: 'text-start',
      cellClass: 'text-start',
      minWidth: 130,
    }
  ]
});

// Example: Using custom column to attain stacked content with buttons in a single row
// For custom columns it is mandatory to keep the 'type' value as 'custom' and the function name as 'renderFunction'
// The button click will provide the necessary info using the example callback function used for specific click events in onClick API
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'Ticker',
      field: 'x._TICKER',
    },
    {
      headerName: 'Name',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    },
    {
      headerName: 'Custom Formatter',
      field: 'q.RIC',
      type: 'custom',
      wrapText: true,
      renderFunction: function (fieldValue, rowData, rowIndex) {
        var eDiv = document.createElement('div');
        eDiv.innerHTML = `<span style="display:inline-block" class="my-css-class">[${fieldValue}]</span>
                          <span style="display:inline-block">
                            <button class="buy-button">Buy</button>
                            <button class="sell-button">Sell</button>
                          </span>`;
        return eDiv;
      },
      headerClass: 'text-start',
      cellClass: 'text-start',
      minWidth: 130,
    }
  ]
});
// onClick method for identifiying selected button while having stacked buttons.
// The button can be identified using the 'class' property in the 'button' attribute which is available in the event payload
marketList.onClick(function callBack(event) {
  if (event.button) {
    console.log('[API] onClick event for ric:', event.ric, 'from button:', event.button.class);
  }
  else{
    console.log('[API] onClick event for ric:', event.ric, 'from cell:', event.gridContext.colDef.field);
  }
});

// Example: Sortable streaming FIDs
// Streaming Fids columns are not sortable by default.
// To add sorting for streaming fids, set `sortable: true` in column configuration and set a flag 'canSortStreamData' to true
// Please note that the sort feature on streaming fids will get disabled automatically if total no. of rows is greater than 200.
// Sorting is enabled by default on x._TICKER and x._DSPLY_NAME regardless of list length, don't use `sortable: true` on them
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'i18n(header.ticker)',
      field: 'x._TICKER'
    },
    {
      headerName: 'i18n(header.name)',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    },
    {
      headerName: 'i18n(header.price)',
      field: 'q._TRDPRC_1',
      cellStyle: { 'background-color': '#f7f2f4' }
      sortable: true
    },
    {
      headerName: 'i18n(header.change)',
      field: 'q._NETCHNG_1',
      sortable: true
    },
    {
      headerName: 'i18n(header.changePercentage)',
      field: 'q._PCTCHNG',
      sortable: true
    }],
  canSortStreamData: true,
});

// Example: Set sorting order for a column using 'sort' property
// Valid values are 'null', 'asc' and 'desc'
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'Ticker',
      field: 'x._TICKER',
      sort: 'desc'
    },
    {
      headerName: 'Name',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    }
  ]
});

// Example: Setting pinned column
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  suppressMenu: true
  columns: [
    {
      headerName: 'Ticker',
      field: 'x._TICKER',
      pinned: true
    },
    {
      headerName: 'Name',
      field: 'x._DSPLY_NAME',
      minWidth: 130
    }
  ]
});
// Example: Initialize widget providing a new language code and the corresponding translation values
// Note: In a real world example all the value strings would be real translations.
// However in this example we just prefixed the default values with "no" to symbolize a "new language".
// This example uses all available translation keys for reference

var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', { indexRic: '.OSEBX' }, 'no', {
  formatterLanguage: 'en', // Language used for date, time and number formatting
  messageLanguage: 'en', // Language used for messages
  header: {
    ticker: 'noTicker',
    name: 'noName',
    price: 'noPrice',
    change: 'no+/-',
    changePercentage: 'no%',
    bid: 'noBid',
    ask: 'noAsk',
    histClose: 'noHist.Close',
    time: 'noTime',
    date: 'noDate',
    exchange: 'noExchange',
    currency: 'noCurrency',
    country: 'noCountry'
  },
  grid: {
    loadingOoo: 'noLoading...',
    noRowsToShow: 'noNo Rows To Show',
    filterOoo: 'noFilter...',
    applyFilter: 'noApply Filter...',
    clearFilter: 'noClear Filter...',
    equals: 'noEquals',
    notEqual: 'noNot equal',
    lessThan: 'noLess than',
    greaterThan: 'noGreater than',
    lessThanOrEqual: 'noLess than or equal',
    greaterThanOrEqual: 'noGreater than or equal',
    inRange: 'noIn range',
    contains: 'noContains',
    notContains: 'noNot contains',
    startsWith: 'noStarts with',
    endsWith: 'noEnds with',
    andCondition: 'noAND',
    orCondition: 'noOR',
  },
  messages: {
    nodata: 'No data available.',
    norics: 'No data available for the given instrument(s).',
    error: 'There was an error. We will try to get the data again in a few moments...',
  },
  a11y: {
    caption: "Market List widget",
    selectCellButton: "Press enter to select the button"
  },
  numberFormats: {
    compact: ['', '', '', '0.0K', '00K', '000K', '0.0M', '00M', '000M', '0.0B', '00B', '000B', '0.0T', '00T', '000T'],
  },
  dateTimeFormats: {
    time: {
      hm: {
        hour: '2-digit',
        minute: '2-digit',
        hour12: true,
      },
      hms: {
        hour: '2-digit',
        minute: '2-digit',
        second: '2-digit',
        hour12: true,
      },
    },
    date: {
      year: '2-digit',
      month: '2-digit',
      day: '2-digit',
    },
  },
});
```

- **selector** (_String_|_HTML Element_): Any valid querySelector or actual dom element
- **initialState** (_Object_):
  - **indexRic** (_String_): Reuters Instrument Code (RIC) for a index (e.g. ".OSEBX").
  - **chainRic** (_String_): Chain RIC (e.g. "0#ETN.OL").
  - **rics** (_Array[String]_): Array of Reuters Instrument Codes (RICs). Note: You can only set either indexRic _or_ chainRic _or_ rics. If more than one are provided then rics will supercede chainRic which will supercede indexRic.
  - **suppressMenu** (_Boolean_): Used to specify if the filter menu is to be shown or not
  - **isStreaming** (_Boolean_): Should the widget stream live updates
  - **canSortStreamData** (_Boolean_): Used to enable sorting for streaming fids
  - **columns** (_Array&lt;Object&gt;_): Array of column objects
    - **headerName** (_String_): Column header name as simple string (e.g. "Ticker") or translation key string (e.g. "i18n(header.ticker)").
    - **field** (_String_): Field id (fid) (e.g. "q.\_NETCHNG_1")
    - **renderer** (_String_): The name of a custom cell renderer (e.g. "compactDateTime"). The **field** id should not be used with renderer since they are mutually exclusive.
    - **rendererParams** (_Object_): You can specify additional key/value pairs based on the **renderer**.
    - **type** (_String_): The type is set dynamically and can be overwritten. This is usually only the case if you want to configure a column with custom buttons or custom user defined renderers. In this case use type: 'button' or 'custom' respectively.
    - **buttons** (_Array&lt;Object&gt;_): Array of button objects. Only available if column type is set 'button'.
      - **label** (_String_): The label of the button
      - **class** (_String_): Custom CSS class to add to the button element
      - **style** (_String_): Custom styles for the button
      - **(any)** (_String_): You can define additional key/value pairs. You will get this key/value pairs back as payload of the clickEvent. In our examples we use 'id' to identify the button if clicked.
    - **headerClass** (_String_ | _Array&lt;String&gt;_): Custom CSS class to add to the header cells.
    - **cellClass** (_String_ | _Array&lt;String&gt;_): Custom CSS class to add to the cells.
    - **cellStyle** (_String_): Custom styles for the cells.
    - **width** (_Float_): Initial width for the cell
    - **minWidth** (_Float_): Initial minWidth for the cell.
    - **maxWidth** (_Float_): Initial maxWidth for the cell.
    - **renderFunction** (_Function_): User defined function for rendering custom columns. The **type** value should be set to 'custom' in order to use this feature.
    - **pinned** (_Boolean_): Pin a column to one side: start or end. A value of true is converted to 'start'.
    - **hide** (_Boolean_) : To show or hide the column (default value is `false`)
    - **sort** (_String_) : Sorts the contents of the column in a particular order ( Valid values are `null`, `asc`, `desc`)
  - **country** (_String_): Country (registered for sale) used to disambiguate fund data. Defaults to US.
  - **currency** (_String_): Currency code used to disambiguate fund data. Defaults to USD.
  - **tableRowHeight** (_Number_): Height of the grid row(If given as `-1`, row height will be set dynamically based on the cell content).
  - **classSchemeID** (_String_): Lipper class scheme ID used to disambiguate fund data. Defaults to 1006052 (i.e. Lipper Global)
- **initialLanguage** (_String_): Language Code
- **localMessages** (_Object_): Translation strings for the language code
- **themeName** (_String_): Theme of the widget in the format _UserName-ThemeName_
- **Returns** (_Object_): new widget instance

## API

### `setIndexRic(ric)`

Set index during runtime.

```js
// Example: Set index after initialisation
marketList.setIndexRic('.GDAXI');
```

- **ric** (_String_): Reuters Instrument Code (RIC) - (Empty string passed as an argument will clear the grid, if indexRic was already set before)
- **Returns** (_void_): void

### `setRics(rics)`

Set a multiple rics (watchlist rows) after initialisation

```js
// Example: Set a watchlist after initialisation
marketList.setRics(['AKER.OL', 'BAKKA.OL', 'DNB.OL', 'ELK.OL', 'GJFS.OL', 'LSG.OL', 'NEL.OL', 'NWC.OL']);
```

- **rics** (_Array&lt;String&gt;_): Array of Reuters Instrument Codes (RICs). Empty list passed as an argument will clear the grid if rics was already set before.
- **Returns** (_void_): void

### `setChainRic(ric)`

Set a chain ric after initialisation

```js
// Example: Set a chain ric after initialisation
marketList.setChainRic('0#ETN.OL');
```

- **ric** (_String_): chain ric (Empty string passed as an argument will clear the grid, if chainRic was already set before)
- **Returns** (_void_): void

### `setTableRowHeight(tableRowHeight)`

Set Data Grid Row Height during runtime.

```js
// Example: Set Row Height after initialisation
marketList.setTableRowHeight(24);
```

- **tableRowHeight** (_Number_): AG Grid Row Height(If given as `-1`, row height will be set dynamically based on the cell content).
- **Returns** (_void_): void

### `setColumns(columns)`

Set new columns after initialisation

```js
// Example: Set a watchlist after initialisation
marketList.setColumns([
  {
    headerName: 'Ticker',
    field: 'x._TICKER',
    headerClass: 'text-center',
    cellClass: ['custom-class', 'text-center'],
  },
  {
    headerName: 'Name',
    field: 'x._DSPLY_NAME',
    minWidth: 130,
  },
  {
    headerName: 'Price',
    field: 'q._TRDPRC_1',
    cellStyle: { 'background-color': '#f7f2f4' },
  },
  {
    headerName: '+/-',
    field: 'q._NETCHNG_1',
  },
  {
    headerName: '%',
    field: 'q._PCTCHNG',
  },
  {
    headerName: 'Bid',
    field: 'q._BID',
    cellStyle: { 'background-color': '#f7f2f4' },
  },
  {
    headerName: 'Bid Sz.',
    field: 'q.BIDSIZE',
  },
  {
    headerName: 'Ask',
    field: 'q._ASK',
    cellStyle: { 'background-color': '#f7f2f4' },
  },
  {
    headerName: 'Ask Sz',
    field: 'q.ASKSIZE',
  },
]);
```

- **columns** (_Array&lt;Object&gt;_): Array of column objects
  - **headerName** (_String_): Column header name as simple string (e.g. "Ticker") or translation key string (e.g. "i18n(header.ticker)").
  - **field** (_String_): Field id (fid) (e.g. "q.\_NETCHNG_1")
  - **renderer** (_String_): The name of a custom cell renderer (e.g. "compactDateTime"). The **field** id should not be used with renderer since they are mutually exclusive.
  - **rendererParams** (_Object_): You can specify additional key/value pairs based on the **renderer**.
  - **type** (_String_): The type is set dynamically and can be overwritten. This is usually only the case if you want to configure a culumn with custon buttons. In this case use type: 'button".
  - **buttons** (_Array&lt;Object&gt;_): Array of button objects. Only available if column type is set 'button'.
  - **label** (_String_): The label of the button
  - **class** (_String_): Custom CSS class to add to the button element
  - **style** (_String_): Custom styles for the button
  - **(any)** (_String_): You can define additional key/value pairs. You will get this key/value pairs back as payload of the clickEvent. In our examples we use 'id' to identify the button if clicked.
  - **headerClass** (_String_ | _Array&lt;String&gt;_): Custom CSS class to add to the header cells.
  - **cellClass** (_String_ | _Array&lt;String&gt;_): Custom CSS class to add to the cells.
  - **cellStyle** (_String_): Custom styles for the cells.
  - **width** (_Float_): Initial width for the cell
  - **minWidth** (_Float_): Initial minWidth for the cell
  - **maxWidth** (_Float_): Initial maxWidth for the cell
  - **pinned** (_Boolean_): Pin a column to one side: start or end. A value of true is converted to 'start'.
  - **sort** (_String_) : Sorts the contents of the column in a particular order ( Valid values are `null`, `asc`, `desc`)
- **Returns** (_void_): void

### `onClick(function(event))`

Registers callback function to listen for click events

```js
// Example: Get all clicks within the grid (cellClicks, buttonClicks ...)
marketList.onClick(function callBack(event) {
  console.log('[API] onClick event from marketList. RIC: ', event.ric);
});

// Example: Handle specific clicks
marketList.onClick(function callBack(event) {
  if (event.button) {
    console.log('[API] onClick event for ric:', event.ric, 'from button:', event.button);
  } else {
    console.log(
      '[API] onClick event for ric:',
      event.ric,
      'from cell:',
      event.gridContext.colDef.field,
      'value:',
      event.gridContext.value
    );
  }
});
```

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **ric** (_String_): Related Reuters Instrument Code (e.g. 'AAPL.OQ')
  - **origin** (_Object_): Original MouseEvent
  - **button** (_Object_): Contains the users original button configuration object for this specific button. Only available if the click source was a user configured button (i.e. configured buttons in your column configuration)
  - **gridContext** (_Object_): Contains extensive information about the grid context if the click originated from within the grid. Includes info about the clicked grid-cell, value of the cell, data of the row and many more (see example).
- **Returns** (_void_): void

### `toggleStreaming()`

Enable/disable streaming updates for the widget

- **Returns** (_void_): void

```js
marketList.toggleStreaming();
```

### `isWidgetStreaming()`

Returns true if streaming is currently enabled for the widget

- **Returns** (_Boolean_)

```js
marketList.isWidgetStreaming();
```

### `setLocale(locale)`

Set new locale for widget instance using a BCP 47 ISO language tag. (Norwegian is 'nb' or 'nb-NO', english is 'en', 'en-US' or 'en-GB')

- **locale** (_String_): country code
- **Returns** (_void_): void

```js
marketList.setLocale('nb-NO');
```

### `getLocale()`

Get the current active locale for widget instance.

```js
marketList.getLocale();
```

- **Returns** (_String_): country code

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(language, messages)`

Add new translations to existing language or add new language and translations.
Translation could be done for fid values which are specified in the _fieldValueTranslations_ as given below. These translation could be done only for fids having datatype of string. The _default_ value which is optional will be chosen if no keys match with the provided value for the fid. If the _default_ value is not specified and the value do not match with any of the keys in the particular fid, then the value will be displayed as it is with no change.

```js
marketList.setLocaleMessages('no', {
  formatterLanguage: 'en', // Language used for date, time and number formatting
  messageLanguage: 'en', // Language used for messages
  header: {
    ticker: 'noTicker',
    name: 'noName',
    price: 'noPrice',
    change: 'no+/-',
    changePercentage: 'no%',
    bid: 'noBid',
    ask: 'noAsk',
    histClose: 'noHist.Close',
    time: 'noTime',
    date: 'noDate',
    exchange: 'noExchange',
    currency: 'noCurrency',
    country: 'noCountry',
  },
  fieldValueTranslations: {
    'x._CURRENCY': {
      EUR: 'Euro',
      USD: 'US Dollar',
      NOK: 'Norwegian Krona',
      default: '-',
    },
    'x._COUNTRY': {
      NO: 'Norway',
      SE: 'Sweden',
      FR: 'France',
      default: '....',
    },
    'x._SECTOR_REU': {
      1: 'Manufacturing',
      8: 'Financials',
    },
  },
  a11y: {
    caption: 'Market List widget',
    exit: 'Exited Market List Widget',
  },
  grid: {
    loadingOoo: 'noLoading...',
    noRowsToShow: 'noNo Rows To Show',
    filterOoo: 'noFilter...',
    selectAll: 'noSelect All',
    searchOoo: 'noSearch...',
    applyFilter: 'noApply Filter...',
    clearFilter: 'noClear Filter...',
    equals: 'noEquals',
    notEqual: 'noNot equal',
    lessThan: 'noLess than',
    greaterThan: 'noGreater than',
    lessThanOrEqual: 'noLess than or equal',
    greaterThanOrEqual: 'noGreater than or equal',
    inRange: 'noIn range',
    contains: 'noContains',
    notContains: 'noNot contains',
    startsWith: 'noStarts with',
    endsWith: 'noEnds with',
    andCondition: 'noAND',
    orCondition: 'noOR',
  },
  numberFormats: {
    compact: ['', '', '', '0.0K', '00K', '000K', '0.0M', '00M', '000M', '0.0B', '00B', '000B', '0.0T', '00T', '000T'],
  },
  dateTimeFormats: {
    time: {
      hour: '2-digit',
      minute: '2-digit',
      second: '2-digit',
      hour12: true,
      hm: {
        hour: '2-digit',
        minute: '2-digit',
        hour12: true,
      },
      hms: {
        hour: '2-digit',
        minute: '2-digit',
        second: '2-digit',
        hour12: true,
      },
    },
    date: {
      year: 'numeric',
      month: '2-digit',
      day: '2-digit',
    },
  },
  booleanFormats: {
    bool: {
      true: 'Yes',
      false: 'No',
      null: '-',
    },
  },
});
```

- **language** (_String_): Language code
- **messages** (_Object_): Translation strings for the language code
- **Returns** (_void_): void

**If the fields formatterLanguage and messageLanguage are not provided, the value of locale is used for those fields**

### Usage of dateTimeFormats option in setLocaleMessages API:

- **time** : Used for formatting time in datetime fids
- **time.hm** : Used for formatting time in HH:MM format when data has no seconds precision in time fids
- **time.hms** : Used for formatting time in HH:MM:SS format when data has seconds precision in time fids
- **date** : Used for formatting the date in datetime and date fids

Note: All the list of options that could be given for dateTimeFormats can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat)

### `setStreamColumnSortable(flag)`

This will enable sorting for streaming FID columns with the `sortable` property set to `true`. <br />
**Note** - _**The sorting functionality for streaming FIDs will automatically get disabled if the table rows count is greater than 200.**_

- **flag** (_Boolean_): true/false to enable/disable sorting for streaming FIDs
- **Returns** (_void_): void

### `refreshRowData(index)`

Refresh grid row data by passing row index.

- **index** (_Number_): grid row index

- **Returns** (_void_): void

```js
marketList.refreshRowData(2);
```

### `destroy()`

Destroys widget instance, removes it from DOM and returns a Promise with value as _true_ when the widget has been completely destroyed

- **Returns** (_object_): Promise

```js
marketList.destroy();
```

## Cell Renderers

List of custom cell renderers:

- **countryFlag** : Show country flag image
  - **rendererParams**
    - **width** : Width of the flag image in pixels.
- **compactDateTime** : Show trade date when time is empty, or when date is not current date (holidays/weekends)
- **bidOrIndAuc** : Show indicative auction price during premarket auction phase, and the bid when there is normal trading
- **askOrIndAuc** : Show indicative auction price during premarket auction phase, and the ask when there is normal trading

Note: **field** id should not be used with renderer in the same column since they are mutually exclusive.

```js
// Example: Set new columns with a custom cell renderer after initialization
marketList.setColumns([
  {
    headerName: 'Name',
    field: 'x._DSPLY_NAME',
  },
  {
    headerName: 'Price',
    field: 'q._TRDPRC_1',
  },
  {
    headerName: 'Country',
    renderer: 'countryFlag',
    rendererParams: {
      width: '22px',
    },
  },
]);
```

## CSS

Most common classes to overwrite/customize

Note: Several grid styles/classes can be set via configuration options.

```css
.market-list-widget .widget-body.w-market-list-widget {
  height: 500px;
}
.market-list-widget .ag-theme-balham .ag-root-wrapper {
  //
}
.market-list-widget .ag-theme-balham .ag-header {
  //
}
.market-list-widget .ag-theme-balham .ag-header .ag-header-row {
  //
}
.market-list-widget .ag-theme-balham .ag-header .ag-header-cell {
  //
}
.market-list-widget .ag-theme-balham .ag-row {
  //
}
.market-list-widget .ag-theme-balham .ag-row .ag-cell {
  //
}
```

For overriding existing styles in the theme which have higher priority, `'!important'` property should be added as shown in the example below

```css
.market-list-widget .ag-theme-balham .ag-header {
  background-color: red !important;
}
```

For aligning text within cells, use the classes: `'text-start'`, `'text-center'`, `'text-end'` and `'direction-ltr'`.
These classes can be used in the column configuration as shown below

```js
var marketList = window.fdc__widgets__.WMarketList.init('.market-list-widget', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'Bid',
      field: 'q._BID',
      headerClass: 'text-center',
      cellClass: ['custom-class', 'text-center'],
    },
  ],
});
```

### `Grid Size`

- When the size of the widget is less than the size of the container, we set the autoHeight property of ag grid.
- If using % for your height, then make sure the container you are putting the grid into also has height specified, as the browser will fit the div according to a percentage of the parents height, and if the parent has no height, then this % will always be zero.
- If your grid is not the size you think it should be then put a border on the grid's div and see if that's the size you want (the grid will fill this div). If it is not the size you want, then you have a CSS layout issue in your application.
