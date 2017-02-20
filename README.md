[![view on npm](http://img.shields.io/npm/v/xlsx-populate.svg)](https://www.npmjs.org/package/xlsx-populate)
[![npm module downloads per month](http://img.shields.io/npm/dm/xlsx-populate.svg)](https://www.npmjs.org/package/xlsx-populate)
[![Build Status](https://travis-ci.org/dtjohnson/xlsx-populate.svg?branch=master)](https://travis-ci.org/dtjohnson/xlsx-populate)
[![Dependency Status](https://david-dm.org/dtjohnson/xlsx-populate.svg)](https://david-dm.org/dtjohnson/xlsx-populate)

# xlsx-populate
TODO

## Table of Contents
- [Setup Development Environment](#setup-development-environment)
  * [Install node and gulp globally](#install-node-and-gulp-globally)
  * [Git clone the project](#git-clone-the-project)
  * [Install xlsx-populate libraries](#install-xlsx-populate-libraries)
  * [Gulp tasks](#gulp-tasks)
- [Styles](#styles)
- [API Reference](#api-reference)

## Setup Development Environment

To contribute, ensure that npm (node package manager) and git are installed. Then continue with the following instructions.

### Install node and gulp globally
```bash
npm install --global node gulp
```

### Git clone the project
```bash
git clone git@github.com:dtjohnson/xlsx-populate.git
cd xlsx-populate
```

### Install xlsx-populate libraries
```bash
npm install
npm install --only=dev # Install dev tools
alias node="node --harmony"  # Run node in ES6 mode
```

### Gulp tasks

* __browserify__ - build client-side javascript project bundle
* __lint__ - check project source code style
* __unit__ - unit test project
* __blank__ - build blank xlsx files for default load
* __docs__ - build docs: generate README.md from docs/template.md and source code
* __test__ - run lint and unit test project
* __watch__ - listen for new project changes and then run associated gulp task
* __default__ - run all gulp tasks

Please review [gulp documentation](https://github.com/gulpjs/gulp) to learn more. Here are a few examples:

```
gulp lint  # checks code style
gulp browserify  # outputs browser/xlsx-populate.js for web applications
```

## Styles

* bold: Boolean
* italic: Boolean
* underline: Boolean or 'double'
* strikethough: Boolean
* subscript: Boolean
* superscript: Boolean
* fontSize: Number > 0
* fontFamily: String
* fontColor: hex String or theme Number
* fontTint: Number [-1, 1] The tint value is stored as a double from -1.0 .. 1.0, where -1.0 means 100% darken and 1.0 means 100% lighten. Also, 0.0 means no change.
* horizontalAlignment: left, center, right, fill, justify, centerContinuous, distributed
* justifyLastLine: Boolean (akak 'Justified Distributed'. Only applies when horizontalAlignment === 'distributed') A boolean value indicating if the cells justified or distributed alignment should be used on the last line of text. (This is typical for East Asian alignments but not typical in other contexts.)
* indent: Number > 0
* verticalAlignment: top, center, bottom, justify, distributed
* wrapText: Boolean
* shrinkToFit: Boolean
* textDirection: 'left-to-right', 'right-to-left'
* textRotation: Number [-90, 90] counter clockwise rotation (negatives are clockwise)
* angleTextCounterclockwise: Boolean. textRotation = 45
* angleTextClockwise: Boolean. textRotation = -45
* rotateTextUp: Boolean. textRotation = 90
* rotateTextDown: Boolean. textRotation = -90
* verticalText: Boolean. Special rotation that shows text vertical but individual letters are oriented normally 
* fill pattern: gray125, darkGray, mediumGray, lightGray, gray0625, darkHorizontal, darkVertical, darkDown, darkUp, darkGrid, darkTrellis, lightHorizontal, lightVertical, lightDown, lightUp, lightGrid, lightTrellis
* path gradient: A box is drawn between top, left, right, and bottom. That is used to draw gradient
* borderStyle: hair, dotted, dashDotDot, dashed, mediumDashDotDot, thin, slantDashDot, mediumDashDot, mediumDashed, medium, thick, double

```js
cell.style("border", true);
cell.style("border", "thin");
cell.style("borderStyle", "thin");
cell.style("borderColor", "ff0000");
cell.style("borderTop", true);
cell.style("borderLeft", "dotted");
cell.style("borderBottom", { style: "dashed", color: 5 });
cell.style("border", {
    top: true,
    left: "medium",
    diagonal: {
        style: "hair",
        direction: "both"
    }
});
```

## API Reference
### Classes

<dl>
<dt><a href="#Cell">Cell</a></dt>
<dd><p>A cell</p>
</dd>
<dt><a href="#Column">Column</a></dt>
<dd><p>A column.</p>
</dd>
<dt><a href="#Range">Range</a></dt>
<dd><p>A range of cells.</p>
</dd>
<dt><a href="#Row">Row</a></dt>
<dd><p>A row.</p>
</dd>
<dt><a href="#Sheet">Sheet</a></dt>
<dd><p>A worksheet.</p>
</dd>
<dt><a href="#Workbook">Workbook</a></dt>
<dd><p>A workbook.</p>
</dd>
</dl>

<a name="Cell"></a>

### Cell
A cell

**Kind**: global class  

* [Cell](#Cell)
    * _instance_
        * [.address([opts])](#Cell+address) ⇒ <code>string</code>
        * [.column()](#Cell+column) ⇒ <code>[Column](#Column)</code>
        * [.clear()](#Cell+clear) ⇒ <code>[Cell](#Cell)</code>
        * [.columnName()](#Cell+columnName) ⇒ <code>number</code>
        * [.columnNumber()](#Cell+columnNumber) ⇒ <code>number</code>
        * [.find(pattern, [replacement])](#Cell+find) ⇒ <code>boolean</code>
        * [.formula()](#Cell+formula) ⇒ <code>string</code>
        * [.formula(formula)](#Cell+formula) ⇒ <code>[Cell](#Cell)</code>
        * [.tap(callback)](#Cell+tap) ⇒ <code>[Cell](#Cell)</code>
        * [.thru(callback)](#Cell+thru) ⇒ <code>\*</code>
        * [.rangeTo(cell)](#Cell+rangeTo) ⇒ <code>[Range](#Range)</code>
        * [.relativeCell(rowOffset, columnOffset)](#Cell+relativeCell) ⇒ <code>[Cell](#Cell)</code>
        * [.row()](#Cell+row) ⇒ <code>[Row](#Row)</code>
        * [.rowNumber()](#Cell+rowNumber) ⇒ <code>number</code>
        * [.sheet()](#Cell+sheet) ⇒ <code>[Sheet](#Sheet)</code>
        * [.style(name)](#Cell+style) ⇒ <code>\*</code>
        * [.style(names)](#Cell+style) ⇒ <code>object.&lt;string, \*&gt;</code>
        * [.style(name, value)](#Cell+style) ⇒ <code>[Cell](#Cell)</code>
        * [.style(styles)](#Cell+style) ⇒ <code>[Cell](#Cell)</code>
        * [.value()](#Cell+value) ⇒ <code>string</code> &#124; <code>boolean</code> &#124; <code>number</code> &#124; <code>Date</code> &#124; <code>undefined</code>
        * [.value(value)](#Cell+value) ⇒ <code>[Cell](#Cell)</code>
        * [.workbook()](#Cell+workbook) ⇒ <code>[Workbook](#Workbook)</code>
    * _inner_
        * [~tapCallback](#Cell..tapCallback) ⇒ <code>undefined</code>
        * [~thruCallback](#Cell..thruCallback) ⇒ <code>\*</code>

<a name="Cell+address"></a>

#### cell.address([opts]) ⇒ <code>string</code>
Get the address of the column.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>string</code> - The address  

| Param | Type | Description |
| --- | --- | --- |
| [opts] | <code>Object</code> | Options |
| [opts.includeSheetName] | <code>boolean</code> | Include the sheet name in the address. |
| [opts.rowAnchored] | <code>boolean</code> | Anchor the row. |
| [opts.columnAnchored] | <code>boolean</code> | Anchor the column. |

<a name="Cell+column"></a>

#### cell.column() ⇒ <code>[Column](#Column)</code>
Gets the parent column of the cell.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Column](#Column)</code> - The parent column.  
<a name="Cell+clear"></a>

#### cell.clear() ⇒ <code>[Cell](#Cell)</code>
Clears the contents from the cell.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  
<a name="Cell+columnName"></a>

#### cell.columnName() ⇒ <code>number</code>
Gets the column name of the cell.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>number</code> - The column name.  
<a name="Cell+columnNumber"></a>

#### cell.columnNumber() ⇒ <code>number</code>
Gets the column number of the cell (1-based).

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>number</code> - The column number.  
<a name="Cell+find"></a>

#### cell.find(pattern, [replacement]) ⇒ <code>boolean</code>
Find the given pattern in the cell and optionally replace it.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>boolean</code> - A flag indicating if the pattern was found.  

| Param | Type | Description |
| --- | --- | --- |
| pattern | <code>string</code> &#124; <code>RegExp</code> | The pattern to look for. Providing a string will result in a case-insensitive substring search. Use a RegExp for more sophisticated searches. |
| [replacement] | <code>string</code> &#124; <code>function</code> | The text to replace or a String.replace callback function. If pattern is a string, all occurrences of the pattern in the cell will be replaced. |

<a name="Cell+formula"></a>

#### cell.formula() ⇒ <code>string</code>
Gets the formula in the cell. Note that if a formula was set as part of a range, the getter will return 'SHARED'. This is a limitation that may be addressed in a future release.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>string</code> - - The formula in the cell.  
<a name="Cell+formula"></a>

#### cell.formula(formula) ⇒ <code>[Cell](#Cell)</code>
Sets the formula in the cell.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Cell](#Cell)</code> - - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| formula | <code>string</code> | The formula to set. |

<a name="Cell+tap"></a>

#### cell.tap(callback) ⇒ <code>[Cell](#Cell)</code>
Invoke a callback on the cell and return the cell. Useful for method chaining.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>[tapCallback](#Cell..tapCallback)</code> | The callback function. |

<a name="Cell+thru"></a>

#### cell.thru(callback) ⇒ <code>\*</code>
Invoke a callback on the cell and return the value provided by the callback. Useful for method chaining.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>\*</code> - The return value of the callback.  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>[thruCallback](#Cell..thruCallback)</code> | The callback function. |

<a name="Cell+rangeTo"></a>

#### cell.rangeTo(cell) ⇒ <code>[Range](#Range)</code>
Create a range from this cell and another.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| cell | <code>[Cell](#Cell)</code> &#124; <code>string</code> | The other cell or cell address to range to. |

<a name="Cell+relativeCell"></a>

#### cell.relativeCell(rowOffset, columnOffset) ⇒ <code>[Cell](#Cell)</code>
Returns a cell with a relative position given the offsets provided.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The relative cell.  

| Param | Type | Description |
| --- | --- | --- |
| rowOffset | <code>number</code> | The row offset (0 for the current row). |
| columnOffset | <code>number</code> | The column offset (0 for the current column). |

<a name="Cell+row"></a>

#### cell.row() ⇒ <code>[Row](#Row)</code>
Gets the parent row of the cell.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Row](#Row)</code> - The parent row.  
<a name="Cell+rowNumber"></a>

#### cell.rowNumber() ⇒ <code>number</code>
Gets the row number of the cell (1-based).

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>number</code> - The row number.  
<a name="Cell+sheet"></a>

#### cell.sheet() ⇒ <code>[Sheet](#Sheet)</code>
Gets the parent sheet.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Sheet](#Sheet)</code> - The parent sheet.  
<a name="Cell+style"></a>

#### cell.style(name) ⇒ <code>\*</code>
Gets an individual style.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>\*</code> - The style.  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the style. |

<a name="Cell+style"></a>

#### cell.style(names) ⇒ <code>object.&lt;string, \*&gt;</code>
Gets multiple styles.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>object.&lt;string, \*&gt;</code> - Object whose keys are the style names and values are the styles.  

| Param | Type | Description |
| --- | --- | --- |
| names | <code>Array.&lt;string&gt;</code> | The names of the style. |

<a name="Cell+style"></a>

#### cell.style(name, value) ⇒ <code>[Cell](#Cell)</code>
Sets an individual style.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the style. |
| value | <code>\*</code> | The value to set. |

<a name="Cell+style"></a>

#### cell.style(styles) ⇒ <code>[Cell](#Cell)</code>
Sets multiple styles.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| styles | <code>object.&lt;string, \*&gt;</code> | Object whose keys are the style names and values are the styles to set. |

<a name="Cell+value"></a>

#### cell.value() ⇒ <code>string</code> &#124; <code>boolean</code> &#124; <code>number</code> &#124; <code>Date</code> &#124; <code>undefined</code>
Gets the value of the cell.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>string</code> &#124; <code>boolean</code> &#124; <code>number</code> &#124; <code>Date</code> &#124; <code>undefined</code> - The value of the cell.  
<a name="Cell+value"></a>

#### cell.value(value) ⇒ <code>[Cell](#Cell)</code>
Sets the value of the cell.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>string</code> &#124; <code>boolean</code> &#124; <code>number</code> &#124; <code>Date</code> &#124; <code>null</code> &#124; <code>undefined</code> | The value to set. |

<a name="Cell+workbook"></a>

#### cell.workbook() ⇒ <code>[Workbook](#Workbook)</code>
Gets the parent workbook.

**Kind**: instance method of <code>[Cell](#Cell)</code>  
**Returns**: <code>[Workbook](#Workbook)</code> - The parent workbook.  
<a name="Cell..tapCallback"></a>

#### Cell~tapCallback ⇒ <code>undefined</code>
Callback used by tap.

**Kind**: inner typedef of <code>[Cell](#Cell)</code>  

| Param | Type | Description |
| --- | --- | --- |
| cell | <code>[Cell](#Cell)</code> | The cell |

<a name="Cell..thruCallback"></a>

#### Cell~thruCallback ⇒ <code>\*</code>
Callback used by thru.

**Kind**: inner typedef of <code>[Cell](#Cell)</code>  
**Returns**: <code>\*</code> - The value to return from thru.  

| Param | Type | Description |
| --- | --- | --- |
| cell | <code>[Cell](#Cell)</code> | The cell |

<a name="Column"></a>

### Column
A column.

**Kind**: global class  

* [Column](#Column)
    * [.address([opts])](#Column+address) ⇒ <code>string</code>
    * [.cell(rowNumber)](#Column+cell) ⇒ <code>[Cell](#Cell)</code>
    * [.columnName()](#Column+columnName) ⇒ <code>string</code>
    * [.columnNumber()](#Column+columnNumber) ⇒ <code>number</code>
    * [.hidden()](#Column+hidden) ⇒ <code>boolean</code>
    * [.hidden(hidden)](#Column+hidden) ⇒ <code>[Column](#Column)</code>
    * [.sheet()](#Column+sheet) ⇒ <code>[Sheet](#Sheet)</code>
    * [.width()](#Column+width) ⇒ <code>undefined</code> &#124; <code>number</code>
    * [.width(width)](#Column+width) ⇒ <code>[Column](#Column)</code>
    * [.workbook()](#Column+workbook) ⇒ <code>[Workbook](#Workbook)</code>

<a name="Column+address"></a>

#### column.address([opts]) ⇒ <code>string</code>
Get the address of the column.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>string</code> - The address  

| Param | Type | Description |
| --- | --- | --- |
| [opts] | <code>Object</code> | Options |
| [opts.includeSheetName] | <code>boolean</code> | Include the sheet name in the address. |
| [opts.anchored] | <code>boolean</code> | Anchor the address. |

<a name="Column+cell"></a>

#### column.cell(rowNumber) ⇒ <code>[Cell](#Cell)</code>
Get a cell within the column.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell in the column with the given row number.  

| Param | Type | Description |
| --- | --- | --- |
| rowNumber | <code>number</code> | The row number. |

<a name="Column+columnName"></a>

#### column.columnName() ⇒ <code>string</code>
Get the name of the column.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>string</code> - The column name.  
<a name="Column+columnNumber"></a>

#### column.columnNumber() ⇒ <code>number</code>
Get the number of the column.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>number</code> - The column number.  
<a name="Column+hidden"></a>

#### column.hidden() ⇒ <code>boolean</code>
Gets a value indicating whether the column is hidden.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>boolean</code> - A flag indicating whether the column is hidden.  
<a name="Column+hidden"></a>

#### column.hidden(hidden) ⇒ <code>[Column](#Column)</code>
Sets whether the column is hidden.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>[Column](#Column)</code> - The column.  

| Param | Type | Description |
| --- | --- | --- |
| hidden | <code>boolean</code> | A flag indicating whether to hide the column. |

<a name="Column+sheet"></a>

#### column.sheet() ⇒ <code>[Sheet](#Sheet)</code>
Get the parent sheet.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>[Sheet](#Sheet)</code> - The parent sheet.  
<a name="Column+width"></a>

#### column.width() ⇒ <code>undefined</code> &#124; <code>number</code>
Gets the width.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>undefined</code> &#124; <code>number</code> - The width (or undefined).  
<a name="Column+width"></a>

#### column.width(width) ⇒ <code>[Column](#Column)</code>
Sets the width.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>[Column](#Column)</code> - The column.  

| Param | Type | Description |
| --- | --- | --- |
| width | <code>number</code> | The width of the column. |

<a name="Column+workbook"></a>

#### column.workbook() ⇒ <code>[Workbook](#Workbook)</code>
Get the parent workbook.

**Kind**: instance method of <code>[Column](#Column)</code>  
**Returns**: <code>[Workbook](#Workbook)</code> - The parent workbook.  
<a name="Range"></a>

### Range
A range of cells.

**Kind**: global class  

* [Range](#Range)
    * _instance_
        * [.address([opts])](#Range+address) ⇒ <code>string</code>
        * [.cell(ri, ci)](#Range+cell) ⇒ <code>[Cell](#Cell)</code>
        * [.clear()](#Range+clear) ⇒ <code>[Range](#Range)</code>
        * [.endCell()](#Range+endCell) ⇒ <code>[Cell](#Cell)</code>
        * [.forEach(callback)](#Range+forEach) ⇒ <code>[Range](#Range)</code>
        * [.formula()](#Range+formula) ⇒ <code>string</code> &#124; <code>undefined</code>
        * [.formula(formula)](#Range+formula) ⇒ <code>[Range](#Range)</code>
        * [.map(callback)](#Range+map) ⇒ <code>Array.&lt;Array.&lt;\*&gt;&gt;</code>
        * [.merged()](#Range+merged) ⇒ <code>boolean</code>
        * [.merged(merged)](#Range+merged) ⇒ <code>[Range](#Range)</code>
        * [.reduce(callback, [initialValue])](#Range+reduce) ⇒ <code>\*</code>
        * [.sheet()](#Range+sheet) ⇒ <code>[Sheet](#Sheet)</code>
        * [.startCell()](#Range+startCell) ⇒ <code>[Cell](#Cell)</code>
        * [.style(name)](#Range+style) ⇒ <code>Array.&lt;Array.&lt;\*&gt;&gt;</code>
        * [.style(names)](#Range+style) ⇒ <code>Object.&lt;string, Array.&lt;Array.&lt;\*&gt;&gt;&gt;</code>
        * [.style(name)](#Range+style) ⇒ <code>[Range](#Range)</code>
        * [.style(name)](#Range+style) ⇒ <code>[Range](#Range)</code>
        * [.style(name, value)](#Range+style) ⇒ <code>[Range](#Range)</code>
        * [.style(styles)](#Range+style) ⇒ <code>[Range](#Range)</code>
        * [.tap(callback)](#Range+tap) ⇒ <code>[Range](#Range)</code>
        * [.thru(callback)](#Range+thru) ⇒ <code>\*</code>
        * [.values()](#Range+values) ⇒ <code>Array.&lt;Array.&lt;\*&gt;&gt;</code>
        * [.values()](#Range+values) ⇒ <code>[Range](#Range)</code>
        * [.values()](#Range+values) ⇒ <code>[Range](#Range)</code>
        * [.values(value)](#Range+values) ⇒ <code>[Range](#Range)</code>
        * [.workbook()](#Range+workbook) ⇒ <code>[Workbook](#Workbook)</code>
    * _inner_
        * [~forEachCallback](#Range..forEachCallback) ⇒ <code>undefined</code>
        * [~mapCallback](#Range..mapCallback) ⇒ <code>\*</code>
        * [~reduceCallback](#Range..reduceCallback) ⇒ <code>\*</code>
        * [~tapCallback](#Range..tapCallback) ⇒ <code>undefined</code>
        * [~thruCallback](#Range..thruCallback) ⇒ <code>\*</code>

<a name="Range+address"></a>

#### range.address([opts]) ⇒ <code>string</code>
Get the address of the range.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>string</code> - The address.  

| Param | Type | Description |
| --- | --- | --- |
| [opts] | <code>Object</code> | Options |
| [opts.includeSheetName] | <code>boolean</code> | Include the sheet name in the address. |
| [opts.startRowAnchored] | <code>boolean</code> | Anchor the start row. |
| [opts.startColumnAnchored] | <code>boolean</code> | Anchor the start column. |
| [opts.endRowAnchored] | <code>boolean</code> | Anchor the end row. |
| [opts.endColumnAnchored] | <code>boolean</code> | Anchor the end column. |

<a name="Range+cell"></a>

#### range.cell(ri, ci) ⇒ <code>[Cell](#Cell)</code>
Gets a cell within the range.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| ri | <code>number</code> | Row index relative to the top-left corner of the range (0-based). |
| ci | <code>number</code> | Column index relative to the top-left corner of the range (0-based). |

<a name="Range+clear"></a>

#### range.clear() ⇒ <code>[Range](#Range)</code>
Clear the contents of all the cells in the range.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  
<a name="Range+endCell"></a>

#### range.endCell() ⇒ <code>[Cell](#Cell)</code>
Get the end cell of the range.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The end cell.  
<a name="Range+forEach"></a>

#### range.forEach(callback) ⇒ <code>[Range](#Range)</code>
Call a function for each cell in the range. Goes by row then column.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>[forEachCallback](#Range..forEachCallback)</code> | Function called for each cell in the range. |

<a name="Range+formula"></a>

#### range.formula() ⇒ <code>string</code> &#124; <code>undefined</code>
Gets the formula shared across the range.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>string</code> &#124; <code>undefined</code> - The shared formula.  
<a name="Range+formula"></a>

#### range.formula(formula) ⇒ <code>[Range](#Range)</code>
Sets the shared formula in the range. The formula will be translated for each cell.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| formula | <code>string</code> | The formula to set. |

<a name="Range+map"></a>

#### range.map(callback) ⇒ <code>Array.&lt;Array.&lt;\*&gt;&gt;</code>
Creates a 2D array of values by running each cell through a callback.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>Array.&lt;Array.&lt;\*&gt;&gt;</code> - The 2D array of return values.  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>[mapCallback](#Range..mapCallback)</code> | Function called for each cell in the range. |

<a name="Range+merged"></a>

#### range.merged() ⇒ <code>boolean</code>
Gets a value indicating whether the cells in the range are merged.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>boolean</code> - The value.  
<a name="Range+merged"></a>

#### range.merged(merged) ⇒ <code>[Range](#Range)</code>
Sets a value indicating whether the cells in the range should be merged.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| merged | <code>boolean</code> | True to merge, false to unmerge. |

<a name="Range+reduce"></a>

#### range.reduce(callback, [initialValue]) ⇒ <code>\*</code>
Reduces the range to a single value accumulated from the result of a function called for each cell.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>\*</code> - The accumulated value.  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>[reduceCallback](#Range..reduceCallback)</code> | Function called for each cell in the range. |
| [initialValue] | <code>\*</code> | The initial value. |

<a name="Range+sheet"></a>

#### range.sheet() ⇒ <code>[Sheet](#Sheet)</code>
Gets the parent sheet of the range.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Sheet](#Sheet)</code> - The parent sheet.  
<a name="Range+startCell"></a>

#### range.startCell() ⇒ <code>[Cell](#Cell)</code>
Gets the start cell of the range.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The start cell.  
<a name="Range+style"></a>

#### range.style(name) ⇒ <code>Array.&lt;Array.&lt;\*&gt;&gt;</code>
Gets a single style for each cell.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>Array.&lt;Array.&lt;\*&gt;&gt;</code> - 2D array of style values.  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the style. |

<a name="Range+style"></a>

#### range.style(names) ⇒ <code>Object.&lt;string, Array.&lt;Array.&lt;\*&gt;&gt;&gt;</code>
Gets multiple styles for each cell.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>Object.&lt;string, Array.&lt;Array.&lt;\*&gt;&gt;&gt;</code> - Object whose keys are style names and values are 2D arrays of style values.  

| Param | Type | Description |
| --- | --- | --- |
| names | <code>Array.&lt;string&gt;</code> | The names of the styles. |

<a name="Range+style"></a>

#### range.style(name) ⇒ <code>[Range](#Range)</code>
Set the style in each cell to the result of a function called for each.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the style. |
|  | <code>[mapCallback](#Range..mapCallback)</code> | The callback to provide value for the cell. |

<a name="Range+style"></a>

#### range.style(name) ⇒ <code>[Range](#Range)</code>
Sets the style in each cell to the corresponding value in the given 2D array of values.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the style. |
|  | <code>Array.&lt;Array.&lt;\*&gt;&gt;</code> | The style values to set. |

<a name="Range+style"></a>

#### range.style(name, value) ⇒ <code>[Range](#Range)</code>
Set the style of all cells in the range to a single style value.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The name of the style. |
| value | <code>\*</code> | The value to set. |

<a name="Range+style"></a>

#### range.style(styles) ⇒ <code>[Range](#Range)</code>
Set multiple styles for the cells in the range.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| styles | <code>object.&lt;string, (Range~mapCallback\|Array.&lt;Array.&lt;\*&gt;&gt;\|\*)&gt;</code> | Object whose keys are style names and values are either function callbacks, 2D arrays of style values, or a single value for all the cells. |

<a name="Range+tap"></a>

#### range.tap(callback) ⇒ <code>[Range](#Range)</code>
Invoke a callback on the range and return the range. Useful for method chaining.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>[tapCallback](#Range..tapCallback)</code> | The callback function. |

<a name="Range+thru"></a>

#### range.thru(callback) ⇒ <code>\*</code>
Invoke a callback on the range and return the value provided by the callback. Useful for method chaining.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>\*</code> - The return value of the callback.  

| Param | Type | Description |
| --- | --- | --- |
| callback | <code>[thruCallback](#Range..thruCallback)</code> | The callback function. |

<a name="Range+values"></a>

#### range.values() ⇒ <code>Array.&lt;Array.&lt;\*&gt;&gt;</code>
Get the values of each cell in the range as a 2D array.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>Array.&lt;Array.&lt;\*&gt;&gt;</code> - The values.  
<a name="Range+values"></a>

#### range.values() ⇒ <code>[Range](#Range)</code>
Set the values in each cell to the result of a function called for each.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
|  | <code>[mapCallback](#Range..mapCallback)</code> | The callback to provide value for the cell. |

<a name="Range+values"></a>

#### range.values() ⇒ <code>[Range](#Range)</code>
Sets the value in each cell to the corresponding value in the given 2D array of values.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
|  | <code>Array.&lt;Array.&lt;\*&gt;&gt;</code> | The values to set. |

<a name="Range+values"></a>

#### range.values(value) ⇒ <code>[Range](#Range)</code>
Set the value of all cells in the range to a single value.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| value | <code>\*</code> | The value to set. |

<a name="Range+workbook"></a>

#### range.workbook() ⇒ <code>[Workbook](#Workbook)</code>
Gets the parent workbook.

**Kind**: instance method of <code>[Range](#Range)</code>  
**Returns**: <code>[Workbook](#Workbook)</code> - The parent workbook.  
<a name="Range..forEachCallback"></a>

#### Range~forEachCallback ⇒ <code>undefined</code>
Callback used by forEach.

**Kind**: inner typedef of <code>[Range](#Range)</code>  

| Param | Type | Description |
| --- | --- | --- |
| cell | <code>[Cell](#Cell)</code> | The cell. |
| ri | <code>number</code> | The relative row index. |
| ci | <code>number</code> | The relative column index. |
| range | <code>[Range](#Range)</code> | The range. |

<a name="Range..mapCallback"></a>

#### Range~mapCallback ⇒ <code>\*</code>
Callback used by map.

**Kind**: inner typedef of <code>[Range](#Range)</code>  
**Returns**: <code>\*</code> - The value to map to.  

| Param | Type | Description |
| --- | --- | --- |
| cell | <code>[Cell](#Cell)</code> | The cell. |
| ri | <code>number</code> | The relative row index. |
| ci | <code>number</code> | The relative column index. |
| range | <code>[Range](#Range)</code> | The range. |

<a name="Range..reduceCallback"></a>

#### Range~reduceCallback ⇒ <code>\*</code>
Callback used by reduce.

**Kind**: inner typedef of <code>[Range](#Range)</code>  
**Returns**: <code>\*</code> - The value to map to.  

| Param | Type | Description |
| --- | --- | --- |
| accumulator | <code>\*</code> | The accumulated value. |
| cell | <code>[Cell](#Cell)</code> | The cell. |
| ri | <code>number</code> | The relative row index. |
| ci | <code>number</code> | The relative column index. |
| range | <code>[Range](#Range)</code> | The range. |

<a name="Range..tapCallback"></a>

#### Range~tapCallback ⇒ <code>undefined</code>
Callback used by tap.

**Kind**: inner typedef of <code>[Range](#Range)</code>  

| Param | Type | Description |
| --- | --- | --- |
| range | <code>[Range](#Range)</code> | The range. |

<a name="Range..thruCallback"></a>

#### Range~thruCallback ⇒ <code>\*</code>
Callback used by thru.

**Kind**: inner typedef of <code>[Range](#Range)</code>  
**Returns**: <code>\*</code> - The value to return from thru.  

| Param | Type | Description |
| --- | --- | --- |
| range | <code>[Range](#Range)</code> | The range. |

<a name="Row"></a>

### Row
A row.

**Kind**: global class  

* [Row](#Row)
    * [.address([opts])](#Row+address) ⇒ <code>string</code>
    * [.cell(columnNameOrNumber)](#Row+cell) ⇒ <code>[Cell](#Cell)</code>
    * [.height()](#Row+height) ⇒ <code>undefined</code> &#124; <code>number</code>
    * [.height(height)](#Row+height) ⇒ <code>[Row](#Row)</code>
    * [.hidden()](#Row+hidden) ⇒ <code>boolean</code>
    * [.hidden(hidden)](#Row+hidden) ⇒ <code>[Row](#Row)</code>
    * [.rowNumber()](#Row+rowNumber) ⇒ <code>number</code>
    * [.sheet()](#Row+sheet) ⇒ <code>[Sheet](#Sheet)</code>
    * [.workbook()](#Row+workbook) ⇒ <code>[Workbook](#Workbook)</code>

<a name="Row+address"></a>

#### row.address([opts]) ⇒ <code>string</code>
Get the address of the row.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>string</code> - The address  

| Param | Type | Description |
| --- | --- | --- |
| [opts] | <code>Object</code> | Options |
| [opts.includeSheetName] | <code>boolean</code> | Include the sheet name in the address. |
| [opts.anchored] | <code>boolean</code> | Anchor the address. |

<a name="Row+cell"></a>

#### row.cell(columnNameOrNumber) ⇒ <code>[Cell](#Cell)</code>
Get a cell in the row.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| columnNameOrNumber | <code>string</code> &#124; <code>number</code> | The name or number of the column. |

<a name="Row+height"></a>

#### row.height() ⇒ <code>undefined</code> &#124; <code>number</code>
Gets the row height.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>undefined</code> &#124; <code>number</code> - The height (or undefined).  
<a name="Row+height"></a>

#### row.height(height) ⇒ <code>[Row](#Row)</code>
Sets the row height.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>[Row](#Row)</code> - The row.  

| Param | Type | Description |
| --- | --- | --- |
| height | <code>number</code> | The height of the row. |

<a name="Row+hidden"></a>

#### row.hidden() ⇒ <code>boolean</code>
Gets a value indicating whether the row is hidden.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>boolean</code> - A flag indicating whether the row is hidden.  
<a name="Row+hidden"></a>

#### row.hidden(hidden) ⇒ <code>[Row](#Row)</code>
Sets whether the row is hidden.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>[Row](#Row)</code> - The row.  

| Param | Type | Description |
| --- | --- | --- |
| hidden | <code>boolean</code> | A flag indicating whether to hide the row. |

<a name="Row+rowNumber"></a>

#### row.rowNumber() ⇒ <code>number</code>
Gets the row number.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>number</code> - The row number.  
<a name="Row+sheet"></a>

#### row.sheet() ⇒ <code>[Sheet](#Sheet)</code>
Gets the parent sheet of the row.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>[Sheet](#Sheet)</code> - The parent sheet.  
<a name="Row+workbook"></a>

#### row.workbook() ⇒ <code>[Workbook](#Workbook)</code>
Get the parent workbook.

**Kind**: instance method of <code>[Row](#Row)</code>  
**Returns**: <code>[Workbook](#Workbook)</code> - The parent workbook.  
<a name="Sheet"></a>

### Sheet
A worksheet.

**Kind**: global class  

* [Sheet](#Sheet)
    * [.cell(address)](#Sheet+cell) ⇒ <code>[Cell](#Cell)</code>
    * [.cell(rowNumber, columnNameOrNumber)](#Sheet+cell) ⇒ <code>[Cell](#Cell)</code>
    * [.column(columnNameOrNumber)](#Sheet+column) ⇒ <code>[Column](#Column)</code>
    * [.definedName(name)](#Sheet+definedName) ⇒ <code>undefined</code> &#124; <code>[Cell](#Cell)</code> &#124; <code>[Range](#Range)</code> &#124; <code>[Row](#Row)</code> &#124; <code>[Column](#Column)</code>
    * [.find(pattern, [replacement])](#Sheet+find) ⇒ <code>[Array.&lt;Cell&gt;](#Cell)</code>
    * [.name()](#Sheet+name) ⇒ <code>string</code>
    * [.range(address)](#Sheet+range) ⇒ <code>[Range](#Range)</code>
    * [.range(startCell, endCell)](#Sheet+range) ⇒ <code>[Range](#Range)</code>
    * [.range(startRowNumber, startColumnNameOrNumber, endRowNumber, endColumnNameOrNumber)](#Sheet+range) ⇒ <code>[Range](#Range)</code>
    * [.row(rowNumber)](#Sheet+row) ⇒ <code>[Row](#Row)</code>
    * [.usedRange()](#Sheet+usedRange) ⇒ <code>[Range](#Range)</code> &#124; <code>undefined</code>
    * [.workbook()](#Sheet+workbook) ⇒ <code>[Workbook](#Workbook)</code>

<a name="Sheet+cell"></a>

#### sheet.cell(address) ⇒ <code>[Cell](#Cell)</code>
Gets the cell with the given address.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| address | <code>string</code> | The address of the cell. |

<a name="Sheet+cell"></a>

#### sheet.cell(rowNumber, columnNameOrNumber) ⇒ <code>[Cell](#Cell)</code>
Gets the cell with the given row and column numbers.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Cell](#Cell)</code> - The cell.  

| Param | Type | Description |
| --- | --- | --- |
| rowNumber | <code>number</code> | The row number of the cell. |
| columnNameOrNumber | <code>string</code> &#124; <code>number</code> | The column name or number of the cell. |

<a name="Sheet+column"></a>

#### sheet.column(columnNameOrNumber) ⇒ <code>[Column](#Column)</code>
Gets a column in the sheet.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Column](#Column)</code> - The column.  

| Param | Type | Description |
| --- | --- | --- |
| columnNameOrNumber | <code>string</code> &#124; <code>number</code> | The name or number of the column. |

<a name="Sheet+definedName"></a>

#### sheet.definedName(name) ⇒ <code>undefined</code> &#124; <code>[Cell](#Cell)</code> &#124; <code>[Range](#Range)</code> &#124; <code>[Row](#Row)</code> &#124; <code>[Column](#Column)</code>
Gets a defined name scoped to the sheet.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>undefined</code> &#124; <code>[Cell](#Cell)</code> &#124; <code>[Range](#Range)</code> &#124; <code>[Row](#Row)</code> &#124; <code>[Column](#Column)</code> - The named selection or undefined if name not found.  
**Throws**:

- <code>Error</code> Will throw if address in defined name is not supported.


| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The defined name. |

<a name="Sheet+find"></a>

#### sheet.find(pattern, [replacement]) ⇒ <code>[Array.&lt;Cell&gt;](#Cell)</code>
Find the given pattern in the sheet and optionally replace it.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Array.&lt;Cell&gt;](#Cell)</code> - The matching cells.  

| Param | Type | Description |
| --- | --- | --- |
| pattern | <code>string</code> &#124; <code>RegExp</code> | The pattern to look for. Providing a string will result in a case-insensitive substring search. Use a RegExp for more sophisticated searches. |
| [replacement] | <code>string</code> &#124; <code>function</code> | The text to replace or a String.replace callback function. If pattern is a string, all occurrences of the pattern in each cell will be replaced. |

<a name="Sheet+name"></a>

#### sheet.name() ⇒ <code>string</code>
Get the name of the sheet.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>string</code> - The sheet name.  
<a name="Sheet+range"></a>

#### sheet.range(address) ⇒ <code>[Range](#Range)</code>
Gets a range from the given range address.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| address | <code>string</code> | The range address (e.g. 'A1:B3'). |

<a name="Sheet+range"></a>

#### sheet.range(startCell, endCell) ⇒ <code>[Range](#Range)</code>
Gets a range from the given cells or cell addresses.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| startCell | <code>string</code> &#124; <code>[Cell](#Cell)</code> | The starting cell or cell address (e.g. 'A1'). |
| endCell | <code>string</code> &#124; <code>[Cell](#Cell)</code> | The ending cell or cell address (e.g. 'B3'). |

<a name="Sheet+range"></a>

#### sheet.range(startRowNumber, startColumnNameOrNumber, endRowNumber, endColumnNameOrNumber) ⇒ <code>[Range](#Range)</code>
Gets a range from the given row numbers and column names or numbers.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Range](#Range)</code> - The range.  

| Param | Type | Description |
| --- | --- | --- |
| startRowNumber | <code>number</code> | The starting cell row number. |
| startColumnNameOrNumber | <code>string</code> &#124; <code>number</code> | The starting cell column name or number. |
| endRowNumber | <code>number</code> | The ending cell row number. |
| endColumnNameOrNumber | <code>string</code> &#124; <code>number</code> | The ending cell column name or number. |

<a name="Sheet+row"></a>

#### sheet.row(rowNumber) ⇒ <code>[Row](#Row)</code>
Gets the row with the given number.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Row](#Row)</code> - The row with the given number.  

| Param | Type | Description |
| --- | --- | --- |
| rowNumber | <code>number</code> | The row number. |

<a name="Sheet+usedRange"></a>

#### sheet.usedRange() ⇒ <code>[Range](#Range)</code> &#124; <code>undefined</code>
Get the range of cells in the sheet that have contained a value or style at any point. Useful for extracting the entire sheet contents.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Range](#Range)</code> &#124; <code>undefined</code> - The used range or undefined if no cells in the sheet are used.  
<a name="Sheet+workbook"></a>

#### sheet.workbook() ⇒ <code>[Workbook](#Workbook)</code>
Gets the parent workbook.

**Kind**: instance method of <code>[Sheet](#Sheet)</code>  
**Returns**: <code>[Workbook](#Workbook)</code> - The parent workbook.  
<a name="Workbook"></a>

### Workbook
A workbook.

**Kind**: global class  

* [Workbook](#Workbook)
    * _instance_
        * [.definedName(name)](#Workbook+definedName) ⇒ <code>undefined</code> &#124; <code>[Cell](#Cell)</code> &#124; <code>[Range](#Range)</code> &#124; <code>[Row](#Row)</code> &#124; <code>[Column](#Column)</code>
        * [.find(pattern, [replacement])](#Workbook+find) ⇒ <code>boolean</code>
        * [.outputAsync([type])](#Workbook+outputAsync) ⇒ <code>string</code> &#124; <code>Uint8Array</code> &#124; <code>ArrayBuffer</code> &#124; <code>Blob</code> &#124; <code>Buffer</code>
        * [.sheet(sheetNameOrIndex)](#Workbook+sheet) ⇒ <code>[Sheet](#Sheet)</code> &#124; <code>undefined</code>
        * [.toFileAsync(path)](#Workbook+toFileAsync) ⇒ <code>Promise.&lt;undefined&gt;</code>
    * _static_
        * [.MIME_TYPE](#Workbook.MIME_TYPE) : <code>string</code>
        * [.dateToNumber(date)](#Workbook.dateToNumber) ⇒ <code>number</code>
        * [.fromBlankAsync()](#Workbook.fromBlankAsync) ⇒ <code>[Promise.&lt;Workbook&gt;](#Workbook)</code>
        * [.fromDataAsync(data)](#Workbook.fromDataAsync) ⇒ <code>[Promise.&lt;Workbook&gt;](#Workbook)</code>
        * [.fromFileAsync(path)](#Workbook.fromFileAsync) ⇒ <code>[Promise.&lt;Workbook&gt;](#Workbook)</code>
        * [.numberToDate(number)](#Workbook.numberToDate) ⇒ <code>Date</code>

<a name="Workbook+definedName"></a>

#### workbook.definedName(name) ⇒ <code>undefined</code> &#124; <code>[Cell](#Cell)</code> &#124; <code>[Range](#Range)</code> &#124; <code>[Row](#Row)</code> &#124; <code>[Column](#Column)</code>
Gets a defined name scoped to the workbook.

**Kind**: instance method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>undefined</code> &#124; <code>[Cell](#Cell)</code> &#124; <code>[Range](#Range)</code> &#124; <code>[Row](#Row)</code> &#124; <code>[Column](#Column)</code> - The named selection or undefined if name not found.  
**Throws**:

- <code>Error</code> Will throw if address in defined name is not supported.


| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | The defined name. |

<a name="Workbook+find"></a>

#### workbook.find(pattern, [replacement]) ⇒ <code>boolean</code>
Find the given pattern in the workbook and optionally replace it.

**Kind**: instance method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>boolean</code> - A flag indicating if the pattern was found.  

| Param | Type | Description |
| --- | --- | --- |
| pattern | <code>string</code> &#124; <code>RegExp</code> | The pattern to look for. Providing a string will result in a case-insensitive substring search. Use a RegExp for more sophisticated searches. |
| [replacement] | <code>string</code> &#124; <code>function</code> | The text to replace or a String.replace callback function. If pattern is a string, all occurrences of the pattern in each cell will be replaced. |

<a name="Workbook+outputAsync"></a>

#### workbook.outputAsync([type]) ⇒ <code>string</code> &#124; <code>Uint8Array</code> &#124; <code>ArrayBuffer</code> &#124; <code>Blob</code> &#124; <code>Buffer</code>
Generates the workbook output.

**Kind**: instance method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>string</code> &#124; <code>Uint8Array</code> &#124; <code>ArrayBuffer</code> &#124; <code>Blob</code> &#124; <code>Buffer</code> - The data.  

| Param | Type | Description |
| --- | --- | --- |
| [type] | <code>string</code> | The type of the data to return. (Supports any supported [JSZip data types](https://stuk.github.io/jszip/documentation/api_jszip/generate_async.html): base64, binarystring, uint8array, arraybuffer, blob, nodebuffer) Defaults to 'nodebuffer' in Node.js and 'blob' in browsers. |

<a name="Workbook+sheet"></a>

#### workbook.sheet(sheetNameOrIndex) ⇒ <code>[Sheet](#Sheet)</code> &#124; <code>undefined</code>
Gets the sheet with the provided name or index (0-based).

**Kind**: instance method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>[Sheet](#Sheet)</code> &#124; <code>undefined</code> - The sheet or undefined if not found.  

| Param | Type | Description |
| --- | --- | --- |
| sheetNameOrIndex | <code>string</code> &#124; <code>number</code> | The sheet name or index. |

<a name="Workbook+toFileAsync"></a>

#### workbook.toFileAsync(path) ⇒ <code>Promise.&lt;undefined&gt;</code>
Write the workbook to file. (Not supported in browsers.)

**Kind**: instance method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>Promise.&lt;undefined&gt;</code> - A promise.  

| Param | Type | Description |
| --- | --- | --- |
| path | <code>string</code> | The path of the file to write. |

<a name="Workbook.MIME_TYPE"></a>

#### Workbook.MIME_TYPE : <code>string</code>
The XLSX mime type.

**Kind**: static property of <code>[Workbook](#Workbook)</code>  
<a name="Workbook.dateToNumber"></a>

#### Workbook.dateToNumber(date) ⇒ <code>number</code>
Convert a date to a number for Excel.

**Kind**: static method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>number</code> - The number.  

| Param | Type | Description |
| --- | --- | --- |
| date | <code>Date</code> | The date. |

<a name="Workbook.fromBlankAsync"></a>

#### Workbook.fromBlankAsync() ⇒ <code>[Promise.&lt;Workbook&gt;](#Workbook)</code>
Create a new blank workbook.

**Kind**: static method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>[Promise.&lt;Workbook&gt;](#Workbook)</code> - The workbook.  
<a name="Workbook.fromDataAsync"></a>

#### Workbook.fromDataAsync(data) ⇒ <code>[Promise.&lt;Workbook&gt;](#Workbook)</code>
Loads a workbook from a data object. (Supports any supported [JSZip data types](https://stuk.github.io/jszip/documentation/api_jszip/load_async.html).)

**Kind**: static method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>[Promise.&lt;Workbook&gt;](#Workbook)</code> - The workbook.  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>string</code> &#124; <code>Array.&lt;number&gt;</code> &#124; <code>ArrayBuffer</code> &#124; <code>Uint8Array</code> &#124; <code>Buffer</code> &#124; <code>Blob</code> &#124; <code>Promise.&lt;\*&gt;</code> | The data to load. |

<a name="Workbook.fromFileAsync"></a>

#### Workbook.fromFileAsync(path) ⇒ <code>[Promise.&lt;Workbook&gt;](#Workbook)</code>
Loads a workbook from file.

**Kind**: static method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>[Promise.&lt;Workbook&gt;](#Workbook)</code> - The workbook.  

| Param | Type | Description |
| --- | --- | --- |
| path | <code>string</code> | The path to the workbook. |

<a name="Workbook.numberToDate"></a>

#### Workbook.numberToDate(number) ⇒ <code>Date</code>
Convert an Excel number to a date.

**Kind**: static method of <code>[Workbook](#Workbook)</code>  
**Returns**: <code>Date</code> - The date.  

| Param | Type | Description |
| --- | --- | --- |
| number | <code>number</code> | The number. |


