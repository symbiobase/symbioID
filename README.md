### Collection metadata 

Access the most up to date revision of the symbioBase collection via .csv:

```{r}

read.csv("https://raw.githubusercontent.com/symbiobase/symbioID/main/Symbiobase.csv") |> 
  str()

```

![Screenshot 2024-07-25 at 11 29 54 AM](https://github.com/user-attachments/assets/424fbe54-20f3-41d0-b435-7945d73b8f84)


### Revision History

For reproducible code, link to the `SHA` hash of a specific commit in the [revision history](https://github.com/symbiobase/symbioID/commits/main/Symbiobase.csv). 

Replace `/main/`

```
raw.githubusercontent.com/symbiobase/symbioID/main/Symbiobase.csv
```

with the `SHA` version, e.g. `/714aa24/`:

```
raw.githubusercontent.com/symbiobase/symbioID/714aa24/Symbiobase.csv
```

For example:

```{r}

read.csv("https://raw.githubusercontent.com/symbiobase/symbioID/714aa24/Symbiobase.csv") |> 
  str()

```

![Screenshot 2024-07-25 at 11 32 27 AM](https://github.com/user-attachments/assets/3c422b51-e03e-4161-9df4-5683e637197b)


### Intitial commit

```{r}
library(httr)
library(tidyverse)
library(read_excel)
library(janitor)

GET("https://github.com/symbiobase/symbioID/raw/cdbc251040f3bd0a84345fe17a0175c2ee176187/symbioBase.xlsx",  write_disk(symbiobase_origin <- tempfile(fileext = ".xlsx")))

symbiobase <- readxl::read_excel(symbiobase_origin, col_types="guess", guess_max=10000)  |>
  clean_names()

write.csv(symbiobase, "symbioBase.csv")

```
