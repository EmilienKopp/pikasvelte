# Pikasvelte

A refreshing Svelte 5 Datepicker component — lightweight, no dependencies, modular CSS.

Based on the original [Pikaday](https://github.com/Pikaday/Pikaday) by David Bushell.

## Installation

```bash
npm install pikasvelte
```

## Usage

### Using the Pikaday class directly

```svelte
<script>
  import { Pikaday } from 'pikasvelte';
  import 'pikasvelte/pikaday.css';
  import { onMount } from 'svelte';

  let picker;
  let inputElement;

  onMount(() => {
    picker = new Pikaday({ field: inputElement });
    return () => picker?.destroy();
  });
</script>

<input type="text" bind:this={inputElement} />
```

## Configuration

Pikaday supports many useful options:

- `field` - bind the datepicker to a form field
- `trigger` - use a different element to trigger opening the datepicker
- `bound` - automatically show/hide the picker on `field` focus (default `true` if `field` is set)
- `position` - preferred position of the datepicker relative to the form field
- `format` - the default output format for `.toString()` and `field` value
- `defaultDate` - the initial date to view when first opened
- `minDate` - the minimum/earliest date that can be selected
- `maxDate` - the maximum/latest date that can be selected
- `disableWeekends` - disallow selection of Saturdays or Sundays
- `yearRange` - number of years either side (e.g. `10`) or array of upper/lower range
- `showWeekNumber` - show the ISO week number at the head of the row
- `i18n` - language defaults for month and weekday names
- `onSelect` - callback function for when a date is selected
- `onOpen` - callback function for when the picker becomes visible
- `onClose` - callback function for when the picker is hidden

## Methods

```javascript
picker.toString('YYYY-MM-DD')  // Returns formatted date string
picker.getDate()               // Returns Date object or null
picker.setDate('2024-01-01')   // Set the current selection
picker.clear()                 // Clear the selection
picker.gotoDate(new Date())    // Change view to specific date
picker.gotoToday()             // Go to today
picker.show()                  // Show the picker
picker.hide()                  // Hide the picker
picker.destroy()               // Clean up and remove event listeners
```

## Development

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build the library
npm run package

# Run type checking
npm run check

# Run linting
npm run lint
```

## Project Structure

```
pikasvelte/
├── src/
│   ├── lib/           # Library source files
│   │   ├── index.js   # Main exports
│   │   ├── pikaday.js # Core Pikaday class
│   │   └── pikaday.css
│   ├── routes/        # Demo/documentation pages
│   └── app.html
├── dist/              # Built library (generated)
├── svelte.config.js
├── vite.config.js
└── package.json
```

## License

BSD & MIT license

Copyright © 2014 David Bushell (original Pikaday)
