# Generating a PDF file with [Reportlab](https://www.youtube.com/watch?v=B3OCXBL4Hxs&list=PLOGAj7tCqHx-IDg2x6cWzqN0um8Z4plQT&index=2)
## Install reportlab
## Registering a custom font
```
#registering a new font (tt stands for truetype)
from reportlab.pdfbase.ttfonts import TTFont
from reportlab.pdfbase import pdfmetrics

pdfmetrics.registerFont(
	TTFont('abc', 'SakBundren.ttf')
)
pdf.setFont('abc, 36')
```

## Import libraries
```
from reportlab.pdfgen import canvas
pdf = canvas.Canvas(<filenname>)
pdf.setTitle(<document_title>)

# Registering font code goes here
 
pdf.setFont('Courier-Font', 24)
# args: coordinates, string to be written to the file
pdf.drawCenteredString(0,0, <string>)

pdf.save()
```

## Drawing lines
```
#Drawing a line
pdf.line(30,710, 550, 710)
```

## Writing multiple lines
```
# Writing text and filling color
from report.lib import colors

text = pdf.beginText(40,680)
text.setFont('Courier', 18)
text.setFillColor(colors.red)
for line in textLines:
	text.textLine(line)

```

## Inserting an image
```
# Inserting a image
pdf.drawInlineImage(<image_path>)
```

## Generating a table (pending)
```
from reportlab.platypus import SimpleDocTemplate, Table
from reportlab.lib.pagesizes import letter

# Input data is usually a list of lists
data = [
	['a', 'b', 'c', 'd'],
	['a', 'b', 'c', 'd'],
	['a', 'b', 'c', 'd']
]

# pdf data
filename = 'example_name.pdf'
pdf = SimpleDocTemplate(
	filename,
	pagesize=letter
)

# declaring the table and styles, etc
table = Table(data)

# Declaring the style 
from reportlab.platypus import TableStyle

# TableStyle requires args of tuples, which is usually a tuple
style = TableStyle([
	('BACKGROUND', (0,0), (3,0), colors.green),
	('TEXTCOLOR', (0,0), (-1,0), colors.whitesmoke),
	('ALIGN',(0,0),(-1,-1), 'CENTER')
	('FONTNAME', (0,0), (-1,0), 'Courier-Bold'),
	('FONTSIZE', (0,0), (-1,0), )
])

table.setStyle(style)

elems = []
elems.append(table)
pdf.build(elems)

```

# References
[Tutorials](https://www.reportlab.com/documentation/tutorial/#json-to-pdf-fund-report-tutorial)
[Reportlab opensource](https://www.reportlab.com/docs/reportlab-userguide.pdf)

## Tags
#guide #incomplete 