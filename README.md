# 🕴️ style-guides
Sensible styles guides for programming languages I use

## Table of Contents

* [Python](#python)
* [R](#r)
* [SQL](#sql)
* [JavaScript](#js)
* [Clojure](#clojure)
* [Stan](#stan)
* [Files](#filenames)


> [A foolish consistency is the hobgoblin of little minds](https://www.python.org/dev/peps/pep-0008/#a-foolish-consistency-is-the-hobgoblin-of-little-minds)


Every now and then a pretty bad case of OCD unfortunately rears its ugly head in my life.
Given that I spend a decent amount of my life programming, it is often most notable for me
in this context. Struggling with getting the look of code to "feel" right is occasionally
a challenge. The following style guides have come in quite handy to help me not have to
deal with this nonsense.

<a name="python">

### Python

* [PEP 8](https://www.python.org/dev/peps/pep-0008/)
* [The Elements of Python Style](https://github.com/amontalenti/elements-of-python-style) aims to provide a "Strunk and White for Python"
* [Craft Your Python Like Poetry](https://treyhunner.com/2017/07/craft-your-python-like-poetry/)
* [The Unreasonable Effectiveness of Method Chaining in Pandas](https://towardsdatascience.com/the-unreasonable-effectiveness-of-method-chaining-in-pandas-15c2109e3c69)
* [Pandas Docstring Guide](https://pandas.pydata.org/docs/development/contributing_docstring.html)
* [NumPy Docstring Guide](https://numpydoc.readthedocs.io/en/latest/format.html)
* [Readability Counts](https://www.youtube.com/watch?v=knMg6G9_XCg&feature=youtu.be&t=)
* [How to Write Beautiful Python Code with PEP 8](https://realpython.com/python-pep8/)

PEP 8 [recommends](https://www.python.org/dev/peps/pep-0008/#should-a-line-break-before-or-after-a-binary-operator) the following:

```python
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

My preference is instead:

```python
income = (
    gross_wages
    + taxable_interest
    + (dividends - qualified_dividends)
    - ira_deduction
    - student_loan_interest
)
```

These extends to method chaining, where my preference is for "aligning
dots." Taking an example from
[Tom Augspurger's "Modern Pandas" blog post series](https://tomaugspurger.github.io/method-chaining.html),
I'd rewrite this:

```python
flights_daily = (df.dropna(subset=['dep_time', 'unique_carrier'])
                 .loc[df['unique_carrier']
                 .isin(df['unique_carrier'].value_counts().index[:5])]
                 .set_index('dep_time')
                 .groupby(['unique_carrier', pd.TimeGrouper("H")])
                 .fl_num.count()
                 .unstack(0)
                 .fillna(0)
                 .rolling(24)
                 .sum()
                 .rename_axis("Flights per Day", axis=1))
```
As this:

```python
flights_daily = (
    df.dropna(subset=['dep_time', 'unique_carrier'])
      .loc[df['unique_carrier'].isin(df['unique_carrier'].value_counts().index[:5])]
      .set_index('dep_time')
      .groupby(['unique_carrier', pd.TimeGrouper("H")])
      .fl_num.count()
      .unstack(0)
      .fillna(0)
      .rolling(24)
      .sum()
      .rename_axis("Flights per Day", axis=1)
)
```

Again, this is subjective, but I just like the alignment.

#### Additional Resources

* [Beyond PEP 8: Best Practices for Beautiful Intelligible Code](https://www.youtube.com/watch?v=wf-BqAjZb8M)
* [Readability Counts](https://www.youtube.com/watch?v=knMg6G9_XCg)


<a name="r">

### R

If you're programming in R, just use the style adopted by tidyverse developers. Full stop.

* [The Tidyverse Style Guide](https://style.tidyverse.org/)
* Rasmus Bååth's talk on [The State of Naming Conventions in R](http://sumsar.net/files/academia/UseR_2013_R_naming_conventions_final.pdf) if worth a look


<a name="js">

### JavaScript

* [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)
* [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)


<a name="clojure">

### Clojure

* [The Clojure Style Guide](https://guide.clojure.style/)
* [Metabase Clojure Style Guide](https://github.com/metabase/metabase/wiki/Metabase-Clojure-Style-Guide)


<a name="sql">

### SQL

I've had a hate-hate relationship with SQL style for years, and have yet
to find a style guide that just works for me (e.g., like the tidyverse
style for R programming).

However, one thing I feel **very strongly** about is that this:

```sql
select
    user_id
    , first_name
    , last_name
    , age
from user_table
```

is way better than this:

```sql
select
    user_id,
    first_name,
    last_name,
    age
from user_table
```

The second is the visual equivalent of fingernails on the chalkboard for me.

* [SQL Style Guide](https://docs.telemetry.mozilla.org/concepts/sql_style.html) from Firefox Data Documentation

Another strong preference I have relates to CTEs.

```sql
-- Good
with
first_cte as (
  ...
)
, second_cte as (
  ...
)
select ...

-- Bad
with first_cte as (
  ...
),
second_cte as (
  ...
)
select ...
```

Put the `WITH` on its own line, and put the `,` separating CTEs before
the CTE name.

I prefer this style of SQL because, when I'm developing queries, I typically
always know the first few columns that I want to select and will be adding some
"maybe these'll be useful" columns at the end. I'll often find myself deleting
the last few columns when finalizing the query. With what I consider
"fingernails-on-chalkboard" queries, I'll often forget to remove the trailing comma,
which will cause me to run a query with invalid syntax. This is avoided in the what I
consider to be good style, saving myself a few seconds of fixing my syntax error. The
same goes for the CTEs.


#### Additional Resources

* [SQL Style Guide](https://docs.telemetry.mozilla.org/concepts/sql_style.html) from Firefox Data Documentation
* GitLab's [SQL Style Guide](https://about.gitlab.com/handbook/business-ops/data-team/platform/sql-style-guide/)


<a name="stan">

### Stan

* [Stan Program Style Guide](https://mc-stan.org/docs/2_22/stan-users-guide/stan-program-style-guide.html)


<a name="filenames">

### Files

> File organization and naming are powerful weapons against chaos.
>
> --- [@JennyBryan](https://twitter.com/JennyBryan)

* [Naming Things](https://speakerdeck.com/jennybc/how-to-name-files)
* [File Organization: Naming](https://datacarpentry.org/rr-organization1/01-file-naming/) from Data Carpentry
* [Best Practices for File Naming](https://records-express.blogs.archives.gov/2017/08/22/best-practices-for-file-naming/) from the National Archives Records Express
* [Names](https://style.tidyverse.org/files.html#names) in The Tidyverse Style Guide
* [Better Naming Convention for Jupyter Notebook](https://stackoverflow.com/questions/38305217/better-naming-convention-for-jupyter-notebook)


### Code Comments

* Good Twitter thread started by [@drewconway](https://twitter.com/drewconway/status/1234840750275342338)
on Markdown vs. code comments in Jupyter notebooks


### Makefiles

* [Makefile Style Guide](https://clarkgrubb.com/makefile-style-guide)


### YAML

* [YAML Style Guide](https://github.com/flathub/flathub/wiki/YAML-Style-Guide)


### Further Reading

* [The Art of Readable Code: Simple and Practical Techniques for Writing Better Code](https://www.oreilly.com/library/view/the-art-of/9781449318482/)
