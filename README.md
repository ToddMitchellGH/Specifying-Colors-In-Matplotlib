# Specifying-Colors-In-Matplotlib
### This is a repository of ideas on how to make useful color plots.
<br>
<br>


Matplotlib has many preset colormaps: 
![alt text](https://matplotlib.org/stable/_images/sphx_glr_colormaps_002_2_00x.png)
<br>

![alt text](https://github.com/ToddMitchellGH/Specifying-Colors-In-Matplotlib/blob/master/Create Blues colormap.png)



cmap = colors.ListedColormap( newcmp.colors )
norm = colors.BoundaryNorm( contours, cmap.N )

cartopygcs = ax.contourf( xgrid2, ygrid2, sumfdat/10, \
            cmap=cmap, levels=contours, norm=norm, transform=ccrs.PlateCarree(), zorder=0 )
In particular, "cmap=cmap, levels=contours, norm=norm" 
where 
contours = np.array( [ 0, 1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024 ] )

