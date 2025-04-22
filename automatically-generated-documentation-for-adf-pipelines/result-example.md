PIPELINE_TITLE

[[_TOC_]]

# Parameters

| #   | Name        | Type   | Default value |
| --- | ----------- | ------ | ------------- |
| 1   | Parameter_1 | String | Example       |

# Variables

| #   | Name       | Type   | Default value |
| --- | ---------- | ------ | ------------- |
| 1   | Variable_1 | String | (empty)       |
| 2   | Variable_2 | String | Example       |

# Pipeline

## _Main_

:::mermaid
graph LR
Start[Start]
Finish[Finish]
Foreach[ForEach]
Start --> |Succeeded| Foreach
Foreach --> |Succeeded| Finish
:::

## _ForEach_

:::mermaid
graph LR
SomeLogic[Some Logic]
Success[Success]
Fail[Fail]
SomeLogic --> |Succeeded| Success
SomeLogic --> |Failed| Fail
:::

1. _Start_ - your description there.
2. _ForEach_ - your description there.
    1. _SomeLogic_ - your description there.
    2. _Success_ - your description there.
    3. _Fail_ - your description there.
3. _Finish_ - your description there.
