HtmlEditor is a client-side WYSIWYG editor that allows users to format text and visual content, and to export it as HTML or Markdown. Supported features include:

- [Inline Formats](/concepts/05%20UI%20Components/HtmlEditor/10%20Formats '/Documentation/Guide/UI_Components/HtmlEditor/Formats/'):
    - **Bold**, *italic*, <s>strikethrough</s>, and <u>underscore</u> text formatting attributes
    - Typeface, font size, and text color changes (HTML only)
- [Block Formats](/concepts/05%20UI%20Components/HtmlEditor/10%20Formats '/Documentation/Guide/UI_Components/HtmlEditor/Formats/'):
    - Headers
    - Lists (ordered and unordered)
    - Code blocks
    - Quotes
- [Built-in Format Customization](/concepts/05%20UI%20Components/HtmlEditor/10%20Formats/33%20Customize%20Built-In%20Formats%20and%20Modules '/Documentation/Guide/UI_Components/HtmlEditor/Formats/#Customize_Built-In_Formats_and_Modules')
- [HTML and Markdown Support](/concepts/05%20UI%20Components/HtmlEditor/00%20Getting%20Started%20with%20HtmlEditor/10%20Set%20the%20Output%20Markup%20Language.md '/Documentation/Guide/UI_Components/HtmlEditor/Getting_Started_with_HtmlEditor/#Set_the_Output_Markup_Language')
- [Mail Merge](/api-reference/10%20UI%20Components/dxHtmlEditor/1%20Configuration/variables '/Documentation/ApiReference/UI_Components/dxHtmlEditor/Configuration/variables/')
- [Adaptive Toolbar](/concepts/05%20UI%20Components/HtmlEditor/00%20Getting%20Started%20with%20HtmlEditor/20%20Configure%20the%20Toolbar.md '/Documentation/Guide/UI_Components/HtmlEditor/Getting_Started_with_HtmlEditor/#Configure_the_Toolbar') designed to work with images, links, and color formats.
- Image upload: drag-and-drop images onto the form, select files from the file system, or specify a URL.
- Copy-paste rich content (the control automatically removes unsupported text formatting attributes).
- [Mentions](https://js.devexpress.com/Demos/WidgetsGallery/Demo/HtmlEditor/Mentions/) (@person, for example)
- [Tables](/concepts/05%20UI%20Components/HtmlEditor/00%20Getting%20Started%20with%20HtmlEditor/30%20Work%20with%20Tables.md '/Documentation/Guide/UI_Components/HtmlEditor/Getting_Started_with_HtmlEditor/#Work_with_Tables')

## How to Use HTMLEditor

HtmlEditor is designed to create rich text and export it in HTML or Markdown format. You can also use the component to parse HTML content (for example, if you set [value](/api-reference/10%20UI%20Components/dxHtmlEditor/1%20Configuration/value.md '/Documentation/ApiReference/UI_Components/dxHtmlEditor/Configuration/#value') to markup). However, this technique may prove ineffective because HtmlEditor does not support all HTML features. The following limitations apply:

- If you use <a href="https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_shadow_DOM" target="_blank">Shadow DOM</a>, the HtmlEditor component may experience issues in some browsers (see <a href="https://developer.mozilla.org/en-US/docs/Web/API/ShadowRoot#browser_compatibility" target="_blank">getSelection</a>).

- HtmlEditor does not produce a fully-structured HTML document with `<!DOCTYPE>`, `<head>`, and `<body>` tags. The editor is meant to export simple markup that contains formatted rich content for an article, forum post, etc.

- HtmlEditor saves only a limited subset of [tags and attributes](/concepts/05%20UI%20Components/HtmlEditor/05%20Tags%20and%20Attributes.md '/Documentation/Guide/UI_Components/HtmlEditor/Tags_and_Attributes/'). All other formatting attributes and features are discarded.

- HtmlEditor automatically removes redundant tags:

        <!-- from -->
        <p><span>He</span><em><span>llo</span></em></p>

        <!-- to -->
        <p>He<em>llo</em></p>

- HtmlEditor trims extra space and tab characters passed to the [value](/api-reference/10%20UI%20Components/dxHtmlEditor/1%20Configuration/value.md '/Documentation/ApiReference/UI_Components/dxHtmlEditor/Configuration/#value') option.

- The component is not designed to convert text enclosed in curly brackets (`{}`) to a variable. Content in curly brackets is always treated as plain text.

- The HtmlEditor tables are native HTML tables and use native features; therefore, the same limitations apply. For example, users cannot paste multiline text in separate cells.

- The HtmlEditor tables do not support complex elements in cells, such as block elements, lists, nested tables, etc.

- HtmlEditor does not support complex clipboard data formats of HTML pages and text processor applications, such as Microsoft Word®.

- HtmlEditor does not support [CSP](/concepts/Common/Security%20Considerations/40%20Content%20Security%20Policy/00%20Content%20Security%20Policy.md '/Documentation/Guide/Common/Security_Considerations/#Content_Security_Policy'). If you want to pass markup that contains inline styles to HtmlEditor [value](/api-reference/10%20UI%20Components/dxHtmlEditor/1%20Configuration/value.md '/Documentation/ApiReference/UI_Components/dxHtmlEditor/Configuration/#value'), use `style-src 'unsafe-inline';` directive to avoid errors.