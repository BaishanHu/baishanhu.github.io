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

