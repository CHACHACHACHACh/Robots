import folium
import pandas as pd
import shapely
import overpass
import numpy as np

anime = pd.read_csv('nyc_robots.csv', delimiter=';')

x1=anime['start station latitude'].tolist()
y1=anime['start station longitude'].tolist()
start= anime['start station name']
x2=anime['end station latitude'].tolist()
y2=anime['end station longitude'].tolist()
end= anime['end station name']

i=0
m = folium.Map(location=[40.8, -74])
for i in range(len(anime)):
    folium.Marker([float(x1[i]), float(y1[i])], popup=start[i], icon=folium.Icon(color="green"),).add_to(m)
    folium.Marker([float(x2[i]), float(y2[i])], popup=end[i], icon=folium.Icon(color="red"),).add_to(m)
m