# Markdig.SemanticUi

Extension to use SemanticUi classes with Markdig.

* Adds `ui table` to table elements (when the advanced extension is also used)
* Adds `ui spaced image` to images

## Examples

Images

``` csharp
const string markdown = "My image ![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)";
const string expected = "<p>My image <img src=\"https://octodex.github.com/images/yaktocat.png\" class=\"ui spaced image\" alt=\"Image of Yaktocat\" /></p>\n";

var pipeline = new MarkdownPipelineBuilder()
    .UseAdvancedExtensions()
    .UseSemanticUi()
    .Build();
var result = Markdown.ToHtml(markdown, pipeline);
result.ShouldBe(expected);
```

Tables

``` csharp
const string markdown = @"First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column";

const string expected = @"<table class=""ui table"">
<thead>
<tr>
<th>First Header</th>
<th>Second Header</th>
</tr>
</thead>
<tbody>
<tr>
<td>Content from cell 1</td>
<td>Content from cell 2</td>
</tr>
<tr>
<td>Content in the first column</td>
<td>Content in the second column</td>
</tr>
</tbody>
</table>
";

var pipeline = new MarkdownPipelineBuilder()
    .UseAdvancedExtensions()
    .UseSemanticUi()
    .Build();
var result = Markdown.ToHtml(markdown, pipeline);
result.ShouldBe(expected);
```
