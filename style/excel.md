## 1E9 Style Guide for Excel 

### Organization

Organize the Report into Sections [Tabs].

Aggregation tabs should always have the same set of rows and in the same place across all copies

Detailed information should be on separate tabs; row headings may vary on a case by case basis for detailed information

### Fonts

Always use `Arial` in `10pt`

### Cell Size

- Row Width: 20 pixels
- Column Width: 75 pixels (11.67)

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

| Content | Format |
| ------- | ------ |
| Year (int) | `0000_)` |
| Year (date) | `yyyy_)` |
| Date | `YYYY-MM-DD` |
| Number | `_(* #,##0.00_);[Red]_(* (#,##0.00);_(* "-"??_);_(@_)` |

