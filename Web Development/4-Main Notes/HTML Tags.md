
**Status:**  #Incomplete
**Tags:** [[frontend]]

---

## **`<div>`**

- **Syntax**: `<div>...</div>`
- **Description**: Defines a division or section in an HTML document.
- **Usage**: Commonly used as a container for grouping and styling other elements.

---

## **`<p>`**

- **Syntax**: `<p>...</p>`
- **Description**: Defines a paragraph.
- **Usage**: Used to group and format text as a standalone paragraph.

---

## **`<a>`**

- **Syntax**: `<a href="...">...</a>`
- **Description**: Defines a hyperlink.
- **Attributes**:
    - `href`: Specifies the URL the link points to.
- **Usage**: Used to navigate to different pages or sections.

---

## **`<img>`**

- **Syntax**: `<img src="..." alt="...">`
- **Description**: Embeds an image in the document.
- **Attributes**:
    - `src`: Specifies the image file path.
    - `alt`: Provides alternative text for the image.
- **Usage**: Displays an image with optional descriptive text for accessibility.

---
## **`<ul>`** - Unordered List

- **Syntax**:
    
    ```html
    <ul>
      <li>...</li>
    </ul>
    ```
    
- **Description**: Defines an unordered list, where items are marked with bullets (default style).
- **Attributes**:
    - `type` (optional): Specifies the bullet style (`disc`, `circle`, or `square`).
- **Usage Example**:
    
    ```html
    <ul>
      <li>Item 1</li>
      <li>Item 2</li>
    </ul>
    ```
    

---

## **`<ol>`** - Ordered List

- **Syntax**:
    
    ```html
    <ol>
      <li>...</li>
    </ol>
    ```
    
- **Description**: Defines an ordered list, where items are marked with numbers or letters.
- **Attributes**:
    - `type` (optional): Specifies the numbering style (`1`, `a`, `A`, `i`, or `I`).
    - `start` (optional): Specifies the starting value for the list.
    - `reversed` (optional): Reverses the order of the list.
- **Usage Example**:
    
    ```html
    <ol start="5">
      <li>Step 5</li>
      <li>Step 6</li>
    </ol>
    ```
    

---

## **`<li>`** - List Item

- **Syntax**:
    
    ```html
    <li>...</li>
    ```
    
- **Description**: Defines an item in a list (used within `<ul>` or `<ol>`).
- **Attributes**:
    - No special attributes; inherits styles based on the parent tag.
- **Usage Example**:
    
    ```html
    <ul>
      <li>First item</li>
      <li>Second item</li>
    </ul>
    ```
    

---

## **`<table>`** - Table

- **Syntax**:
    
    ```html
    <table>...</table>
    ```
    
- **Description**: Defines a table structure in HTML.
- **Attributes**:
    - `border` (optional): Specifies the border width.
    - `cellpadding` (optional): Defines space between cell content and borders.
    - `cellspacing` (optional): Defines space between table cells.
    - `width` and `height`: Define the table's dimensions.
- **Usage Example**:
    
    ```html
    <table border="1">
      <tr>
        <th>Header 1</th>
        <th>Header 2</th>
      </tr>
      <tr>
        <td>Data 1</td>
        <td>Data 2</td>
      </tr>
    </table>
    ```
    

---

## **`<tr>`** - Table Row

- **Syntax**:
    
    ```html
    <tr>...</tr>
    ```
    
- **Description**: Defines a row within a table.
- **Usage Example**:
    
    ```html
    <table>
      <tr>
        <td>Row 1, Column 1</td>
        <td>Row 1, Column 2</td>
      </tr>
    </table>
    ```
    

---

## **`<th>`** - Table Header Cell

- **Syntax**:
    
    ```html
    <th>...</th>
    ```
    
- **Description**: Defines a header cell in a table. Text is bold and centered by default.
- **Attributes**:
    - `scope`: Specifies whether the header applies to a row, column, or group (`row`, `col`, `rowgroup`, `colgroup`).
- **Usage Example**:
    
    ```html
    <table>
      <tr>
        <th>Header 1</th>
        <th>Header 2</th>
      </tr>
    </table>
    ```
    

---

## **`<td>`** - Table Data Cell

- **Syntax**:
    
    ```html
    <td>...</td>
    ```
    
- **Description**: Defines a data cell in a table.
- **Attributes**:
    - `colspan`: Specifies the number of columns a cell should span.
    - `rowspan`: Specifies the number of rows a cell should span.
- **Usage Example**:
    
    ```html
    <table>
      <tr>
        <td>Data 1</td>
        <td colspan="2">Spanned Data</td>
      </tr>
    </table>
    ```
    
---
## **`<form>`** - HTML Form

- **Syntax**:
    
    ```html
    <form action="..." method="...">
      ...
    </form>
    ```
    
- **Description**: Defines an HTML form to collect user input.
- **Attributes**:
    - `action`: Specifies the URL where form data is sent.
    - `method`: Defines the HTTP method (`GET` or `POST`) for form submission.
    - `enctype`: Specifies the encoding type (`application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain`).
- **Usage Example**:
    
    ```html
    <form action="/submit" method="POST">
      <input type="text" name="username">
      <button type="submit">Submit</button>
    </form>
    ```
    

---

## **`<input>`** - Input Control

- **Syntax**:
    
    ```html
    <input type="..." name="..." value="...">
    ```
    
- **Description**: Defines an input field for user data within a form.
- **Attributes**:
    - `type`: Specifies the input type (`text`, `password`, `email`, `checkbox`, `radio`, etc.).
    - `name`: Assigns a name to the input for form submission.
    - `value`: Specifies the default value.
    - `placeholder`: Provides hint text inside the field.
    - `required`: Marks the input as mandatory.
- **Usage Example**:
    
    ```html
    <input type="text" name="username" placeholder="Enter your name" required>
    ```
    

---

## **`<button>`** - Button

- **Syntax**:
    
    ```html
    <button type="...">...</button>
    ```
    
- **Description**: Defines a clickable button.
- **Attributes**:
    - `type`: Specifies button type (`submit`, `reset`, `button`).

The `type` attribute of the `<button>` element in HTML specifies the behavior of the button. It determines what action the button will perform when clicked. There are three main values for the `type` attribute:
#### **1. `submit` (Default Value)**

- **Description**:  
    When a `<button>` is inside a `<form>` and has `type="submit"`, clicking the button will submit the form's data to the URL specified in the `action` attribute of the `<form>`.
- **Behavior**:
    - If no `type` is specified, `<button>` defaults to `type="submit"`.
    - Form validation rules (e.g., `required` fields) are checked before submission.
    - Triggers the `onsubmit` event of the form (if defined in JavaScript).
- **Usage Example**:
    
    ```html
    <form action="/submit" method="POST">
      <input type="text" name="username" required>
      <button type="submit">Submit Form</button>
    </form>
    ```
    

---

#### **2. `reset`**

- **Description**:  
    Clicking a button with `type="reset"` will clear all user inputs in the form to their default values (initial values when the form was loaded).
- **Behavior**:
    - Does not submit the form.
    - Resets text inputs, checkboxes, radio buttons, and other form elements.
- **Usage Example**:
    
    ```html
    <form>
      <input type="text" name="username" placeholder="Enter your name">
      <button type="reset">Reset Form</button>
    </form>
    ```
    

---

#### **3. `button`**

- **Description**:  
    A button with `type="button"` has no default behavior. It can be used for custom functionality, such as triggering JavaScript functions.
- **Behavior**:
    - Does not submit or reset the form.
    - Requires a custom script or event handler to define its behavior.
- **Usage Example**:
    
    ```html
    <button type="button" onclick="alert('Button clicked!')">Click Me</button>
    ```
    

---

### **Comparison of Button Types**

|**Type**|**Default Action**|**Common Use Case**|
|---|---|---|
|`submit`|Submits the form data to the server|Form submission|
|`reset`|Clears all user inputs and resets to default values|Resetting form fields|
|`button`|No default action; relies on JavaScript|Custom actions, e.g., showing modals|

---

## **`<h1>` – `<h6>`** - Headings

- **Syntax**:
    
    ```html
    <h1>...</h1>
    ```
    
- **Description**: Defines headings, with `<h1>` being the most important and `<h6>` the least.
- **Usage Example**:
    
    ```html
    <h1>Main Heading</h1>
    <h2>Subheading</h2>
    <h3>Section Title</h3>
    ```
    

---

## **`<span>`** - Inline Container

- **Syntax**:
    
    ```html
    <span>...</span>
    ```
    
- **Description**: Defines a generic inline container for styling or grouping inline elements.
- **Attributes**:
    - Commonly styled using CSS (`class`, `id`).
- **Usage Example**:
    
    ```html
    <span class="highlight">Highlighted Text</span>
    ```
    

---

## **`<label>`** - Label for Input

- **Syntax**:
    
    ```html
    <label for="...">...</label>
    ```
    
- **Description**: Associates a label with an input element to improve accessibility.
- **Attributes**:
    - `for`: Specifies the `id` of the input element it labels.
- **Usage Example**:
    
    ```html
    <label for="username">Username:</label>
    <input type="text" id="username" name="username">
    ```
    

---

## **`<iframe>`** - Inline Frame

- **Syntax**:
    
    ```html
    <iframe src="..." width="..." height="..."></iframe>
    ```
    
- **Description**: Embeds external content like web pages or videos within an inline frame.
- **Attributes**:
    - `src`: Specifies the URL of the content to embed.
    - `width` and `height`: Define the size of the iframe.
    - `allowfullscreen`: Allows full-screen mode for videos or content.
- **Usage Example**:
    
    ```html
    <iframe src="https://example.com" width="600" height="400"></iframe>
    ```
    
