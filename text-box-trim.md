# Explainer for the CSS `text-box`, `text-box-trim`, and `text-box-edge` properties

## Table of Contents
* Placeholder for Table of Content (Must not be removed)
{:toc}

## Introduction

To achieve optical balance of text content,
the [`text-box-trim`] and [`text-box-edge`] properties,
along with the shorthand property [`text-box`],
make finer control of vertical alignment of text possible.

They properties are defined in
the [Trimming Leading Over/Under Text] section of
the CSS Inline Level 3.

## Use cases

### Use case 1

[This example by Jan Nicklas](https://lists.w3.org/Archives/Public/www-archive/2018Oct/att-0009/00-part)
explains various points of vertical alignments:
<p>
  <img src="https://lists.w3.org/Archives/Public/www-archive/2018Oct/att-0007/cgikdonhiondpafc.png">
</p>

When aligning the top of text to non-text objects,
[this comment explains](https://github.com/w3c/csswg-drafts/issues/3240#issuecomment-737374575)
how the desired "top of text" may vary:
<p style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
  <img src="https://user-images.githubusercontent.com/10702/100905587-89817b80-34c8-11eb-8454-57f48cdc2b00.gif">
  <img src="https://camo.githubusercontent.com/5776b249db46310818b54c8627639b90b5af53effc76a307bcd95dd1c6bd4cb1/68747470733a2f2f692e696d6775722e636f6d2f36416664496e6f2e706e67">
</p>

Note, the rules in the picture above may vary
depends on preferences of authors or writing systems.
For example, the "top of text" may vary by text content or by preferences.
Also, other writing systems may prefer other "top of text" and "bottom of text".

### Use case 2

Another common pain point today is vertical centering of text against non-text objects, such as:

<p style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
  <img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*dpO-Wj1WJkUhfMJo6b16Nw.png">
  <img src="https://user-images.githubusercontent.com/709153/47383751-38341a80-d6ba-11e8-8cc6-cde2417f0574.png">
</p>

[This video from Figma](https://x.com/figma/status/1640750882613493760)
demonstrates how the their implementation solves this use case.

Similar to the use case above, the "top of text" could be the cap-height or the x-height,
depends on the text content or on the authors' preferences.
The bottom of text is usually the alphabetic baseline for Latin,
but they may be different for different writing systems.

### How this solution would solve the use cases

The following CSS is a simple example for the use cases above for the Latin writing systems:
```css
.trim-at-cap {
  text-box: cap alphabetic;
}

.trim-at-ex {
  text-box: ex alphabetic;
}
```

For more details, please see
the [`text-box`] shorthand property,
along with the [`text-box-trim`] and [`text-box-edge`] longhand properties
in the [Trimming Leading Over/Under Text] section of the CSS Inline Level 3.


## Stakeholder Feedback / Opposition

- [Chromium] : Positive, [available as Experimental Web Platform features](https://crbug.com/40254880).
- [WebKit] : Positive, available under a runtime flag.
- [Microsoft Design] : Positive, published [an article](https://medium.com/microsoft-design/leading-trim-the-future-of-digital-typesetting-d082d84b202).
- [Figma] : Positive, [launched their implementation](https://forum.figma.com/t/launched-leading-trim/27039).

[Trimming Leading Over/Under Text]: https://drafts.csswg.org/css-inline-3/#leading-trim
[`text-box`]: https://drafts.csswg.org/css-inline-3/#propdef-text-box
[`text-box-edge`]: https://drafts.csswg.org/css-inline-3/#propdef-text-box-edge
[`text-box-trim`]: https://drafts.csswg.org/css-inline-3/#propdef-text-box-trim
