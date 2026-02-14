Title: 40 - Introduction to Pandas - Dealing with missing (null) data
Author: [[DigitalSreeni]]
Tags: #python #youtube 

[[pandas]]


# Notes
``` python
df.isnull().sum()

df.drop("Manual")
df.dropna()

df["Manual"].fillna(100, inplace = True)
df["Manual"] = df.apply(lambda row: (round(row["second"]/3)))

```
# Links
next: [[41 - Introduction to Pandas - Plotting]]
link: https://youtu.be/0_mGopGP2dQ?si=RhEKzpBRNA2V40vQ