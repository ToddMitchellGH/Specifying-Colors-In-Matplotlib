# Specifying-Colors-In-Matplotlib
### This is a repository of ideas on how to make useful color plots.
<br>
<br>


Matplotlib has many preset colormaps (from <a href="https://matplotlib.org/stable/users/explain/colors/colormaps.html">here</a>):
![alt text](https://matplotlib.org/stable/_images/sphx_glr_colormaps_002_2_00x.png)
<br>

The basic code here I got from somewhere else, StackOverflow most likely.  My goal is to make just the code one needs available in one place.
<p align='center'>
<img src="Create_Blues_colormap.png" align="center" width=750>
</p>
<br>

</rb>
The "Blues" colormap has the following Red-Green-Blue (RGB) decomposition:
<p align='center'>
<img src="matplotlib_blues_rgb_decomposition.png" align="center" width=750>
</p>
I don't like how the blue saturates so much at the highest values.  Matplotlib doesn't explain how they came up with their colormaps.  In the above link, they claim that "Blues" is "perceptually uniform," but I don't see it.  From looking at the RGB decomposition, it seems that it would easy to get the B-values of the colormap to decrease linearly for the highest values.
<br>

Once you have found a colormap you like, you need the following code to use it in a filled contour diagram:

<code>
cmap = colors.ListedColormap( newcmp.colors )
norm = colors.BoundaryNorm( contours, cmap.N )

cartopygcs = ax.contourf( xgrid2, ygrid2, sumfdat/10, \
            cmap=cmap, levels=contours, norm=norm, transform=ccrs.PlateCarree(), zorder=0 )
In particular, "cmap=cmap, levels=contours, norm=norm" 
where 
contours = np.array( [ 0, 1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024 ] )
</code>

