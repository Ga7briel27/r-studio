
R version 4.4.2 (2024-10-31 ucrt) -- "Pile of Leaves"
Copyright (C) 2024 The R Foundation for Statistical Computing
Platform: x86_64-w64-mingw32/x64

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

[Previously saved workspace restored]

> install.packages("tidyverse")
Installing package into ‘C:/Users/IU Student/AppData/Local/R/win-library/4.4’
(as ‘lib’ is unspecified)
--- Please select a CRAN mirror for use in this session ---
trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/tidyverse_2.0.0.zip'
Content type 'application/zip' length 431685 bytes (421 KB)
downloaded 421 KB

package ‘tidyverse’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
        C:\Users\IU Student\AppData\Local\Temp\RtmpQZjq8a\downloaded_packages
> 
> install.packages("tidymodels")
Installing package into ‘C:/Users/IU Student/AppData/Local/R/win-library/4.4’
(as ‘lib’ is unspecified)
trying URL 'https://cran.case.edu/bin/windows/contrib/4.4/tidymodels_1.3.0.zip'
Content type 'application/zip' length 89269 bytes (87 KB)
downloaded 87 KB

package ‘tidymodels’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
        C:\Users\IU Student\AppData\Local\Temp\RtmpQZjq8a\downloaded_packages
> # Load necessary packages
> 
> library(tidyverse)
── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.1.4     ✔ readr     2.1.5
✔ forcats   1.0.0     ✔ stringr   1.5.1
✔ ggplot2   3.5.1     ✔ tibble    3.2.1
✔ lubridate 1.9.4     ✔ tidyr     1.3.1
✔ purrr     1.0.4     
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
Warning messages:
1: package ‘tidyverse’ was built under R version 4.4.3 
2: package ‘lubridate’ was built under R version 4.4.3 
> 
>  
> 
> # Read in the dataset
> 
> fraud_data <- read_csv("fraud_detection_data.csv")
Error: 'fraud_detection_data.csv' does not exist in current working directory ('C:/Users/IU Student/Documents').
> 
>  
> 
> # View the first few rows
> 
> head(fraud_data)
Error: object 'fraud_data' not found
> 
>  
> 
> # Check the structure of the dataset
> 
> glimpse(fraud_data)
Error: object 'fraud_data' not found
> # Load necessary packages
> 
> library(tidyverse)
> 
>  
> 
> # Read in the dataset
> 
> fraud_data <- read_csv("fraud_detection_data.csv")

[1mindexing[0m [34mfraud_detection_data.csv[0m [========================] [32m26.24MB/s[0m, eta: [36m 0s[0m
                                                                                                                   
Rows: 1000 Columns: 9
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (4): transaction_id, device_type, location, merchant_type
dbl (5): amount, transaction_time, previous_fraud, card_usage_freq, fraudulent

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
> 
>  
> 
> # View the first few rows
> 
> head(fraud_data)
# A tibble: 6 × 9
  transaction_id amount transaction_time device_type location    previous_fraud
  <chr>           <dbl>            <dbl> <chr>       <chr>                <dbl>
1 TXN0001          458.            16.1  Desktop     New York                 0
2 TXN0002          469.            15.0  Desktop     Los Angeles              0
3 TXN0003          147.             1.75 Mobile      New York                 0
4 TXN0004          416.            10.5  Desktop     Miami                    0
5 TXN0005          323.            15.4  Desktop     Houston                  0
6 TXN0006          262.            22.8  Mobile      Miami                    0
# ℹ 3 more variables: card_usage_freq <dbl>, merchant_type <chr>,
#   fraudulent <dbl>
> 
>  
> 
> # Check the structure of the dataset
> 
> glimpse(fraud_data)
Rows: 1,000
Columns: 9
$ transaction_id   <chr> "TXN0001", "TXN0002", "TXN0003", "TXN0004", "TXN0005"…
$ amount           <dbl> 457.83, 468.85, 146.64, 416.07, 322.66, 261.95, 369.6…
$ transaction_time <dbl> 16.14, 15.05, 1.75, 10.50, 15.39, 22.75, 9.40, 22.86,…
$ device_type      <chr> "Desktop", "Desktop", "Mobile", "Desktop", "Desktop",…
$ location         <chr> "New York", "Los Angeles", "New York", "Miami", "Hous…
$ previous_fraud   <dbl> 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0,…
$ card_usage_freq  <dbl> 7, 4, 5, 4, 3, 5, 5, 8, 7, 6, 3, 1, 7, 1, 23, 5, 9, 1…
$ merchant_type    <chr> "Travel", "Grocery", "Electronics", "Travel", "Travel…
$ fraudulent       <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,…
> # Convert categorical variables to factors
> 
> Library(tidyverse)
Error in Library(tidyverse) : could not find function "Library"
> 
> fraud_data <- fraud_data %>%
+ 
+   mutate(
+ 
+     device_type = as.factor(device_type),
+ 
+     location = as.factor(location),
+ 
+     merchant_type = as.factor(merchant_type),
+ 
+     fraudulent = as.factor(fraudulent) 
+ 
+   )
> ggplot(fraud_data, aes(x = transaction_time, y = amount, color = fraudulent)) +
+ 
+   geom_point(alpha = 0.6) +
+ 
+   labs(title = "Transaction Amount vs. Time",
+ 
+        x = "Transaction Time (24-hour format)",
+ 
+        y = "Transaction Amount ($)",
+ 
+        color = "Fraudulent") +
+ 
+   theme_minimal()
> ggplot(fraud_data, aes(x = device_type, fill = fraudulent)) +
+ 
+   geom_bar(position = "fill") +
+ 
+   labs(title = "Fraud Cases by Device Type",
+ 
+        x = "Device Type",
+ 
+        y = "Proportion of Transactions",
+ 
+        fill = "Fraudulent") +
+ 
+   theme_minimal()
> # Load tidymodels for modeling
> 
> library(tidymodels)
── Attaching packages ────────────────────────────────────── tidymodels 1.3.0 ──
✔ broom        1.0.7     ✔ rsample      1.3.0
✔ dials        1.4.0     ✔ tune         1.3.0
✔ infer        1.0.7     ✔ workflows    1.2.0
✔ modeldata    1.4.0     ✔ workflowsets 1.1.0
✔ parsnip      1.3.1     ✔ yardstick    1.3.2
✔ recipes      1.2.1     
── Conflicts ───────────────────────────────────────── tidymodels_conflicts() ──
✖ scales::discard() masks purrr::discard()
✖ dplyr::filter()   masks stats::filter()
✖ recipes::fixed()  masks stringr::fixed()
✖ dplyr::lag()      masks stats::lag()
✖ yardstick::spec() masks readr::spec()
✖ recipes::step()   masks stats::step()
• Search for functions across packages at https://www.tidymodels.org/find/
There were 11 warnings (use warnings() to see them)
> 
>  
> 
> # Set up the data split (80% training, 20% testing)
> 
> set.seed(42)
> 
> fraud_split <- initial_split(fraud_data, prop = 0.8, strata = fraudulent)
> 
>  
> 
> # Create training and testing datasets
> 
> fraud_train <- training(fraud_split)
> 
> fraud_test <- testing(fraud_split)
> 
>  # Define the decision tree model
> 
> fraud_model <- decision_tree() %>%
+ 
+   set_engine("rpart") %>%
+ 
+   set_mode("classification")
> 
>  
> 
> # Fit the model to the training data
> 
> fraud_fit <- fraud_model %>%
+ 
+   fit(fraudulent ~ amount + transaction_time + device_type + previous_fraud + card_usage_freq, data = fraud_train)
> 
>  
> 
> # View the decision tree model
> 
> fraud_fit
parsnip model object

n= 800 

node), split, n, loss, yval, (yprob)
      * denotes terminal node

1) root 800 37 0 (0.9537500 0.0462500) *
> ggplot(fraud_data, aes(x = hour_of_day, y = amount, color = fraudulent)) + 
+ 
+   geom_point(alpha = 0.6) +
+ 
+   labs(title = "Transaction Amount vs. Time",
+ 
+        x = "Transaction Time (24-hour format)",
+ 
+        y = "Transaction Amount ($)",
+ 
+        color = "Fraudulent") +
+ 
+   theme_minimal()
Error in `geom_point()`:
! Problem while computing aesthetics.
ℹ Error occurred in the 1st layer.
Caused by error:
! object 'hour_of_day' not found
Run `rlang::last_trace()` to see where the error occurred.
> ggplot(fraud_data, aes(x = transaction_time, y = amount, color = fraudulent)) +
+ 
+ # Load necessary packages
+ 
+ library(tidyverse)
Error in `ggplot_add()`:
! Can't add `library(tidyverse)` to a <ggplot> object.
Run `rlang::last_trace()` to see where the error occurred.
> 
> # Load dataset (update file path as needed)
> fraud_data <- read_csv("C:/Your/Full/File/Path/fraud_detection_data.csv")
Error: 'C:/Your/Full/File/Path/fraud_detection_data.csv' does not exist.
> 
> # View column names to confirm time column
> colnames(fraud_data)
[1] "transaction_id"   "amount"           "transaction_time" "device_type"     
[5] "location"         "previous_fraud"   "card_usage_freq"  "merchant_type"   
[9] "fraudulent"      
> 
> # Assuming 'transaction_time' is the correct column name
> # Scatter plot: Transaction Amount vs. Time
> 
> ggplot(fraud_data, aes(x = transaction_time, y = amount, color = fraudulent)) + 
+ 
+   geom_point(alpha = 0.6) +
+ 
+   labs(title = "Transaction Amount vs. Time",
+ 
+        x = "Transaction Time (24-hour format)",
+ 
+        y = "Transaction Amount ($)",
+ 
+        color = "Fraudulent") +
+ 
+   theme_minimal()
> # Define the decision tree model
> 
> fraud_model <- decision_tree() %>%
+ 
+   set_engine("rpart") %>%
+ 
+   set_mode("classification")
> 
>  
> 
> # Fit the model to the training data
> 
> fraud_fit <- fraud_model %>%
+ 
+   fit(fraudulent ~ amount + transaction_time + location_type + previous_fraud + card_usage_freq, data = fraud_train)  
Error in eval(predvars, data, env) : object 'location_type' not found
> 
>  
> 
> # View the decision tree model
> 
> fraud_fit
parsnip model object

n= 800 

node), split, n, loss, yval, (yprob)
      * denotes terminal node

1) root 800 37 0 (0.9537500 0.0462500) *
> # Generate predictions on the test set
> 
> fraud_predictions <- predict(fraud_fit, fraud_test, type = "class")
> 
>  
> 
> # Create a confusion matrix
> 
> library(yardstick)
> 
> conf_mat <- conf_mat(fraud_test$fraudulent, estimate = fraud_predictions$.pred_class)
Error in UseMethod("conf_mat") : 
  no applicable method for 'conf_mat' applied to an object of class "factor"
> 
> print(conf_mat)
function (data, ...) 
{
    UseMethod("conf_mat")
}
<bytecode: 0x0000020afa1a4630>
<environment: namespace:yardstick>
> 
> # Alternatively, you can also use this 
> # conf_mat <- table(fraud_test$fraudulent, fraud_predictions$.pred_class)
> 
> # Step 2: Compute precision
> 
> precision <- precision(fraud_test$fraudulent, estimate = fraud_predictions$.pred_class)
Error in UseMethod("precision") : 
  no applicable method for 'precision' applied to an object of class "factor"
> print(precision)
A class metric | direction: maximize
> # Compute precision and recall
> 
> library(yardstick)
> 
> fraud_metrics <- fraud_predictions %>%
+ 
+   bind_cols(fraud_test) %>%
+ 
+   metrics(truth = fraudulent, estimate = $.pred_class)
Error: unexpected '$' in:
"
  metrics(truth = fraudulent, estimate = $"
> 
>  
> 
> print(fraud_metrics)
Error: object 'fraud_metrics' not found
> # Compute precision and recall
> 
> library(yardstick)
> 
> fraud_metrics <- metrics(truth = fraud_test$fraudulent, 
+                         estimate = fraud_predictions$.pred_class)
Error in UseMethod("metrics") : 
  no applicable method for 'metrics' applied to an object of class "factor"
> 
> print(fraud_metrics)
Error: object 'fraud_metrics' not found
> q()
> 
