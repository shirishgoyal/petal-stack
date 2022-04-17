---
title: Calculate age from date of birth in Elixir
description: A code snippet to calculate age in years from date of birth without using
  external libraries like Timex
date: 2022-04-17T05:42:58.851Z
tags:
  - elixir
  - date
lastmod: 2022-04-17T06:01:33.365Z
---

Elixir has default modules for Date and Time calculations but lack many functions which are often needed. One of them is calculating age from date of birth. Although 3rd party libraries like Timex do provide some in-built functions to calculate date differences in terms of years, months or days etc., but no such function is directly available for age calculation.

```elixir
defmodule Calculator do
  def age(dob) do
    today = Date.utc_today()

    # birthday is yet to arrive this year
    birthday_pending =
      if {today.month, today.day} < {dob.month, dob.day}, do: 1, else: 0

    age = today.year - dob.year - birthday_pending

    age
  end
end
```

Usage is as given below

```elixir
Calculator.age(~D[1980-09-22]) # date in format yyyy-mm-dd
```

For today as 17 Apr, 2022, the response will be 41 years
