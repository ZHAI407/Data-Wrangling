Building blocks
================
Boran Zhai
2025-12-22

# Getting started and best practices

this code does variable assignments!

``` r
x = runif(n = 20)    # Generate 20 random numbers
y = c(1,3,17,25)

mean(x)
```

    ## [1] 0.525983

``` r
var(x)
```

    ## [1] 0.1363061

## data frames

tibble() \# create a dataframe

#### First example of dataframe

``` r
library(tidyverse)

example_df = tibble(
  vec_numeric = 1:4,
  vec_char = c("Jack","Jeff","Lily","Sam"),
  vec_factor = factor(c("male","male","famale","male"))
)

example_df
```

    ## # A tibble: 4 × 3
    ##   vec_numeric vec_char vec_factor
    ##         <int> <chr>    <fct>     
    ## 1           1 Jack     male      
    ## 2           2 Jeff     male      
    ## 3           3 Lily     famale    
    ## 4           4 Sam      male

## make a df; and some plots!!

``` r
plot_df = tibble(
  x = rnorm(1000, sd = 0.5),       # draw 1000 from normal distribution
  y = 1 + 2 * x + rnorm(1000),      # add noise
  y_quad = 1 + 2 * x - 3 * x ^ 2 +rnorm(1000)
  )

ggplot(plot_df, aes(x = x)) + geom_histogram()     
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Building-blocks_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
# first thing is what data set, second is what I put in x-axis, and than going to say what kind of polt I want to draw

ggplot(plot_df, aes(x = x, y = y_quad)) + geom_point()
```

![](Building-blocks_files/figure-gfm/unnamed-chunk-3-2.png)<!-- -->

``` r
plot_df = tibble(
  x = rnorm(1000, sd = 0.5),       # draw 1000 from normal distribution
  y = 1 + 2 * x + rnorm(1000),      # add noise
  y_quad = 1 + 2 * x - 3 * x ^ 2 +rnorm(1000)
  )

ggplot(plot_df, aes(x = x)) + geom_histogram()     
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Building-blocks_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
ggplot(plot_df, aes(x = x, y = y_quad)) + geom_point()
```

![](Building-blocks_files/figure-gfm/unnamed-chunk-4-2.png)<!-- -->

# Writing with data

I am on R Markdown document!

## Section 1

Here’s a **code chunk** that samples from a *normal distribution*:

tips: “\*\* \*\*” make words bold, and “\_ \_” make words italicized

``` r
samp = rnorm(100)
length(samp)
```

    ## [1] 100

## Section 2

I can take the mean of the sample, too! The mean is 0.1291096. (Inline R
code)

### Code chunk options

give code chunk name in {r xxx};

echo = FALSE：code will be executed but not displayed; results are
included.

eval = FALSE：code will be displayed but not executed; results are not
included.;

include = FALSE: code won’t be executed or displayed;

message = FALSE：隐藏 package 启动等 message;

warning = FALSE：隐藏 warning 警告信息;

collapse = TRUE：把代码和输出合并显示在同一个代码块中output will be
collapsed into a single block at shown at the end of the chunk.

results = “hide”：代码运行，但文本输出不显示（图还会显示）;

fig.show = “hide”：代码运行，但图不显示（文本结果还显示）;

fig.width = 6：设置图的宽度（英寸）; fig.height =
4：设置图的高度（英寸）;

fig.cap = “…”：给图加 caption（论文/报告常用）;

cache = TRUE：缓存运行结果，加快重新 knit;

error = TRUE：即使出错也继续 knit 文档. errors in code will stop
rendering when FALSE; errors in code will be printed in the doc when
TRUE. The default is FALSE and you should almost never change it;

child = “other.Rmd”：把另一个 Rmd 当子文档插入;

out.width = “70%”：控制图在页面中的显示宽度

![](Building-blocks_files/figure-gfm/plot_example-1.png)<!-- -->

This plot is really great! It shows a linear relation just as expected.

The data frame has 500 rows. (Inline R code)

## Formatting text

section heading: \# \## \### \####

make things bold: **bold** or **bold**

italicized: *italic* or *italic*

`code`

superscript <sup>2</sup> 上标and subscript<sub>2</sub> 下标

Here is a list:

- Bulleted list item 1

- Item 2

  - Item 2a

  - Item 2b

1.  Numbered list item 1

2.  Item 2. The numbers are incremented automatically in the output.

Here is for links and images:

<http://example.com>

[R Markdown cheatsheet](https://r4ds.had.co.nz/r-markdown.html)

<figure>
<img src="path/to/img.png" alt="optional caption text" />
<figcaption aria-hidden="true">optional caption text</figcaption>
</figure>

Here is a table:

| First Header | Second Header |
|--------------|---------------|
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |

| Col 1 | Col 2 | Col 3 |
|-------|-------|-------|
| a     | b     | c     |
| d     | e     | f     |

> This is a block quote.

## Output formats

### 1. html_document

output:

html_document:

    toc: true              # 生成目录

    toc_depth: 3           # 目录显示到第几级标题

    toc_float: true        # 目录浮动在侧边

    code_folding: hide     # 代码默认折叠

    number_sections: true  # 标题自动编号

    theme: flatly          # 页面主题

    highlight: textmate    # 代码高亮

    df_print: paged        # 数据框分页显示（HTML 特有）

    fig_caption: true      # 启用图注

### 2. pdf_document

output:

pdf_document:

    toc: true

    number_sections: true

    fig_caption: true

    keep_tex: true         # 保留中间 tex 文件（调试用）

### 3. word_document

output:

word_document:

    toc: true

    fig_caption: true

    reference_docx: custom.docx  # 自定义 Word 样式（可选）

### 4. github_document（GitHub README）

output:

github_document:

    html_preview: false

### 5. beamer_presentation（PPT，PDF）

output:

beamer_presentation:

    theme: Madrid

    colortheme: dolphin

    toc: true
