# Human Body Map Component Documentation v1.0

[Ler em Português (Brasil)](./README-ptbr.md)

## Table of Contents
1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Basic Usage](#basic-usage)
4. [Properties](#properties)
5. [Events](#events)
6. [Examples](#examples)
7. [Compatibility](#compatibility)
8. [Troubleshooting](#troubleshooting)

## Introduction

The Human Body Map is an interactive web component that allows users to view and interact with different systems of the human body. The component offers the following features:

- Interactive human body visualization
- Selection of various anatomical systems
- Identification and selection of specific organs
- Display of medical findings when a CPF is provided
- Real-time visual feedback for user interactions

## Installation

### Using a CDN
```html
<script type="module" src="https://d2343lbggy2b29.cloudfront.net/human-body-map-illustration-[version].js"></script>
```

> **Important Note**: When implemented in a web view, ensure JavaScript is enabled for the component to function properly.

## Basic Usage

Add the component to your HTML:

```html
<human-body-map
    cpf="12345678900"
    access-key="your-access-key">
</human-body-map>
```

> **Note**: The CPF parameter is optional. Without it, the component will function normally but will not display any associated medical findings.

## Properties

| Property         | Type   | Description                                   | Required |
|------------------|--------|-----------------------------------------------|----------|
| cpf              | String | Patient's CPF for displaying findings         | No       |
| access-key       | String | Authentication key for API access             | Yes      |
| selected-system  | String | Currently selected body system                | No       |
| selected-organ   | String | Currently selected organ                      | No       |

## Interactivity

The component supports various interactions:

1. **Hover over organs**:
   - When hovering over an organ, it gets highlighted and its name is displayed.
   - Immediate visual feedback to aid identification.

2. **System selection**:
   - Click on system buttons to toggle between different views.
   - The background image dynamically changes to display the selected system.

3. **Organ selection**:
   - Click on specific organs to select them.
   - The selected organ is highlighted in blue.
   - Displays detailed information when findings are associated with the CPF.

## Events

The component emits the following custom events:

### organ-click
Triggered when an organ is clicked.

```javascript
bodyMap.addEventListener('organ-click', (e) => {
    console.log('Selected:', e.detail);
    // e.detail = { system: "Nervous System", organ: "Brain" }
});
```

### reset-filter
Triggered when filters are reset.

```javascript
bodyMap.addEventListener('reset-filter', () => {
    console.log('Filters have been reset');
});
```

## Examples

### Online Demo
You can view a working example of the component on JSFiddle:  
[Human Body Map Demo](https://jsfiddle.net/sysnee/zv9tbhsm/3/)

### Basic Implementation
```html
<!DOCTYPE html>
<html>
<head>
    <script type="module" src="https://d2343lbggy2b29.cloudfront.net/human-body-map-illustration-1.0.0.js"></script>
</head>
<body>
    <human-body-map
        id="bodyMap"
        cpf="12345678900"
        access-key="demo-key">
    </human-body-map>
</body>
</html>
```

### Implementation with System Buttons
```html
<div class="system-buttons">
    <button class="system-button" data-system="default">Overview</button>
    <button class="system-button" data-system="Nervous System">Nervous System</button>
    <!-- Add other system buttons as needed -->
</div>

<human-body-map id="bodyMap"></human-body-map>

<script>
    const bodyMap = document.getElementById('bodyMap');
    const buttons = document.querySelectorAll('.system-button');

    buttons.forEach(button => {
        button.addEventListener('click', () => {
            const system = button.dataset.system;
            if (system === 'default') {
                bodyMap.resetOrganFilter();
            } else {
                bodyMap.selectedSystem = system;
            }
        });
    });
</script>
```

## Styling

You can style the component using CSS:

```css
human-body-map {
    width: 100%;
    height: 500px;
    display: block;
}
```

## Troubleshooting

### Common Issues

1. **Component does not load**:
   - Verify if the script is loaded correctly.
   - Ensure JavaScript is enabled.
   - Check if the access key is valid.

2. **Images do not appear**:
   - Check the internet connection.
   - Verify access to the CDN.
   - Confirm the CORS configuration.

3. **Events are not working**:
   - Check the implementation of event listeners.
   - Review the browser console for errors.
   - Ensure the component is properly mounted.

### Error Messages

| Error                 | Cause                                | Solution                         |
|-----------------------|--------------------------------------|----------------------------------|
| "Invalid access key"  | Invalid or expired access key        | Verify the key's validity        |
| "Invalid system"      | Invalid system selection             | Check the system's name          |
| "Error fetching data" | Network or API error                 | Check the connection and API     |

## Support

Feel free to report issues and ask questions!  
--- 
