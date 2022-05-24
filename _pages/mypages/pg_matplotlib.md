---
layout: archive
permalink: /misc/matplotlib/
title: How to matplotlib
description: Last update on Oct. 2021
---


## Setting figure

```python
plt.rcParams.update({
        'font.size'           : 18      ,
        'font.sans-serif'     : 'Arial'    ,
        'font.weight'         : 'normal',
        'xtick.major.size'    : 7        ,
        'xtick.minor.size'    : 4        ,
        'xtick.major.width'   : 1.2     ,
        'xtick.minor.width'   : 1.2     ,
        'xtick.labelsize'     : 16      ,
        'xtick.direction'     : 'in'      ,
        'ytick.major.size'    : 7        ,
        'ytick.minor.size'    : 4        ,
        'ytick.major.width'   : 1.2     ,
        'ytick.minor.width'   : 1.2     ,
        'ytick.labelsize'     : 16      ,
        'ytick.direction'     : 'in'      ,
        'xtick.major.pad'     : 3        ,
        'xtick.minor.pad'     : 5        ,
        'ytick.major.pad'     : 3        ,
        'ytick.minor.pad'     : 5        ,
        'savefig.dpi'         : 601      ,
        'text.usetex'         : False     ,
        'axes.linewidth'      : 1.2      })
```

## Setting figure size and dpi

```python
# The column width in PRC is about 6 cm, and the recommended dpi is 1200
fig = plt.figure (figsize = (6,4), dpi=1200)
fig.subplots_adjust(top=0.90,bottom=0.13,right=0.98,left=0.10,hspace=0.10,wspace=0.22)
axs = []
ax1 = fig.add_subplot(1,1,1); axs.append(ax1)
```

## Set labels

```python
ax1.set_xlabel('$S_{\\nu}$ (MeV)')
ax1.set_ylabel('$L$ (MeV)'
```

## vlines and hlines

```python
ax1.axhline (y=0.0 , linewidth=1.0 , color='black' , linestyle='dotted')
ax1.vlines(13.5, -20.0, -13.0, colors="black", linestyles=":", label='')
```

## Arrows

```python
ax1.arrow(xmin, ymin, 0, ymax-ymin, fc='k', ec='k', lw=1.5, 
        head_width=0.1, head_length=0.1, overhang=0.3, 
```

## Annotations

```python
# At the very end, just before saving the figure
matplotlib.rc ('text', usetex=True)
ax1.annotate(r"$2^+$", xy=(17.0,4.0), color='black', ha="left", va="center", fontsize=10)
```

## Save figure
```python
fig.savefig('plot.pdf', bbox_inches='tight', transparent=True)
```

## Numpy
```python
np.set_printoptions(precision=5)
np.set_printoptions(suppress=True)
```

## Pandas
```python
inplace=True changes the original dataframe and returns None. inplace=False returns a copy of the object with the operation performed.

df.reset_index(inplace=True)

df.sort_values(by='XXX', ascending=True,  ignore_index=True); df.sort_values(by=['XXX','xxx'], ascending=[True,False],  ignore_index=True)

df = df.merge(df_a)

handles, labels = ax.get_legend_handles_labels()
leg=ax.legend(handles[:],labels[:],fontsize=14,ncol=2,loc='upper left',frameon=True,shadow=True)

ax1.set_ylabel('XXX',x=0,y=-0.1)

transform=ax.transAxes
```

## Tips
```python
h, l = ax1.get_legend_handles_labels()
leg1=ax1.legend([ h[0],h[1] ],[ l[0],l[1] ], fontsize=14, ncol=1, bbox_to_anchor=(0.4,0.95), \
loc='best',frameon=False,shadow=False,markerscale=1.0, labelspacing=0.5,columnspacing=0.2,handletextpad=0.3)

def formatnum0(x, pos):
    return '$%.1f$' % (x*1e40)
formatter0 = FuncFormatter(formatnum0)
ax1.yaxis.set_major_formatter(formatter0)

ax1.set_yticks([1e-40,1e-39,1e-38,1e-37])
ax1.set_yticklabels(['1','10','10$^2$','10$^3$'])

ax1.fill_between(Xs,Ys_max,Ys_min,alpha=0.5, hatch='/////',facecolor='C9',edgecolor='C0',label='XXX')
Note: if use color='C2', facecolor and edgecolor will not work

ax1.errorbar(np.array([X]),np.array([Y]),yerr=[np.array([dY1]),np.array([dY2])], \
linewidth=0,fmt='s',markersize=6,capsize=4,capthick=1,elinewidth=1,color='b')

df.reset_index(drop=True, inplace=True) # inplace = True: no new and change the original df
```

