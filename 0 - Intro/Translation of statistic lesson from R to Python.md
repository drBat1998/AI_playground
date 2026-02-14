# Завдання 01. Робота з даними
1. Підготувати дані до імпорту (узгодити розділювач дрібної частини, перевірити коректність та зручність використання заголовків стовпчиків - вони будуть назвами ваших змінних).
2. Імпортувати дані з доданої таблиці.
3. Перетворити на фактори усі змінні, які можуть бути використаними як фактори.
4. Описати демографічний склад кожної з чотирьох груп: стать, вік, зріст та вагу. Дані представити у текстовому файлі (гугл документ). В нього вставити код з R (які функції використовували), результат виконання та текстовий опис.

``` R
library(tidyverse)
library(readxl)

```R
Lesson1 <- read_excel("Lesson1.xlsx", col_types = c("text", 
    "numeric", "numeric", "numeric", "text", 
    "numeric", "numeric"))
View(Lesson1)

Lesson1$Gender <- as.factor(Lesson1$Gender)

Lesson1$Groups[str_detect(Lesson1$Group, str_c("contr", collapse = "|"))] <- "control"
Lesson1$Groups[str_detect(Lesson1$Group, str_c("hunt", collapse = "|"))] <- "hunt"
Lesson1$Groups[str_detect(Lesson1$Group, str_c("park", collapse = "|"))] <- "park"
Lesson1$Groups[str_detect(Lesson1$Group, str_c("als", collapse = "|"))] <- "als"

Lesson1$Groups <- as.factor(Lesson1$Groups)


## Опис за гендером
Lesson1 %>% 
  select(Groups, Gender) %>% 
  group_by(Groups, Gender) %>% 
  summarize(number = n())

chuj = Lesson1 %>% 
  select(Groups, Age) %>% 
  drop_na() %>% 
  group_by(Groups) %>%
  summarize(Mean = mean(Age),
            Std = sd(Age),
            Median = median(Age), 
            Min = min(Age), 
            Max = max(Age), 
            IQR =IQR(Age) )

# Графік розподілу за віком
ggplot(Lesson1, aes(x = Groups, y = Age, fill = Groups)) +
  geom_boxplot() +
  labs(title = "Розподіл віку по групах", y = "Вік") +
  theme_minimal()
```


``` python
import pandas as pd

data = pd.read_excel('tmp.xlsx', index_col=0,
              dtype={'Name': str, 'Value': float}) 


# Assuming Lesson1 is a DataFrame and 'Group' and 'Groups' are columns
Lesson1['Groups'] = Lesson1['GROUP/PAT']  # Initialize 'Groups' with the same values as 'Group'

Lesson1.loc[Lesson1['GROUP/PAT'].str.contains('contr', case=False, na=False), 'Groups'] = 'control'
Lesson1.loc[Lesson1['GROUP/PAT'].str.contains('hunt', case=False, na=False), 'Groups'] = 'hunt'
Lesson1.loc[Lesson1['GROUP/PAT'].str.contains('park', case=False, na=False), 'Groups'] = 'park'
Lesson1.loc[Lesson1['GROUP/PAT'].str.contains('als', case=False, na=False), 'Groups'] = 'als'


Lesson1["Groups"].astype('category')

import numpy as np

Lesson1.pivot_table(index="Groups", 
                    values=["AGE(YRS)"], 
                    aggfunc=[np.mean, np.median])
                
import seaborn as sns
import matplotlib.pyplot as plt

# Побудова графіку
plt.figure(figsize=(8, 6))
sns.boxplot(data=Lesson1, x="Groups", y="AGE(YRS)", hue="Groups", dodge=False)

# Додаткові налаштування
plt.title("Розподіл віку по групах")
plt.ylabel("Вік")
plt.xlabel("Група")
plt.xticks(rotation=45)
plt.legend(title="Група", loc="upper right")
sns.despine()
plt.tight_layout()
plt.show()
```

What should I learn 
pd.read_excel
.loc
.str.contains
.groupby()
pivot_table()
.groupby().agg()


# Завдання 02. Нормальність розподілу та перевірка статистичних гіпотез
``` R
# Нормальність за зростом
Lesson1 %>%
select(Height, Groups) %>%
ggplot(aes(Height, fill = Groups))+
geom_histogram(binwidth=0.05)+
facet_wrap(~Groups, scales = "free_y", )+
ggtitle("Гістограма розподілу по зросту")


Lesson1 %>%
select(Height, Groups) %>%
drop_na() %>%
ggplot(aes(sample = Height, colour = Groups))+
stat_qq_band()+
stat_qq_point(size =2)+
stat_qq_line()+
facet_wrap(~Groups, scales = "free_y", )+
ggtitle("QQ plot по зросту")

nor.test(Height ~ Groups, data = Lesson1)


```

``` python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats


Lesson1 = pd.read_excel('/content/Lesson1.xlsx')
Lesson1.head()

# Assuming Lesson1 is a DataFrame and 'Group' and 'Groups' are columns
Lesson1['Groups'] = Lesson1['GROUP/PAT']  # Initialize 'Groups' with the same values as 'Group'

Lesson1.loc[Lesson1['GROUP/PAT'].str.contains('contr', case=False, na=False), 'Groups'] = 'control'
Lesson1.loc[Lesson1['GROUP/PAT'].str.contains('hunt', case=False, na=False), 'Groups'] = 'hunt'
Lesson1.loc[Lesson1['GROUP/PAT'].str.contains('park', case=False, na=False), 'Groups'] = 'park'
Lesson1.loc[Lesson1['GROUP/PAT'].str.contains('als', case=False, na=False), 'Groups'] = 'als'


Lesson1["Groups"].astype('category')
Lesson1["gender"].astype('category')


g = sns.FacetGrid(Lesson1, col="Groups")
g.map_dataframe(sns.histplot, x="HEIGHT(meters)")


sm.qqplot(Lesson1["HEIGHT(meters)"])
plt.show()

from statsmodels.graphics.gofplots import qqplot
from scipy.stats.distributions import norm
qqplot(Lesson1["HEIGHT(meters)"], line='s', dist=norm)
plt.show()


import numpy as np
from scipy import stats
shapiro_test = stats.shapiro(Lesson1["HEIGHT(meters)"])
shapiro_test.pvalue
```