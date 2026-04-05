---
title: "Research on AI Ethics"  # Page title
image: /assets/images/header.png  # Banner image path
paper: https://example.com/paper1  # Link to paper
code: https://github.com/user/research1  # Link to code
date: 2023-01-01  # Publication date
categories: [tech, tutorial]  # Categories for organization
tags: [github, markdown]  # Tags for search
description: "A short summary of what this post is about for SEO and previews."  # Meta description
author: "Michel Torny"  # Author name
layout: default  # Layout to use
---

# Main Title (H1)

This is the main title of the page. Use H1 for the primary heading.

## Introduction (H2)

Welcome to this comprehensive Markdown template! This page includes all common elements you might need for a webpage. Feel free to copy and modify this template for your own use.

### Subsection (H3)

This is a subsection under the introduction. You can nest headings up to H6.

#### Sub-subsection (H4)

Even deeper nesting for detailed content.

##### H5

##### H6

## Text Formatting

You can format text in various ways:

- **Bold text** using double asterisks.
- *Italic text* using single asterisks.
- ***Bold and italic*** using triple asterisks.
- ~~Strikethrough text~~ using double tildes.
- `Inline code` using backticks.
- [Links](https://example.com) using brackets and parentheses.
- Footnotes[^1] for references.

[^1]: This is a footnote.

## Lists

### Unordered List

- Item 1
- Item 2
  - Nested item
  - Another nested item
- Item 3

### Ordered List

1. First item
2. Second item
   1. Nested ordered item
   2. Another nested
3. Third item

### Definition List

Term 1
: Definition of term 1.

Term 2
: Definition of term 2.

## Images

### Sample Image

<img src="/assets/images/header.png" alt="Sample Image" width="400" height="300">

Images are center-aligned by default.

## Tables

### Sample Data Table

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |
| Data 7   | Data 8   | Data 9   |

Tables are centered and have borders.

## Code

### Inline Code

Use `print("Hello, World!")` for inline code.

### Code Blocks

```python
def hello_world():
    # this is a comment
    print("Hello, GitHub Pages!")
    return "Success"
```

```javascript
function greet(name) {
    console.log("Hello, " + name);
}
greet("World");
```

```sql
SELECT id, name, email
FROM users
WHERE active = 1
ORDER BY name;
```

## Math Equations

### Sample Math Equation

$$ E = mc^2 $$

### Multiline Math Equation

$$
\begin{align}
\frac{d}{dx} \int_a^x f(t) \, dt &= f(x) \\
\int_a^b f(x) \, dx &= F(b) - F(a)
\end{align}
$$

Math is rendered using MathJax.

## Blockquotes

> This is a blockquote.
>
> It can span multiple lines.
>
>> Nested blockquote.

## Horizontal Rules

---

Above is a horizontal rule.

## Links and References

- [External Link](https://example.com)
- [Internal Link](#main-title-h1)

## Abbreviations

This is HTML, but for reference: <abbr title="HyperText Markup Language">HTML</abbr>

## Task Lists

- [x] Completed task
- [ ] Incomplete task
- [x] Another completed task

## Emojis

😀 ❤️ 👍

## HTML Elements

You can include raw HTML:

<button onclick="alert('Hello!')">Click Me</button>

<div style="background-color: lightblue; padding: 10px;">
  This is a styled div.
</div>

## Jekyll Specific

- Page title: {{ page.title }}
- Date: {{ page.date | date: "%B %d, %Y" }}
- Categories: {{ page.categories | join: ", " }}
- Tags: {{ page.tags | join: ", " }}

---

**{{ page.title }}**

## Interactive Charts and Visualizations

### Plotly Chart Example

<div id="plotly-chart" style="width: auto; height: 400px;"></div>
<script>
  var data = [{
    x: [1, 2, 3, 4, 5],
    y: [1, 4, 9, 16, 25],
    type: 'scatter',
    mode: 'lines+markers',
    name: 'Quadratic Function'
  }];

  var layout = {
    title: 'Interactive Chart Example',
    xaxis: { title: 'X Values' },
    yaxis: { title: 'Y Values' }
  };

  Plotly.newPlot('plotly-chart', data, layout, {responsive: true});
</script>


## Citations and References

### Academic Citations

This research builds upon previous work in machine learning [^1] and statistical analysis [^2].

[^1]: Smith, J. (2020). Machine Learning Fundamentals. Academic Press.
[^2]: Johnson, A., & Brown, B. (2019). Statistical Methods in Data Science. Springer.

### BibTeX Format

```bibtex
@article{smith2020ml,
  title={Machine Learning Fundamentals},
  author={Smith, John},
  journal={Journal of AI},
  year={2020},
  publisher={Academic Press}
}

@inproceedings{johnson2019stats,
  title={Statistical Methods in Data Science},
  author={Johnson, Alice and Brown, Bob},
  booktitle={Proceedings of the International Conference on Data Science},
  year={2019},
  organization={Springer}
}
```
