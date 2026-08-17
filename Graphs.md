```python
import matplotlib.pyplot as plt
import numpy as np
from matplotlib.colors import LinearSegmentedColormap

import matplotlib
import matplotlib as mpl
from matplotlib.pyplot import color_sequences

Type_of_support = ["Invasive MV", "Non-Invasive MV", "Vasopressors ", "Renal replacement therapy "]
Age_groups = ["65-74", "75-84", "≥85"]

Percentages = np.array([[36.7, 35.9, 34.3],
                        [0.7, 0.9, 1.3],
                        [34.2, 32.6, 27.9],
                        [6.0, 7.2, 7.8]
])


fig, ax = plt.subplots()
im = ax.imshow(Percentages)

# Show all ticks and label them with the respective list entries
ax.set_xticks(range(len(Age_groups)), labels=Age_groups,
              rotation=45, ha="right", rotation_mode="anchor")
ax.set_yticks(range(len(Type_of_support)), labels=Type_of_support)

# Loop over data dimensions and create text annotations.
for i in range(len(Type_of_support)):
    for j in range(len(Age_groups)):
        text = ax.text(j, i, Percentages[i, j],
                       ha="center", va="center", color="w")
# Graph color
colors = ["#ff0000", "#ffff00", "#00ff00", "#00ffff", "#0000ff"]
custom_cmap = LinearSegmentedColormap.from_list("custom_cmap", colors)
im = ax.imshow(Percentages, cmap=custom_cmap)
#Color bar
cbar = ax.figure.colorbar(im, ax=ax)
cbar.set_label("Percentage")

ax.set_title("Support during index ICU stay")
fig.tight_layout()
plt.show()
```


    
![png](Heatmap_files/Heatmap_0_0.png)
    



```python
import matplotlib.pyplot as plt
import numpy as np
from matplotlib.colors import LinearSegmentedColormap

import matplotlib
import matplotlib as mpl
from matplotlib.pyplot import color_sequences

Type_of_support = ["Invasive MV", "Non-Invasive MV", "Vasopressors ", "Renal replacement therapy "]
Age_groups = ["65-74", "75-84", "≥85"]

Percentages = np.array([[36.7, 35.9, 34.3],
                        [0.7, 0.9, 1.3],
                        [34.2, 32.6, 27.9],
                        [6.0, 7.2, 7.8]
])


fig, ax = plt.subplots()
im = ax.imshow(Percentages)

# Show all ticks and label them with the respective list entries
ax.set_xticks(range(len(Age_groups)), labels=Age_groups,
              rotation=45, ha="right", rotation_mode="anchor")
ax.set_yticks(range(len(Type_of_support)), labels=Type_of_support)

# Loop over data dimensions and create text annotations.
for i in range(len(Type_of_support)):
    for j in range(len(Age_groups)):
        text = ax.text(j, i, Percentages[i, j],
                       ha="center", va="center", color="w")
# Graph color
im = ax.imshow(Percentages, cmap= "viridis", vmin=0, vmax=40)
#Color bar
cbar = ax.figure.colorbar(im, ax=ax)
cbar.set_label("Percentage")

ax.set_title("Support during index ICU stay")
fig.tight_layout()
plt.show()
```


    
![png](Heatmap_files/Heatmap_1_0.png)
    



```python
import pandas as pd
import matplotlib.pyplot as plt
# DEFINE Data
catagories = ["Not at all","Unlikely", "Likely", "Very likely"]
intention_counts = [50, 27, 45, 30]
substitute_counts = [45, 22, 42, 43]
# data frame
df_plot = pd.DataFrame({
          "Catagory": catagories,
          "Intention": intention_counts,
          "Substitute": substitute_counts
          })
# DEFINE y based on plot
y = range(len(df_plot))
plt.figure(figsize = (8, 4), dpi = 150)

# the connection
for i in y:
    plt.plot(
        [df_plot["Intention"][i], df_plot["Substitute"][i]],
        [i, i],
        linestyle=':',
        color= '#e6c870',
        linewidth = 1
    )
# dottes
plt.scatter(df_plot["Intention"], y, s=100, color='#e6c870', label="Intention to use")
plt.scatter(df_plot["Substitute"], y, s=100, color='#7abcd6', label="Use as substitute")
# label names
plt.yticks(y, df_plot["Catagory"])
plt.xlabel("Number of participants")
plt.ylabel("Response category")
plt.legend(frameon=False)
plt.title("Intention vs Likelihood of Using Nicotine Pouches (N=152)")
plt.tight_layout()
plt.show()
```


    
![png](Heatmap_files/Heatmap_2_0.png)
    



```python
import matplotlib.pyplot as plt

labels = 'Lung Cancer', 'Diabetes', 'CVD'
sizes = [37,10,53]
colors = ['#EBCB86', '#D1A74F', '#B88323']
fig, ax = plt.subplots(figsize=(6, 6), dpi=150)
plt.title("Perceived Health Risks Associated with Nicotine Pouch Use — A Cross-Sectional Study, 2025, Riyadh, Saudi Arabia (N = 840)")
ax.pie(sizes, labels=labels)
plt.show()
```


    
![png](Heatmap_files/Heatmap_3_0.png)
    

