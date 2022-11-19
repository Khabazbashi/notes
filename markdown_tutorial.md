# markdown_tutorial
<!-- This content will not appear in the rendered Markdown -->

## Table of Contents
- [Headings](#heading-1)
- [Text styling](#text-styling)
- [Links](#links)
- [Escape characters](#escape-special-characters)
- [Lists](#lists)
- [Tables](#tables)
- [Code](#code)
- [Icons](#icons)
- [Images](#images)
- [Footnotes](#footnotes)
- [Subscript and superscript](#subscript-and-superscript)
- [Collapsible markdown](#collapsible-markdown)

## Heading 2
### Heading 3
##### Heading 4
###### Heading 5


## Text styling
*This text* is italic

_This text_ is also italic

**This text** is strong

__This text__ is also strong

***This text*** is strong and italic 

~~This text~~ is strikethrough

> This is a quote.

## Links
Visit [this very special link](https://mynoise.net/noiseMachines.php "Enjoy the music") or why not visit this link https://github.com.


## Escape special characters
Use backslash "\\" to escape characters with special meaning like | or *. 


## Lists
- Item 1
+ Item 2
*
* Item 3
    * Nested Item 1
        - Nested item 2

___

1. Item 1

        List item1 with indented block.

2. Item 2
3. Item 3

***

- [x] #739
- [x] https://github.com/octo-org/octo-repo/issues/740
- [ ] Add delight to the experience when all tasks are complete :tada:


## Tables
| Heading1 | Heading2 | Heading3 |
| :---  | :---  | :---: |
| `Something` | Lorem ipsum dolor sit amet, *consectetur* adipiscing elit. | Ok |
| `Something` | Quisque viverra mi nec ligula molestie, **id tincidunt** justo dapibus.  | Ok |
| `Dark side` | ` | Ok |
| `Escape this pipe` | \| | Escaped


## Code
```bash
    npm install
    npm start
```

```javascript
    function add(num1, num2) {
        return num1 + num2;
    }
```

```csharp
    public int GetSum(int num1, int num2)
    {
        return num1 + num2
    }
```
Also possible to write `<p>inline code block</p>`.


## Icons
| icon | shortcode |
| - | :- |
| :link: | `:link:`  |
| :paperclip: |  `:paperclip:` |
| :envelope: |  `:envelope:` |
|:date:  | `:date:` |
| :wrench:  | `:wrench:` |
| :bulb:  | `:bulb:` |
| :key:  | `:key:` |
| :bust_in_silhouette: |  `:bust_in_silhouette:` |
| :wave:  | `:wave:` |
| :round_pushpin:  | `:round_pushpin:` |
| :hammer_and_wrench: |  `:hammer_and_wrench:` |
| :syringe:  | `:syringe:` |
| :pencil2:  | `:pencil2:` |
| :white_check_mark: |  `:white_check_mark:` |
| :link:  | `:email:` |


## Images
![AltText](./images.png)


## Footnotes
Here's a simple footnote,[^1] and here's a longer one.[^bignote]
[^1]: This is the first footnote.
[^bignote]: Here's one with multiple paragraphs and code.
    Indent paragraphs to include them in the footnote.
    `{ my code }`
    Add as many paragraphs as you like.


## Subscript and Superscript
And so it was indeed: she was now only $_{ten\ inches\ high}$, and her face brightened  up at the thought that she was now the right size for going through the little door into that lovely $^{garden}$.
H<sub>2</sub>O
H<sup>2</sup>O


## Collapsible markdown
<details>
<summary>Hide text</summary>
<p>
    Hidden text
<p>
</details>


