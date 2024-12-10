## 1E9 Style Guide for UI (HTML + CSS + Bootstrap 5.x) 

### Organization

### Fonts

```css
body {
  font-family: "Inter", sans-serif;
}
```

### Alignment

#### Vertical Alignment

- Middle Align: Default
- Top Align: If there is wrapping text in any cell in the table
- Bottom Align: !Never

#### Horizontal Alignment

- Avoid text that wraps unless unavoidable
- Text should always be left-aligned
- Numbers should always be right-aligned
- Dates should be left-aligned by default and may be center aligned if appropriate

## Formats

| Content     | Format                                |
| ----------- | ------------------------------------- |
| Year (int)  | `0000_)`                              |
| Year (date) | `yyyy_)`                              |
| Date        | `YYYY-MM-DD`                          |
| Number      | `font-variant-numeric: tabular-nums;` |

