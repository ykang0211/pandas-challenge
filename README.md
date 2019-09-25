
### Note
* Instructions have been included for each segment. You do not have to follow them exactly, but they are included to help you think through the steps.


```python
# Dependencies and Setup
import pandas as pd

```


```python
# File to Load (Remember to Change These)
school_data =  "Resources/schools_complete.csv"
student_data = "Resources/students_complete.csv"

#Read school and Student Data File and store into Pandas Data Frames
school_df = pd.read_csv(school_data)
student_df = pd.read_csv(student_data)

#Combine the data into a single dataset
merge_df = pd.merge(student_df, school_df, how = "left", on = ["school_name", "school_name"])

# merge_df = pd.merge(school_df, student_df, on = ["school_name", "school_name"])
merge_df

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>student_name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school_name</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>School ID</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>2</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>3</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>4</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>39165</td>
      <td>39165</td>
      <td>Donna Howard</td>
      <td>F</td>
      <td>12th</td>
      <td>Thomas High School</td>
      <td>99</td>
      <td>90</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
    <tr>
      <td>39166</td>
      <td>39166</td>
      <td>Dawn Bell</td>
      <td>F</td>
      <td>10th</td>
      <td>Thomas High School</td>
      <td>95</td>
      <td>70</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
    <tr>
      <td>39167</td>
      <td>39167</td>
      <td>Rebecca Tanner</td>
      <td>F</td>
      <td>9th</td>
      <td>Thomas High School</td>
      <td>73</td>
      <td>84</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
    <tr>
      <td>39168</td>
      <td>39168</td>
      <td>Desiree Kidd</td>
      <td>F</td>
      <td>10th</td>
      <td>Thomas High School</td>
      <td>99</td>
      <td>90</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
    <tr>
      <td>39169</td>
      <td>39169</td>
      <td>Carolyn Jackson</td>
      <td>F</td>
      <td>11th</td>
      <td>Thomas High School</td>
      <td>95</td>
      <td>75</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
<p>39170 rows × 11 columns</p>
</div>




```python
merge_df.dtypes
```




    Student ID        int64
    student_name     object
    gender           object
    grade            object
    school_name      object
    reading_score     int64
    math_score        int64
    School ID         int64
    type             object
    size              int64
    budget            int64
    dtype: object



## District Summary

* Calculate the total number of schools

* Calculate the total number of students

* Calculate the total budget

* Calculate the average math score 

* Calculate the average reading score

* Calculate the overall passing rate (overall average score), i.e. (avg. math score + avg. reading score)/2

* Calculate the percentage of students with a passing math score (70 or greater)

* Calculate the percentage of students with a passing reading score (70 or greater)

* Create a dataframe to hold the above results

* Optional: give the displayed data cleaner formatting


```python
total_number_schools = school_df["school_name"].count()
total_number_students = merge_df["student_name"].count()


total_budget = school_df["budget"].sum()

average_math_score = merge_df["math_score"].mean()
average_reading_score = merge_df["reading_score"].mean()

passing_math_score = merge_df.loc[merge_df["math_score"] >= 70]["student_name"].count()
passing_math_rate = (passing_math_score / total_number_students) * 100

passing_reading_score = merge_df.loc[merge_df["reading_score"] >= 70]["student_name"].count()
passing_reading_rate = (passing_reading_score / total_number_students) * 100

overall_passing_rate = (passing_math_rate + passing_reading_rate) / 2

results_df = pd.DataFrame({"Total Schools" : total_number_schools, "Total Students" : total_number_students, 
                           "Total Budget" : total_budget,
                           "Average Math Score" : average_math_score, "Average Reading Score" : average_reading_score,
                          "% Passing Math" : passing_math_rate, "% Passing Reading" : passing_reading_rate,
                          "% Overall Passing Rate" : overall_passing_rate}, index = [0])

# using map to format displaying $ and two decimal points
results_df["Total Budget"] = results_df["Total Budget"].map("${:,.2f}".format)
results_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Schools</th>
      <th>Total Students</th>
      <th>Total Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>15</td>
      <td>39170</td>
      <td>$24,649,428.00</td>
      <td>78.985371</td>
      <td>81.87784</td>
      <td>74.980853</td>
      <td>85.805463</td>
      <td>80.393158</td>
    </tr>
  </tbody>
</table>
</div>



## School Summary

* Create an overview table that summarizes key metrics about each school, including:
  * School Name
  * School Type
  * Total Students
  * Total School Budget
  * Per Student Budget
  * Average Math Score
  * Average Reading Score
  * % Passing Math
  * % Passing Reading
  * Overall Passing Rate (Average of the above two)
  
* Create a dataframe to hold the above results


```python
school_summary_df = pd.merge(student_df, school_df, on = "school_name")
school_summary_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>student_name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school_name</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>School ID</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>2</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>3</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>4</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
      <td>0</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>39165</td>
      <td>39165</td>
      <td>Donna Howard</td>
      <td>F</td>
      <td>12th</td>
      <td>Thomas High School</td>
      <td>99</td>
      <td>90</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
    <tr>
      <td>39166</td>
      <td>39166</td>
      <td>Dawn Bell</td>
      <td>F</td>
      <td>10th</td>
      <td>Thomas High School</td>
      <td>95</td>
      <td>70</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
    <tr>
      <td>39167</td>
      <td>39167</td>
      <td>Rebecca Tanner</td>
      <td>F</td>
      <td>9th</td>
      <td>Thomas High School</td>
      <td>73</td>
      <td>84</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
    <tr>
      <td>39168</td>
      <td>39168</td>
      <td>Desiree Kidd</td>
      <td>F</td>
      <td>10th</td>
      <td>Thomas High School</td>
      <td>99</td>
      <td>90</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
    <tr>
      <td>39169</td>
      <td>39169</td>
      <td>Carolyn Jackson</td>
      <td>F</td>
      <td>11th</td>
      <td>Thomas High School</td>
      <td>95</td>
      <td>75</td>
      <td>14</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
<p>39170 rows × 11 columns</p>
</div>




```python
# School Summary
# school_summary = school_df
school_summary_df = pd.merge(student_df, school_df, on = "school_name")

school_name = school_df["school_name"].unique()
# school_name = school_df["school_name"].count()
# school_name = school_summary_df.groupby("school_name")["school_name"].unique()
school_type = school_summary_df.groupby("school_name")["type"].unique()

# total_school_students = school_summary_df["size"].count()
total_school_students = school_summary_df["school_name"].value_counts()

# total school budget and per student budget
total_school_budget = school_summary_df.groupby("school_name")["budget"].mean()
per_student_budget = total_school_budget / total_school_students

# average school math and reading score to get passing rate and overall passing rate
average_school_math_score = school_summary_df.groupby("school_name")["math_score"].mean()
average_school_reading_score = school_summary_df.groupby("school_name")["reading_score"].mean()


passing_school_math_score = school_summary_df[(school_summary_df["math_score"] >= 70)]
passing_school_reading_score = school_summary_df[(school_summary_df["reading_score"] >= 70)]

passing_school_math_rate = (passing_school_math_score.groupby(["school_name"])["student_name"].count() / total_school_students) * 100
passing_school_reading_rate = (passing_school_reading_score.groupby(["school_name"])["student_name"].count() / total_school_students) * 100
        

overall_school_passing_rate = (passing_school_math_rate + passing_school_reading_rate) / 2

# create dataframe
results_school_summary_df = pd.DataFrame({"School Name" : school_name, "School Type" : school_type, "Total Students" : total_school_students,
                                  "Total School Budget" : total_school_budget, "Per Student Budget" : per_student_budget,
                                  "Average Math Score" : average_school_math_score, "Average Reading Score" : average_school_reading_score,
                                 "% Passing Math" : passing_school_math_rate, "% Passing Reading" : passing_school_reading_rate,
                                  "% Overall Passing Rate" : overall_school_passing_rate
                                 })
del results_school_summary_df["School Name"]

results_school_summary_df["Total School Budget"] = results_school_summary_df["Total School Budget"].map("${:,.2f}".format)
results_school_summary_df["Per Student Budget"] = results_school_summary_df["Per Student Budget"].map("${:.2f}".format)

results_school_summary_df

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Bailey High School</td>
      <td>[District]</td>
      <td>4976</td>
      <td>$3,124,928.00</td>
      <td>$628.00</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>74.306672</td>
    </tr>
    <tr>
      <td>Cabrera High School</td>
      <td>[Charter]</td>
      <td>1858</td>
      <td>$1,081,356.00</td>
      <td>$582.00</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <td>Figueroa High School</td>
      <td>[District]</td>
      <td>2949</td>
      <td>$1,884,411.00</td>
      <td>$639.00</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <td>Ford High School</td>
      <td>[District]</td>
      <td>2739</td>
      <td>$1,763,916.00</td>
      <td>$644.00</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>73.804308</td>
    </tr>
    <tr>
      <td>Griffin High School</td>
      <td>[Charter]</td>
      <td>1468</td>
      <td>$917,500.00</td>
      <td>$625.00</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <td>Hernandez High School</td>
      <td>[District]</td>
      <td>4635</td>
      <td>$3,022,020.00</td>
      <td>$652.00</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>73.807983</td>
    </tr>
    <tr>
      <td>Holden High School</td>
      <td>[Charter]</td>
      <td>427</td>
      <td>$248,087.00</td>
      <td>$581.00</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>94.379391</td>
    </tr>
    <tr>
      <td>Huang High School</td>
      <td>[District]</td>
      <td>2917</td>
      <td>$1,910,635.00</td>
      <td>$655.00</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <td>Johnson High School</td>
      <td>[District]</td>
      <td>4761</td>
      <td>$3,094,650.00</td>
      <td>$650.00</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <td>Pena High School</td>
      <td>[Charter]</td>
      <td>962</td>
      <td>$585,858.00</td>
      <td>$609.00</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <td>Rodriguez High School</td>
      <td>[District]</td>
      <td>3999</td>
      <td>$2,547,363.00</td>
      <td>$637.00</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <td>Shelton High School</td>
      <td>[Charter]</td>
      <td>1761</td>
      <td>$1,056,600.00</td>
      <td>$600.00</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>94.860875</td>
    </tr>
    <tr>
      <td>Thomas High School</td>
      <td>[Charter]</td>
      <td>1635</td>
      <td>$1,043,130.00</td>
      <td>$638.00</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>95.290520</td>
    </tr>
    <tr>
      <td>Wilson High School</td>
      <td>[Charter]</td>
      <td>2283</td>
      <td>$1,319,574.00</td>
      <td>$578.00</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
    <tr>
      <td>Wright High School</td>
      <td>[Charter]</td>
      <td>1800</td>
      <td>$1,049,400.00</td>
      <td>$583.00</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>94.972222</td>
    </tr>
  </tbody>
</table>
</div>



## Top Performing Schools (By Passing Rate)

* Sort and display the top five schools in overall passing rate


```python
# Top Five Schools by Passing Rate 
top_five = results_school_summary_df.sort_values("% Overall Passing Rate", ascending = False)
top_five.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Cabrera High School</td>
      <td>[Charter]</td>
      <td>1858</td>
      <td>$1,081,356.00</td>
      <td>$582.00</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <td>Thomas High School</td>
      <td>[Charter]</td>
      <td>1635</td>
      <td>$1,043,130.00</td>
      <td>$638.00</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>95.290520</td>
    </tr>
    <tr>
      <td>Pena High School</td>
      <td>[Charter]</td>
      <td>962</td>
      <td>$585,858.00</td>
      <td>$609.00</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <td>Griffin High School</td>
      <td>[Charter]</td>
      <td>1468</td>
      <td>$917,500.00</td>
      <td>$625.00</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <td>Wilson High School</td>
      <td>[Charter]</td>
      <td>2283</td>
      <td>$1,319,574.00</td>
      <td>$578.00</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
  </tbody>
</table>
</div>



## Bottom Performing Schools (By Passing Rate)

* Sort and display the five worst-performing schools


```python
bottom_five = results_school_summary_df.sort_values("% Overall Passing Rate", ascending = True)
bottom_five.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Rodriguez High School</td>
      <td>[District]</td>
      <td>3999</td>
      <td>$2,547,363.00</td>
      <td>$637.00</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <td>Figueroa High School</td>
      <td>[District]</td>
      <td>2949</td>
      <td>$1,884,411.00</td>
      <td>$639.00</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <td>Huang High School</td>
      <td>[District]</td>
      <td>2917</td>
      <td>$1,910,635.00</td>
      <td>$655.00</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <td>Johnson High School</td>
      <td>[District]</td>
      <td>4761</td>
      <td>$3,094,650.00</td>
      <td>$650.00</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <td>Ford High School</td>
      <td>[District]</td>
      <td>2739</td>
      <td>$1,763,916.00</td>
      <td>$644.00</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>73.804308</td>
    </tr>
  </tbody>
</table>
</div>



## Math Scores by Grade

* Create a table that lists the average Reading Score for students of each grade level (9th, 10th, 11th, 12th) at each school.

  * Create a pandas series for each grade. Hint: use a conditional statement.
  
  * Group each series by school
  
  * Combine the series into a dataframe
  
  * Optional: give the displayed data cleaner formatting


```python

ninth_math = student_df.loc[student_df["grade"] == "9th"].groupby("school_name")["math_score"].mean()
tenth_math = student_df.loc[student_df["grade"] == "10th"].groupby("school_name")["math_score"].mean()
eleventh_math = student_df.loc[student_df["grade"] == "11th"].groupby("school_name")["math_score"].mean()
twelfth_math = student_df.loc[student_df["grade"] == "12th"].groupby("school_name")["math_score"].mean()

student_df.rename(columns = {"school_name" : " "})

grade_df = pd.DataFrame({"School Name" : school_name, "9th" : ninth_math, "10th" : tenth_math, 
                         "11th" : eleventh_math, "12th" : twelfth_math})

# .set_index("School Name").rename_axis(None)

del grade_df["School Name"]

# grade_df.columns

grade_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
    <tr>
      <th>school_name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Bailey High School</td>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
    </tr>
    <tr>
      <td>Cabrera High School</td>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
    </tr>
    <tr>
      <td>Figueroa High School</td>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
    </tr>
    <tr>
      <td>Ford High School</td>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
    </tr>
    <tr>
      <td>Griffin High School</td>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
    </tr>
    <tr>
      <td>Hernandez High School</td>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
    </tr>
    <tr>
      <td>Holden High School</td>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
    </tr>
    <tr>
      <td>Huang High School</td>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
    </tr>
    <tr>
      <td>Johnson High School</td>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
    </tr>
    <tr>
      <td>Pena High School</td>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
    </tr>
    <tr>
      <td>Rodriguez High School</td>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
    </tr>
    <tr>
      <td>Shelton High School</td>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
    </tr>
    <tr>
      <td>Thomas High School</td>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
    </tr>
    <tr>
      <td>Wilson High School</td>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
    </tr>
    <tr>
      <td>Wright High School</td>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
    </tr>
  </tbody>
</table>
</div>



## Reading Score by Grade 

* Perform the same operations as above for reading scores


```python
ninth_reading = student_df.loc[student_df["grade"] == "9th"].groupby("school_name")["math_score"].mean()
tenth_reading = student_df.loc[student_df["grade"] == "10th"].groupby("school_name")["math_score"].mean()
eleventh_reading = student_df.loc[student_df["grade"] == "11th"].groupby("school_name")["math_score"].mean()
twelfth_reading = student_df.loc[student_df["grade"] == "12th"].groupby("school_name")["math_score"].mean()

student_df.rename(columns = {"school_name" : " "})

grade_df = pd.DataFrame({"School Name" : school_name, "9th" : ninth_reading, "10th" : tenth_reading, 
                         "11th" : eleventh_reading, "12th" : twelfth_reading})

del grade_df["School Name"]

# del grade_df.index.name

grade_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
    <tr>
      <th>school_name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Bailey High School</td>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
    </tr>
    <tr>
      <td>Cabrera High School</td>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
    </tr>
    <tr>
      <td>Figueroa High School</td>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
    </tr>
    <tr>
      <td>Ford High School</td>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
    </tr>
    <tr>
      <td>Griffin High School</td>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
    </tr>
    <tr>
      <td>Hernandez High School</td>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
    </tr>
    <tr>
      <td>Holden High School</td>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
    </tr>
    <tr>
      <td>Huang High School</td>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
    </tr>
    <tr>
      <td>Johnson High School</td>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
    </tr>
    <tr>
      <td>Pena High School</td>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
    </tr>
    <tr>
      <td>Rodriguez High School</td>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
    </tr>
    <tr>
      <td>Shelton High School</td>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
    </tr>
    <tr>
      <td>Thomas High School</td>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
    </tr>
    <tr>
      <td>Wilson High School</td>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
    </tr>
    <tr>
      <td>Wright High School</td>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
    </tr>
  </tbody>
</table>
</div>



## Scores by School Spending

* Create a table that breaks down school performances based on average Spending Ranges (Per Student). Use 4 reasonable bins to group school spending. Include in the table each of the following:
  * Average Math Score
  * Average Reading Score
  * % Passing Math
  * % Passing Reading
  * Overall Passing Rate (Average of the above two)


```python
#create bins 
school_spending = results_school_summary_df
spending_bins = [0, 585, 615, 645, 675]
group_names = ["<$585", "$585-615", "$615-645", "$645-675"]
student_spending = school_spending["Per Student Budget"].replace("[\$,)]", "" , regex=True)

#change data type to float
per_student_spending = student_spending.astype(float)
per_student_spending

school_spending["Spending Ranges (Per Student)"] = pd.cut(per_student_spending, spending_bins, labels = group_names)
school_spending["Average Math Score"] = school_spending["Average Math Score"].astype(float)
school_spending["Average Reading Score"] = school_spending["Average Reading Score"].astype(float)


school_spending_math = school_spending.groupby("Spending Ranges (Per Student)")["Average Math Score"].mean()
school_spending_reading = school_spending.groupby("Spending Ranges (Per Student)")["Average Reading Score"].mean()

#reset data types to float
school_spending["% Passing Math"] = school_spending["% Passing Math"].astype(float)
school_spending["% Passing Reading"] = school_spending["% Passing Reading"].astype(float)
school_spending["% Overall Passing Rate"] = school_spending["% Overall Passing Rate"].astype(float)

#calculate percentages
spending_pass_math = school_spending.groupby("Spending Ranges (Per Student)")["% Passing Math"].mean() 
spending_pass_reading = school_spending.groupby("Spending Ranges (Per Student)")["% Passing Reading"].mean()
spending_overall_reading = school_spending.groupby("Spending Ranges (Per Student)")["% Overall Passing Rate"].mean()

#set dataframe
results_spending = pd.DataFrame({"Average Math Score": school_spending_math, "Average Reading Score": school_spending_reading,
                                 "% Passing Math": spending_pass_math, "% Passing Reading": spending_pass_reading,
                                 "% Overall Passing Rate": spending_overall_reading})

results_spending = results_spending[["Average Math Score", "Average Reading Score", "% Passing Math", "% Passing Reading",
                                       "% Overall Passing Rate"]]
results_spending
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>Spending Ranges (Per Student)</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>&lt;$585</td>
      <td>83.455399</td>
      <td>83.933814</td>
      <td>93.460096</td>
      <td>96.610877</td>
      <td>95.035486</td>
    </tr>
    <tr>
      <td>$585-615</td>
      <td>83.599686</td>
      <td>83.885211</td>
      <td>94.230858</td>
      <td>95.900287</td>
      <td>95.065572</td>
    </tr>
    <tr>
      <td>$615-645</td>
      <td>79.079225</td>
      <td>81.891436</td>
      <td>75.668212</td>
      <td>86.106569</td>
      <td>80.887391</td>
    </tr>
    <tr>
      <td>$645-675</td>
      <td>76.997210</td>
      <td>81.027843</td>
      <td>66.164813</td>
      <td>81.133951</td>
      <td>73.649382</td>
    </tr>
  </tbody>
</table>
</div>



## Scores by School Size

* Perform the same operations as above, based on school size.


```python
# Sample bins. Feel free to create your own bins.
size_bins = [0, 1000, 2000, 5000]
group_names = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]
```


```python
#create bins 
school_size = results_school_summary_df
size_bins = [0, 1000, 2000, 5000]
group_names = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]
student_size = school_size["Total Students"]

#change data type to float
per_student_spending = student_size.astype(float)
per_student_spending

school_size["School Size"] = pd.cut(per_student_spending, size_bins, labels = group_names)
school_size["Average Math Score"] = school_size["Average Math Score"].astype(float)
school_size["Average Reading Score"] = school_size["Average Reading Score"].astype(float)


school_spending_math = school_size.groupby("School Size")["Average Math Score"].mean()
school_spending_reading = school_size.groupby("School Size")["Average Reading Score"].mean()

#reset data types to float
school_size["% Passing Math"] = school_size["% Passing Math"].astype(float)
school_size["% Passing Reading"] = school_size["% Passing Reading"].astype(float)
school_size["% Overall Passing Rate"] = school_size["% Overall Passing Rate"].astype(float)

#calculate percentages
spending_pass_math = school_size.groupby("School Size")["% Passing Math"].mean() 
spending_pass_reading = school_size.groupby("School Size")["% Passing Reading"].mean()
spending_overall_reading = school_size.groupby("School Size")["% Overall Passing Rate"].mean()

#set dataframe
results_size = pd.DataFrame({"Average Math Score": school_spending_math, "Average Reading Score": school_spending_reading,
                                 "% Passing Math": spending_pass_math, "% Passing Reading": spending_pass_reading,
                                 "% Overall Passing Rate": spending_overall_reading})

results_size = results_size[["Average Math Score", "Average Reading Score", "% Passing Math", "% Passing Reading",
                                       "% Overall Passing Rate"]]
results_size
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>School Size</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Small (&lt;1000)</td>
      <td>83.821598</td>
      <td>83.929843</td>
      <td>93.550225</td>
      <td>96.099437</td>
      <td>94.824831</td>
    </tr>
    <tr>
      <td>Medium (1000-2000)</td>
      <td>83.374684</td>
      <td>83.864438</td>
      <td>93.599695</td>
      <td>96.790680</td>
      <td>95.195187</td>
    </tr>
    <tr>
      <td>Large (2000-5000)</td>
      <td>77.746417</td>
      <td>81.344493</td>
      <td>69.963361</td>
      <td>82.766634</td>
      <td>76.364998</td>
    </tr>
  </tbody>
</table>
</div>



## Scores by School Type

* Perform the same operations as above, based on school type.


```python
 
school_type = results_school_summary_df

# school_type["School Size"] = pd.cut(per_student_spending, size_bins, labels = group_names)
school_type["Average Math Score"] = school_type["Average Math Score"].astype(float)
school_type["Average Reading Score"] = school_type["Average Reading Score"].astype(float)

school_type['School Type'] = school_type['School Type'].map(tuple)

school_type_math = school_type.groupby("School Type")["Average Math Score"].mean()
school_type_reading = school_type.groupby("School Type")["Average Reading Score"].mean()

#reset data types to float
school_type["% Passing Math"] = school_type["% Passing Math"].astype(float)
school_type["% Passing Reading"] = school_type["% Passing Reading"].astype(float)
school_type["% Overall Passing Rate"] = school_type["% Overall Passing Rate"].astype(float)

#calculate percentages
type_pass_math = school_type.groupby("School Type")["% Passing Math"].mean() 
type_pass_reading = school_type.groupby("School Type")["% Passing Reading"].mean()
type_overall_reading = school_type.groupby("School Type")["% Overall Passing Rate"].mean()

#set dataframe
results_type = pd.DataFrame({"Average Math Score": school_type_math, "Average Reading Score": school_type_reading,
                                 "% Passing Math": type_pass_math, "% Passing Reading": type_pass_reading,
                                 "% Overall Passing Rate": type_overall_reading})

results_type = results_type[["Average Math Score", "Average Reading Score", "% Passing Math", "% Passing Reading",
                                       "% Overall Passing Rate"]]
results_type
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>% Overall Passing Rate</th>
    </tr>
    <tr>
      <th>School Type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>(Charter,)</td>
      <td>83.473852</td>
      <td>83.896421</td>
      <td>93.620830</td>
      <td>96.586489</td>
      <td>95.103660</td>
    </tr>
    <tr>
      <td>(District,)</td>
      <td>76.956733</td>
      <td>80.966636</td>
      <td>66.548453</td>
      <td>80.799062</td>
      <td>73.673757</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Description of observable trends

# 1. Based on the data, we can analyze that the Chareter schools performed better than the District schools.
# 2. Schools with smaller number of students performed better in both math and reading
```


```python

```
