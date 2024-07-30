# An Analysis and Visualization of Speed Camera across Taiwan, Penghu, Kinmen and Matsu

```python 
import pandas as pd
import plotly.express as px
pd.options.plotting.backend = "plotly"

df = pd.read_csv("NPA_TD1.csv")
"
```
```python
data = {'OtherColumn': [1,28],
'highway': [4,5,6,7,8,9,10,11,12]
}
city_df = df.groupby(["CityName"]).size().reset_index(name='counts')

# Show total individual counts for each county
indices_to_exclude = [1, 4, 5, 6, 7, 8, 9, 10, 11, 12, 28]

# Drop the specified rows
# Drop the specified rows
df_filtered = city_df.drop(indices_to_exclude)

# Sort by counts in descending order
df_filtered = df_filtered.sort_values(by='counts', ascending=False)

# Create a bar graph
fig = px.bar(df_filtered, x='CityName', y='counts', 
             title='測速相機分佈 - 按數量降序排列', 
             labels={'CityName': '城市名稱', 'counts': '數量'})
fig.show()
```
```python
# Remove rows with non-numeric Longitude or Latitude
df_cleaned = df[df['Longitude'].apply(lambda x: isinstance(x, (int, float)) or str(x).replace('.', '', 1).isdigit())]
df_cleaned = df_cleaned[df_cleaned['Latitude'].apply(lambda x: isinstance(x, (int, float)) or str(x).replace('.', '', 1).isdigit())]

# Convert Longitude and Latitude to float
df_cleaned["Longitude"] = df_cleaned["Longitude"].astype(float)
df_cleaned["Latitude"] = df_cleaned["Latitude"].astype(float)

# Print the cleaned DataFrame

# Create a scatter mapbox plot using available columns
fig2 = px.scatter_mapbox(df_cleaned, lat="Latitude", lon="Longitude",
                         hover_name="Address",  # Change to an existing column
                         hover_data=["direct", "limit"],  # Use existing columns
                         mapbox_style="open-street-map")
fig2.update_layout(margin={"r": 0, "t": 0, "l": 0, "b": 0})
fig2.show()

```