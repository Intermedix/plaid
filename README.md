# Plaid

Plaid is a robust and tailor-able grid system, ready to align your
most complex layout.  LESS variables allow for tailoring the number
and width of columns and gutters and, thanks to the power of LESS,
columns can be infinitely nested.  When designing responsively, LESS
mixins paired with media queries make it simple to changes column
widths.

## Basic Columns

To create a grid, add the `grid-row` class to any element.  Then, add
child elements with `col-N` classes where *N* is the number of
columns to span.

## Offsetting

In addition to the `col-N` class, add a `skip-N` class to skip *N*
columns.

## Nesting

Creating a complex nested grid with Plaid is easy: simply add `col-N`
elements inside other `col-N` elements.  If you want to support IE7,
add the `last-col` class to the last element in a row.

## Tailoring the Grid

There are a few LESS variables that allow the grid to be tailored to
fit your needs:

* **@grid-columns** – The number of columns.  12 is the default.
* **@grid-column-width** – The column width.  Don't add a unit; the
  width will be converted to a percentage (relative to the gutter
  width).
* **@grid-gutter-width** – The gutter width.  Again, no unit
  needed.

## The LESS `column` Mixin

After setting the aforementioned variables and compiling you LESS
files (if necessary), you will have most of the classes you need to
start building fluid layouts.  If you need to apply column styling to
other elements or adapt your layout to act responsively at certain
breakpoints, you can use the `column` mixin.  There are three
parameters:

* [int] **Number of columns to span** – If left blank, this
  defaults to one.
* [int] **Total number of columns in context** – This defaults to
  `@grid-columns`.  If you are nesting columns, this is the width of
  the containing parent.
* [string] **Position** – The column's horizontal position in the
  grid.  The valid options are *first*, *middle*, and *last*. This
  determines the correct CSS to manipulate the gutters and margins,
  depending on the column's position in the grid.

### Example Using the `column` Mixin

In this example, we're overriding the default column width for
`col-2` columns at a 500px breakpoint.  We're giving them a width of
4 columns, based on the global grid width, essentially doubling
their width to adapt to a narrowing screen.

    @media screen and (max-width: 500px) {
        .col-2 {
            .column (4, @grid-columns);
        }
    }

# Generating

Make sure that you have the less compiler installed locally with:

    npm install

To generate un-minified CSS:

    npm test

To generate minified CSS:

    npm start

# License

Copyright 2013 Intermedix Corporation.

Licensed under the Apache License, Version 2.0 (the "License"); you
may not use this file except in compliance with the License.  You may
obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
implied.  See the License for the specific language governing
permissions and limitations under the License.
