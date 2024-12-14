# Uncommon HTML Bug: DOM access before parsing

This repository demonstrates an uncommon bug in HTML that occurs when attempting to access and manipulate the DOM (Document Object Model) before the browser has finished parsing the HTML.  The bug is subtle and often overlooked because the typical `DOMContentLoaded` event isn't always sufficient to address the issue in all scenarios.

## Bug Description
The primary issue lies in accessing `document.getElementById("myDiv")` before the element with the ID 'myDiv' has been fully parsed by the browser.  The browser's rendering process takes place asynchronously, and executing JavaScript that interacts with the DOM too early can lead to errors.  These errors may not always be immediately obvious; they might manifest as unexpected behavior or silent failures.

## How to Reproduce
1. Open `bug.html` in a web browser.
2. Observe that the error is thrown in the browser's console, indicating that `document.getElementById("myDiv")` returned null before the element existed.

## Solution
The solution involves ensuring the script attempting to access the DOM executes after the element has been parsed.  The most robust way to do this is using the `DOMContentLoaded` event.

## Solution Details
The `bugSolution.html` file provides the corrected code that leverages the `DOMContentLoaded` event to guarantee the script runs only after the document is fully parsed.  This prevents the null reference error and ensures the correct execution of the JavaScript code.