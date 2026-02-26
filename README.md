# Students_Performance_R_lang_code

---
title: "Students Performance"
author: "Samarth Ghule"
date: "2026-02-26"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## R Markdown


```{r}
library(ggplot2)
library(dplyr)
```
```{r}
data <- read.csv("StudentsPerformance.csv")
head(data)
```
```{r}
summary(data)
```
```{r}
mean(data$math.score)
```
```{r}
mean(data$reading.score)
```
```{r}
mean(data$writing.score)
```
```{r}
str(data)
```
```{r}
colSums(is.na(data))
```
```{r}
data <- data[!duplicated(data), ]
```

```{r}
data <- read.csv("StudentsPerformance.csv", stringsAsFactors = FALSE)
colnames(data) <- make.names(colnames(data))
```
```{r}
boxplot(data$math.score,
        main = "Boxplot of Math Scores",
        col = "lightblue",
        ylab = "Math Score")
```
```{r}
Q1 <- quantile(data$math.score, 0.25)
Q3 <- quantile(data$math.score, 0.75)
IQR_value <- IQR(data$math.score)

lower_limit <- Q1 - 1.5 * IQR_value
upper_limit <- Q3 + 1.5 * IQR_value

outliers <- data$math.score[data$math.score < lower_limit |
                             data$math.score > upper_limit]

outliers
```
```{r}
hist(data$math.score,
     main = "Histogram of Math Scores",
     col = "skyblue",
     xlab = "Math Score")
```
```{r}
hist(data$writing.score,
     main = "Histogram of Writing Scores",
     col = "yellow",
     xlab = "Writing Score")
```

```{r}
barplot(table(data$gender),
        main = "Gender Distribution",
        col = c("pink", "lightgreen"))
```
```{r}
plot(data$math.score, data$reading.score,
     main = "Math vs Reading Score",
     xlab = "Math Score",
     ylab = "Reading Score",
     col = "blue",
     pch = 19)
```
```{r}
plot(data$math.score, data$writing.score,
     main = "Math vs Writing Score",
     xlab = "Math Score",
     ylab = "Writing Score",
     col = "red",
     pch = 19)
```
