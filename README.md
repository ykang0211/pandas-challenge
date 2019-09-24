# pandas-challenge

# Dependencies and Setup
import pandas as pd

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

merge_df.dtypes

total_number_schools = school_df["school_name"].count()
total_number_students = merge_df["student_name"].count()

# total budget calculates incorrectly, need to talk to TA or Travis
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

school_summary_df = pd.merge(student_df, school_df, on = "school_name")
school_summary_df

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

# Top Five Schools by Passing Rate 
top_five = results_school_summary_df.sort_values("% Overall Passing Rate", ascending = False)
top_five.head()

bottom_five = results_school_summary_df.sort_values("% Overall Passing Rate", ascending = True)
bottom_five.head()


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

# Sample bins. Feel free to create your own bins.
size_bins = [0, 1000, 2000, 5000]
group_names = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]

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

 
school_type = results_school_summary_df

# school_type["School Size"] = pd.cut(per_student_spending, size_bins, labels = group_names)
school_type["Average Math Score"] = school_type["Average Math Score"].astype(float)
school_type["Average Reading Score"] = school_type["Average Reading Score"].astype(float)

# school_type.dtypes
# school_type["School Type"].value_counts()
# help from Travis
# this is a subtle difference: because lists are mutable, 
# they can't be "hash"ed, which is what groupby is using to do the grouping. 
# However, tuples are immutable, and can be hashed
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

# Description of observable trends

# 1. Based on the data, we can analyze that the Chareter schools performed better than the District schools.
# 2. Schools with smaller number of students performed better in both math and reading
