# HTML Codeacademy Intro Notes

## HTML Basics

- HTML is a markup language is a computer language that defines the structure and presentation of raw text.
- A tag and the content between it is called an HTML element.
- When an element is contained inside another element, it is considered the child of that element. The child element is said to be nested inside of the parent element.
- Question - is it ok practice to use tab for indentation instead of the space bar?
    - "There is no official standard on how many spaces or tabs to indent by within our HTML documents. So long as you are consistent, you may use tabs rather than spaces if you prefer. That having been said, 2 space indentation is very common and adheres to Google’s HTML style guide."
- If you want to display text in HTML, you can use a paragraph or span.
- It's best to use a <span> element when you want to target a specific piece of content that is inline, or on the same line as other text
- The <em> tag emphasizes text, while the <strong> tag highlights important text.
- The `<em>` tag will generally render as *italic* emphasis.
- The `<strong>` will generally render as **bold** emphasis.
- The line break element is unique because it is only composed of a starting tag. <br>
- In HTML, you can use an unordered list tag (<ul>) to create a list of items in no particular order.
- The <img> tag allows you to add an image to a web page. Most elements require both opening and closing tags, but the <img> tag is a self-closing tag. Note that the end of the <img> tag has a forward slash /
- The alt attribute, which means alternative text, brings meaning to the images on our sites. The alt attribute can be added to the image tag just like the src attribute. The value of alt should be a description of the image.

## HTML Formatting, Structure and Lists

- `<!DOCTYPE html>`, the declaration specifying the version of HTML for the browser
- The `<html>` tags that enclose all of your HTML code
- The `<head>` tag that contains the metadata of a webpage, such as its `<title>`

- Thankfully, HTML allows you to turn nearly any element into a link by wrapping that element with an anchor element. With this technique, it's possible to turn images into links by simply wrapping the `<img>` element with an `<a>` element.

    <a href="https://en.wikipedia.org/wiki/Opuntia" target="_blank"><img src="#" alt="A red prickly pear fruit"/></a>

In order to link to a *target* on the same page, we must give the target an *id*, like this:

    <p id="top">This is the top of the page!</p>
    <h1 id="bottom">This is the bottom! </h1>

An `id` should be descriptive to make it easier to remember the purpose of a link. The target link is a string containing the `#`character and the target element's `id`.

    <ol>
      <li><a href="#top">Top</a></li>
      <li><a href="#bottom">Bottom</a></li>
    </ol>

- Comments begin with <!-- and end with -->. Any characters in between will be ignored by your browser.
- The first step in entering data into the table is to add rows using the *table row* element: `<tr>`.

    <table>
      <tr>
      </tr>
      <tr>
      </tr>
    </table>

- Rows aren't sufficient to add data to a table. Each cell element must also be defined. In HTML, you can add data using the *table data* element: `<td>`.

    <table>
      <tr>
        <td>73</td>
        <td>81</td>
      </tr>
    </table>

## Lists

1. The `<table>` element creates a table.
2. The `<tr>` element adds rows to a table.
3. To add data to a row, you can use the `<td>` element.
4. Table headings clarify the meaning of data. Headings are added with the `<th>` element.
5. Table data can span columns using the `colspan` attribute.
6. Table data can span rows using the `rowspan` attribute.
7. Tables can be split into three main sections: a head, a body, and a footer.
8. A table's head is created with the `<thead>` element.
9. A table's body is created with the `<tbody>` element.
10. A table's footer is created with the `<tfoot>` element.
11. All the CSS properties you learned about in this course can be applied to tables and their data.

## Forms

- We need to supply the <form> element with both the location of where the <form>'s information goes and what HTTP request to make.
- The action attribute determines where the information is sent and the method attribute is assigned a HTTP verb that is included in the HTTP request. (Note: HTTP verbs like POST do not need to be capitalized for the request to work, but it's done so out of convention.
- The purpose of a `<form>` is to allow users to input information and send it.
- The `<form>`'s `action` attribute determines where the form's information goes.
- The `<form>`'s `method` attribute determines how the information is sent and processed.
- To add fields for users to input information we use the `<input>` element and set the `type` attribute to a field of our choosing:
    - Setting `type` to `"text"` creates a single row field for text input.
    - Setting `type` to `"password"` creates a single row field that censors text input.
    - Setting `type` to `"number"` creates a single row field for number input.
    - Setting `type` to `"range"` creates a slider to select from a range of numbers.
    - Setting `type` to `"checkbox"` creates a single checkbox which can be paired with other checkboxes.
    - Setting `type` to `"radio"` creates a radio button that can be paired with other radio buttons.
    - Setting `type` to `"list"` will pair the `<input>` with a `<datalist>` element.
    - Setting `type` to `"submit"` creates a submit button.
- A `<select>` element is populated with `<option>` elements and renders a dropdown list selection.
- A `<datalist>` element is populated with `<option>`elements and works with an `<input>` to search through choices.
- A `<textarea>` element is a text input field that has a customizable area.
- When a `<form>` is submitted, the `name` of the fields that accept input and the `value` of those fields are sent as `name=value` pairs.

## Validation

- Client-side validations happen in the browser before information is sent to a server.
- Adding the `required` attribute to an input related element will validate that the input field has information in it.
- Assigning a value to the `min` attribute of a number input element will validate an acceptable minimum value.
- Assigning a value to the `max` attribute of a number input element will validate an acceptable maximum value.
- Assigning a value to the `minlength` attribute of a text input element will validate an acceptable minimum number of characters.
- Assigning a value to the `maxlength` attribute of a text input element will validate an acceptable maximum number of characters.
- Assigning a regex to `pattern` matches the input to the provided regex.
- If validations on a `<form>` do not pass, the user gets a message explaining why and the `<form>` cannot be submitted