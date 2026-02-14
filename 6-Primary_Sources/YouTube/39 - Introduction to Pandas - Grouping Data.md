Title: 39 - Introduction to Pandas - Grouping Data
Author: [[DigitalSreeni]]
Tags: #python #youtube 

[[pandas]]

# Notes
``` python
df = pd.read_csv("")

df.rename(columns ={"Unanmed":"Image_set"})
df.drop("Manual", axis =1)

group_by_file = df.groupby(by = ["Image_set"])
group_by_count = group_by_file.coun()
group_by_avg = group_by_file.mean()

df["columns"].corr(df["Autho_th_2"])

df.head()
```
# Links
next: [[40 - Introduction to Pandas - Dealing with missing (null) data]]
link: https://youtu.be/p7KyukHE9xU?si=ioJ8n6k5GK8cm1sR