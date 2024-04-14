# T_Test-in-reall_life-scenario-with-the-application-of-the-Mall_Customer-Datasets
In this example, we first loaded the Mall Customer dataset into R using the read.csv() function. We then subsetted the data into two groups, one for female customers and one for male customers, using the subset() function.
---
title: "T_TEST iN REAL_LIFE SCENARIO USING MALL CUSTOMER DATASET"
author: "Langat Erick"
output:
  beamer_presentation: default
  powerpoint_presentation: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(
 message = FALSE,
 warning = FALSE,
 echo = FALSE)
```

```{r}
#load the libraries
library(tidyverse)
library(report)
library(tidymodels)
```

```{r}
# Load the Mall Customer dataset
mall_customer <- read.csv("C:/Users/JIT/Downloads/PYTHON TUTORIALS/Mall_Customers.csv")
mall_customer

```

```{r}
# Subset the data by gender
female_data <- subset(mall_customer, Gender == "Female")
female_data
```

```{r}
male_data <- subset(mall_customer, Gender == "Male")
male_data
```

```{r}
# Conduct an independent samples t-test
ttest_result <- t.test(female_data$Spending.Score..1.100., male_data$Spending.Score..1.100., var.equal = TRUE)

# Print the results
ttest_result %>% report()

```

In this example, we first loaded the Mall Customer dataset into R using the **`read.csv()`** function. We then subsetted the data into two groups, one for female customers and one for male customers, using the **`subset()`** function.

Next, we conducted an independent samples t-test using the **`t.test()`** function. We specified the spending score variable for each gender group as the two samples to compare, and set the **`var.equal`** argument to **`TRUE`** to assume equal variances for the two groups. If we had reason to believe that the variances were not equal, we could set this argument to **`FALSE`** and use the Welch's t-test instead.

Finally, we printed the results of the t-test using the **`ttest_result`** object. The output will include the mean spending score for each group, the difference in means, the standard error, the t-statistic, the degrees of freedom, and the p-value. The p-value will indicate if there is a significant difference in spending score between male and female customers in the Mall Customer dataset. If the p-value is less than the commonly used threshold of 0.05, we can reject the null hypothesis and conclude that there is a significant difference in spending score between the two gender groups.

**report()** function gives us the results explanation in a more simplified way for proper understanding

\
