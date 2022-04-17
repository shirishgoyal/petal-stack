---
title: Calculate ranks for list of numbers in Elixir
description: In a list of N numbers with duplicates allowed, elements can be ranked in
  ascending or descending order based on their values from 1 to N
date: 2022-04-17T14:05:29.358Z
tags:
  - elixir
  - math
lastmod: 2022-04-17T14:18:44.959Z
---

In a list of N numbers with duplicates allowed, elements can be ranked in ascending or descending order based on their values from 1 to N. If there are duplicate values, then they are all assigned same rank and corresponding rank values are not used anymore.

For example:

Given list = 1, 4, 2, 3, 1

Ranks (ascending) = 1, 5, 3, 4, 1

Ranks (descending) = 4, 1, 3, 2, 4

```elixir
defmodule Calculator do
    def ranks(values, order \\ :desc) do
        sorted = Enum.sort(values, order)

        Enum.map(values, fn x ->
        index = Enum.find_index(sorted, fn y -> y == x end)
        index + 1
        end)
    end
end
```

Usage is as given below

```elixir
Calculator.ranks([1, 4, 2, 3, 1])
Calculator.ranks([1, 4, 2, 3, 1], :desc)
Calculator.ranks([1, 4, 2, 3, 1], :asc)
```

Response will be

```bash
[4, 1, 3, 2, 4]
[4, 1, 3, 2, 4]
[1, 5, 3, 4, 1]
```
