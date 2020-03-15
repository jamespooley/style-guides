# 🕴️ style-guides
Sensible styles guides for programming languages I use


><sup>[A foolish consistency is the hobgoblin of little minds](https://www.python.org/dev/peps/pep-0008/#a-foolish-consistency-is-the-hobgoblin-of-little-minds)</sup>


Every now and then a pretty bad case of OCD unfortunately rears its ugly head in my life.
Given that I spend a decent amount of my life programming, it is often most notable for me
in this context. Struggling with getting the look of code to "feel" right is occasionally
a challenge. The following style guides have come in quite handy to help me not have to
deal with this nonsense.


### Python

* [PEP 8](https://www.python.org/dev/peps/pep-0008/)
* [Craft Your Python Like Poetry](https://treyhunner.com/2017/07/craft-your-python-like-poetry/)
* [Pandas Docstring Guide](https://pandas.pydata.org/docs/development/contributing_docstring.html)
* [NumPy Docstring Guide](https://numpydoc.readthedocs.io/en/latest/format.html)


### R

If you're programming in R, just use the style adopted by tidyverse developers. Full stop.

* [The Tidyverse Style Guide](https://style.tidyverse.org/)


### JavaScript

* [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)
* [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)


### Clojure

* [The Clojure Style Guide](https://guide.clojure.style/)
* [Metabase Clojure Style Guide](https://github.com/metabase/metabase/wiki/Metabase-Clojure-Style-Guide)


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


### Stan

* [Stan Program Style Guide](https://mc-stan.org/docs/2_22/stan-users-guide/stan-program-style-guide.html)


### Files

><sup>File organization and naming are powerful weapons against chaos. (Jenny Bryan)</sup>

* [Naming Things](https://speakerdeck.com/jennybc/how-to-name-files)
* [File Organization: Naming](https://datacarpentry.org/rr-organization1/01-file-naming/) from Data Carpentry
* [Best Practices for File Naming](https://records-express.blogs.archives.gov/2017/08/22/best-practices-for-file-naming/) from the National Archives Records Express
* [Names](https://style.tidyverse.org/files.html#names) in The Tidyverse Style Guide
* [Better Naming Convention for Jupyter Notebook](https://stackoverflow.com/questions/38305217/better-naming-convention-for-jupyter-notebook)
