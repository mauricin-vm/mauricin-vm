# HTML Usage Manual

## Basic Structure
```html
<!DOCTYPE html>
<html lang="en"> <!-- root -->
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Page Title</title>
  </head>
  <body>
      <!-- Page content here -->
  </body>
</html>
```

## Text Elements
```html
<!-- Headings -->
<h1>Main Title</h1>
<h2>Subtitle</h2>
<h3>Level 3 Heading</h3>
<!-- up to h6 -->

<!-- Paragraphs and formatting -->
<p>Text paragraph</p>
<strong>Bold text</strong>
<em>Italic text</em>
<s>Crossed out text</s>
<mark>Marked text</mark>
<br> <!-- Line break -->
<hr> <!-- Horizontal line -->
```

## Links and Images
```html
<!-- Links -->
<a href="https://www.example.com">External link</a>
<a href="page.html">Internal link</a>
<a href="#section">Link to section on same page</a>

<!-- Images -->
<img src="path/image.jpg" alt="Image description">
<figure>
    <img src="photo.jpg" alt="Description">
    <figcaption>Image caption</figcaption>
</figure>
```

## Lists
```html
<!-- Unordered list -->
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
</ul>

<!-- Ordered list -->
<ol>
    <li>First item</li>
    <li>Second item</li>
</ol>

<!-- Definition list -->
<dl>
    <dt>Term</dt>
    <dd>Definition</dd>
</dl>
```

## Tables
```html
<table>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Data 1</td>
            <td>Data 2</td>
        </tr>
    </tbody>
</table>
```

## Forms
```html
<form action="/submit" method="POST">
    <!-- Text fields -->
    <input type="text" name="name" placeholder="Your name">
    <input type="email" name="email" required>
    <input type="password" name="password">

    <!-- Text area -->
    <textarea name="message" rows="4" cols="50"></textarea>

    <!-- Checkbox and Radio -->
    <input type="checkbox" name="accept" id="accept">
    <label for="accept">I accept the terms</label>

    <input type="radio" name="gender" value="m">Male
    <input type="radio" name="gender" value="f">Female

    <!-- Select -->
    <select name="options">
        <option value="1">Option 1</option>
        <option value="2">Option 2</option>
    </select>

    <!-- Button -->
    <button type="submit">Submit</button>
</form>
```

## Semantic Elements
```html
<header>Page header</header>
<nav>Navigation menu</nav>
<main>Main content</main>
<article>Independent article</article>
<section>Content section</section>
<aside>Related content</aside>
<footer>Page footer</footer>
```

## Media Elements
```html
<!-- Video -->
<video controls width="500">
    <source src="video.mp4" type="video/mp4">
    Your browser does not support the video element.
</video>

<!-- Audio -->
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>
```

## Important Tips
1. Always use HTML5 basic structure in your documents
2. Maintain proper indentation for better readability
3. Use semantic elements for better SEO and accessibility
4. Always include alternative texts for images (alt attribute)
5. Validate your HTML using tools like W3C Validator