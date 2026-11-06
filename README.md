<div align="center">

<img src="assets/siq-benchmark-bar-chart-v2.png" alt="SIQ Benchmark Bar Chart icon" width="96">

# SIQ Benchmark Bar Chart

**A custom Power BI chart that brings actual performance and benchmarks together.**

![Version 1.1.0.0](https://img.shields.io/badge/version-1.1.0.0-2563EB)
![Power BI custom visual](https://img.shields.io/badge/Power%20BI-custom%20visual-F2C811?logo=powerbi&logoColor=black)
![MIT licence](https://img.shields.io/badge/licence-MIT-64748B)

[**Download the visual**](https://github.com/gabechisholm/Overlay-Benchmark-Bar-Chart/releases) · [Quick start](#-try-it-with-sales-and-targets) · [Features](#-features) · [Formatting](#-formatting-options) · [Changelog](CHANGELOG.md)

</div>

---

Compare sales against targets, costs against budgets, or results against a previous period. Overlay actual columns on benchmark columns so readers can see the result and its reference value together. Add a sub-category to compare products within each region, then use colours and labels to make differences easy to spot.

| When you want to… | Use… |
|---|---|
| See how results compare with a target | **Overlaid actual and benchmark columns** with separate widths and colours |
| Compare products within a region | A **sub-category** to group columns within each base category |
| Highlight performance against the benchmark | **Conditional colours** for at-or-above and below-benchmark values |
| Apply your own business rules | **DAX colour measures** for actual bars and data-label text |

> [!NOTE]
> **New in 1.1.0.0** — Style presets, conditional colours, per-series data-label formatting, label backgrounds, and consistent SIQ font and number controls. See the [Changelog](CHANGELOG.md) for release details.

---

## 📦 Installation

1. Download the latest `SIQ-Benchmark-Bar-Chart-v{version}.pbiviz` file from the [Releases](https://github.com/gabechisholm/Overlay-Benchmark-Bar-Chart/releases) page, or build it using the commands below.
2. Open **Power BI Desktop** or **Power BI Service**.
3. In the **Visualizations** pane, click **···** (More options) → **Import a visual from a file**.
4. Choose the downloaded `.pbiviz` file.

---

## 🚀 Try it with sales and targets

| **Base Category** | **Sub-Category** | **Actual Target Value** | **Benchmark Comparison Value** |
| :---: | :---: | :---: | :---: |
| Region | Product (optional) | Sales | Sales Target |

1. Add **Region**, **Sales**, and **Sales Target** to the matching fields in **Build visual**. Add **Product** for a breakdown within each region.
2. Open **Format visual → Columns** and set the actual and benchmark colours and widths so both values are easy to distinguish.
3. Under **Conditional colours**, set **Colour mode** to **At or above / below benchmark** and choose the two colours.
4. Enable **Data labels** and **Benchmark labels** to show the values directly on the chart.

> [!TIP]
> Start with **Layout and style presets → Minimal** for a simpler presentation, or **Contrast** for stronger visual separation.

## 🗂 Adding Data

Add your fields in the **Build visual** pane. **Sub-Category** and **Colour measures** are optional.

| Role | Description |
|---|---|
| **Base Category (e.g. Region)** | Categories along the X-axis |
| **Sub-Category (e.g. Products)** | Series to compare within each base category |
| **Actual Target Value** | Numeric measure for the actual result, such as sales |
| **Benchmark Comparison Value** | Numeric reference measure, such as a target, budget, or prior-period result |
| **Colour measures (optional)** | Measures returning hex colours for actual bars or data-label text |

---

## ✨ Features

### 🎯 Compare performance

* **Overlaid Columns**: Show actual and benchmark values together, with independent widths, colours, and transparency.
* **Grouped Series**: Break each base category into sub-categories for more detailed comparisons.
* **Positive and Negative Values**: Actual columns and their labels use the zero baseline for positive and negative results.
* **Benchmark Labels**: Display reference values with a custom prefix, font, colour, display units, and decimal places.

### 🎨 Make results stand out

* **3 Style Presets**: Choose `Default`, `Minimal`, or `Contrast` as a starting point.
* **Conditional Colours**: Colour actual bars by sign or by whether they meet the benchmark.
* **Colour Measures**: Use DAX to drive actual-bar colours and data-label font colours.
* **Per-Series Styling**: Customise column styling and data-label fonts and colours for individual series, or base categories when there are no series.
* **Label Backgrounds**: Add a background with its own colour, transparency, corner radius, and padding.

### 🔎 Read and explore

* **Tooltips**: Hover over actual or benchmark columns to inspect values.
* **Power BI Selection**: Select actual columns and open the Power BI context menu.
* **Flexible Axes**: Wrap unrotated category labels, rotate labels, customise titles, and set Y-axis bounds.
* **Number Formatting**: Choose display units and decimal places independently for data labels, benchmark labels, and the Y-axis.

---

## 🎨 Formatting Options

| In **Format visual**, open… | To customise… |
|---|---|
| **Layout and style presets** | Choose `Default`, `Minimal`, or `Contrast`. |
| **Legend** | Set visibility, position, title, font, and font colour. |
| **X-axis** | Set label visibility, font, rotation, word wrap, label offset, padding, and title. |
| **Y-axis** | Set labels, display units, decimal places, title, axis position, axis line, start/end values, and padding. |
| **Gridlines** | Set visibility, colour, transparency, line style, thickness, and scaling by width. |
| **Columns** | Select a series or base category; set actual and benchmark colours, transparency, borders, widths, and spacing. |
| **Data labels** | Set fonts and colours by series or base category; set shared number formatting, position, and background styling. |
| **Benchmark labels** | Set visibility, prefix, number formatting, font, and font colour. |
| **Chart padding** | Set the top, right, bottom, and left margins around the plot. |
| **Conditional colours** | Choose a value or benchmark rule, its colours, and optional colour measures. |

> [!TIP]
> Presets supply defaults. Explicitly saved formatting takes precedence; reset an individual formatting card to use its preset defaults again.

<details>
<summary><strong>Number formatting and label backgrounds</strong></summary>

Choose **Auto**, **None**, **Thousands**, **Millions**, or **Billions** for display units. Existing custom numeric divisors remain supported. Decimal places accept **0–10**; clear the input for **Auto**, which retains significant digits without unnecessary trailing zeros.

Under **Data labels → Background**, transparency runs from **0%** (opaque) to **100%** (transparent). Corner radius and padding use pixels. Background transparency does not affect the label text.

The **Apply settings to series** selection is shared between **Columns** and **Data labels**. Label number formatting, position, and backgrounds apply to all labels. X-axis word wrap applies to unrotated labels; rotated labels stay on one line.

</details>

---

## 🎨 Conditional Colours

For built-in rules, open **Conditional colours → Colour mode** and choose **Positive / negative** or **At or above / below benchmark**. Rules affect actual bars.

For custom rules, add a DAX measure returning a hex colour such as `"#2D7DD2"` or `BLANK()` to **Colour measures (optional)** in **Build visual**. Select it under **Bar colour from measure**, **Font colour from measure**, or both.

For example, with measures named `[Sales]` and `[Sales Target]`:

```dax
Performance Colour =
IF (
    ISBLANK ( [Sales] ) || ISBLANK ( [Sales Target] ),
    BLANK (),
    IF ( [Sales] >= [Sales Target], "#16A34A", "#DC2626" )
)
```

Measure colours take precedence over conditional rules, which take precedence over normal series colours. Missing or invalid colour results fall back to the rule or normal styling.

> [!NOTE]
> Power BI high-contrast mode takes precedence over custom bar and label colours.

---

## 🛠 Build and Validation

Install dependencies and start the development visual:

```sh
npm install
npm start
```

With the Power BI visuals CLI (`pbiviz`) available, run the checks and create the package:

```sh
npm test
npx tsc --noEmit
npm run package
```

The packaged visual is written to `dist/SIQ-Benchmark-Bar-Chart-v{version}.pbiviz`, using the version in `pbiviz.json`.

---

## 🏢 Author

Made by **[Gabe Chisholm](https://www.linkedin.com/in/gabe-chisholm/)** at [SynapsysIQ](https://www.synapsysiq.co.uk/)

---

## 📄 License

MIT

---

## 💬 Want a dashboard with this functionality and more?

Bring actual-versus-target comparisons like SIQ Benchmark Bar Chart into a Power BI dashboard built around how your team works. From tracking sales targets to comparing budgets and exploring performance, get in touch to discuss what your dashboard could do. [Visit SynapsysIQ](https://www.synapsysiq.co.uk/)
