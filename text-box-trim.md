# Explainer for the CSS `text-box`, `text-box-trim`, and `text-box-edge` properties

## Table of Contents
{:toc}

## Introduction

The CSS Inline Level 3
[Trimming Leading Over/Under Text](https://drafts.csswg.org/css-inline-3/#leading-trim)
section defines two longhand properties, `text-box-trim` and `text-box-edge`,
and one shorthand property `text-box`.
These properties make finer control of vertical alignment of text possible.

## Use cases

[Describe in detail what problems end-users are facing, which this project is trying to solve. A
common mistake in this section is to take a web developer's or server operator's perspective, which
makes reviewers worry that the proposal will violate [RFC 8890, The Internet is for End
Users](https://www.rfc-editor.org/rfc/rfc8890).]

### Use case 1

The vertical position of text isn't visually interoperable across platforms,
due to different font metrics.

The rendering of
[this test page](https://tobireif.com/non_site_stuff/test_case_for_font_position_report_yet_another_font/)
on macOS (left) and Windows (right):
</style>
<p style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
  <img src="https://user-images.githubusercontent.com/80411/41592189-1b1b8ee4-73bc-11e8-9c21-9ff43ac2167f.png">
  <img src="https://user-images.githubusercontent.com/80411/41592204-25a82ae8-73bc-11e8-818d-d64216d9c480.png">
</p>

This use case diverged to
the [font metrics overrides discussion](https://github.com/w3c/csswg-drafts/issues/4792),
and partially resolved by adding
the [default font metrics overriding](https://drafts.csswg.org/css-fonts/#font-metrics-override-desc).
It addressed cross-platform visual interoperability,
but the desire for finer control such as seen in other use cases still remains.

### Use case 2

This example by Jan Nicklas explains various points of vertical alignments:
<p>
  <img src="https://lists.w3.org/Archives/Public/www-archive/2018Oct/att-0007/cgikdonhiondpafc.png">
</p>

When aligning the top of text to non-text objects,
[this comment explains](https://github.com/w3c/csswg-drafts/issues/3240#issuecomment-737374575) that
the desired "top of text" may vary:
<p style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
  <img src="https://user-images.githubusercontent.com/10702/100905587-89817b80-34c8-11eb-8454-57f48cdc2b00.gif">
  <img src="https://camo.githubusercontent.com/5776b249db46310818b54c8627639b90b5af53effc76a307bcd95dd1c6bd4cb1/68747470733a2f2f692e696d6775722e636f6d2f36416664496e6f2e706e67">
</p>

### Use case 3

Another common pain point today is vertical centering of text against non-text objects, such as:

<p style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
  <img src="https://camo.githubusercontent.com/6d251f2f9069238b80100319e95198207f58cf12cd593fed4765808a36e7cee7/68747470733a2f2f692e696d6775722e636f6d2f34514e4e6972582e706e67">
  <img src="https://user-images.githubusercontent.com/709153/47383751-38341a80-d6ba-11e8-8cc6-cde2417f0574.png">
</p>

[This video from Figma](https://x.com/figma/status/1640750882613493760)
demonstrates how Figma's implementation works.

Similar to the use case 2, the top of text could be the cap-height or the x-height,
depends on the text content.
The bottom of text is usually the alphabetic baseline for Latin,
but it's different for different writing systems.

### How this solution would solve the use cases

Please see the CSS Inline Level 3
[Trimming Leading Over/Under Text](https://drafts.csswg.org/css-inline-3/#leading-trim) section.

## Stakeholder Feedback / Opposition

- [Chromium] : Positive, [implementing](https://crbug.com/40254880)
- [WebKit] : Positive, available under a runtime flag
- [Microsoft Design] : [Positive](https://medium.com/microsoft-design/leading-trim-the-future-of-digital-typesetting-d082d84b202)
- [Figma] : Positive, [launched their implementation](https://forum.figma.com/t/launched-leading-trim/27039)
