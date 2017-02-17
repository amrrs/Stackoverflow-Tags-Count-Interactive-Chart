
##Stack Overflow Tags Count Interctive Chart

###Visualizing Stack Overflow Tags Count using Bokeh + Python


```python
%matplotlib inline
import urllib2
from bs4 import BeautifulSoup as bs
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib.style as style

```


```python
df = {'Language':[],'Tag_Count':[]}

```


```python
def extract_tagged(url):
    #print('Extracting Content')
    content = urllib2.urlopen(url).read()
    soup = bs(content,'html.parser')
     
    for tag in soup.find_all('a',attrs={'class':'post-tag'}):
        df['Language'].append(tag.text)
    for count in soup.find_all('span',attrs={'class':'item-multiplier-count'}):
        df['Tag_Count'].append(count.text)
    

```


```python
for i in range(1,3):
    extract_tagged('http://stackoverflow.com/tags?page='+str(i)+'&tab=popular')    
df['Tag_Count']=[int(i) for i in df['Tag_Count']]

df2= pd.DataFrame(df)
df2

```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Language</th>
      <th>Tag_Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>javascript</td>
      <td>1322430</td>
    </tr>
    <tr>
      <th>1</th>
      <td>java</td>
      <td>1211460</td>
    </tr>
    <tr>
      <th>2</th>
      <td>c#</td>
      <td>1059649</td>
    </tr>
    <tr>
      <th>3</th>
      <td>php</td>
      <td>1037622</td>
    </tr>
    <tr>
      <th>4</th>
      <td>android</td>
      <td>951441</td>
    </tr>
    <tr>
      <th>5</th>
      <td>jquery</td>
      <td>815753</td>
    </tr>
    <tr>
      <th>6</th>
      <td>python</td>
      <td>702187</td>
    </tr>
    <tr>
      <th>7</th>
      <td>html</td>
      <td>624090</td>
    </tr>
    <tr>
      <th>8</th>
      <td>c++</td>
      <td>498218</td>
    </tr>
    <tr>
      <th>9</th>
      <td>ios</td>
      <td>491622</td>
    </tr>
    <tr>
      <th>10</th>
      <td>css</td>
      <td>449688</td>
    </tr>
    <tr>
      <th>11</th>
      <td>mysql</td>
      <td>446022</td>
    </tr>
    <tr>
      <th>12</th>
      <td>sql</td>
      <td>372281</td>
    </tr>
    <tr>
      <th>13</th>
      <td>asp.net</td>
      <td>309594</td>
    </tr>
    <tr>
      <th>14</th>
      <td>objective-c</td>
      <td>273279</td>
    </tr>
    <tr>
      <th>15</th>
      <td>ruby-on-rails</td>
      <td>267520</td>
    </tr>
    <tr>
      <th>16</th>
      <td>.net</td>
      <td>247565</td>
    </tr>
    <tr>
      <th>17</th>
      <td>c</td>
      <td>242388</td>
    </tr>
    <tr>
      <th>18</th>
      <td>angularjs</td>
      <td>220785</td>
    </tr>
    <tr>
      <th>19</th>
      <td>iphone</td>
      <td>216758</td>
    </tr>
    <tr>
      <th>20</th>
      <td>arrays</td>
      <td>213383</td>
    </tr>
    <tr>
      <th>21</th>
      <td>sql-server</td>
      <td>191419</td>
    </tr>
    <tr>
      <th>22</th>
      <td>json</td>
      <td>187001</td>
    </tr>
    <tr>
      <th>23</th>
      <td>ruby</td>
      <td>176818</td>
    </tr>
    <tr>
      <th>24</th>
      <td>r</td>
      <td>170712</td>
    </tr>
    <tr>
      <th>25</th>
      <td>ajax</td>
      <td>163189</td>
    </tr>
    <tr>
      <th>26</th>
      <td>regex</td>
      <td>161942</td>
    </tr>
    <tr>
      <th>27</th>
      <td>node.js</td>
      <td>160166</td>
    </tr>
    <tr>
      <th>28</th>
      <td>xml</td>
      <td>152779</td>
    </tr>
    <tr>
      <th>29</th>
      <td>asp.net-mvc</td>
      <td>150274</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>186</th>
      <td>spring</td>
      <td>104353</td>
    </tr>
    <tr>
      <th>187</th>
      <td>html5</td>
      <td>99885</td>
    </tr>
    <tr>
      <th>188</th>
      <td>multithreading</td>
      <td>94466</td>
    </tr>
    <tr>
      <th>189</th>
      <td>git</td>
      <td>81724</td>
    </tr>
    <tr>
      <th>190</th>
      <td>oracle</td>
      <td>80351</td>
    </tr>
    <tr>
      <th>191</th>
      <td>bash</td>
      <td>79683</td>
    </tr>
    <tr>
      <th>192</th>
      <td>forms</td>
      <td>79080</td>
    </tr>
    <tr>
      <th>193</th>
      <td>image</td>
      <td>78246</td>
    </tr>
    <tr>
      <th>194</th>
      <td>mongodb</td>
      <td>77513</td>
    </tr>
    <tr>
      <th>195</th>
      <td>facebook</td>
      <td>77273</td>
    </tr>
    <tr>
      <th>196</th>
      <td>vba</td>
      <td>76476</td>
    </tr>
    <tr>
      <th>197</th>
      <td>twitter-bootstrap</td>
      <td>76445</td>
    </tr>
    <tr>
      <th>198</th>
      <td>osx</td>
      <td>75235</td>
    </tr>
    <tr>
      <th>199</th>
      <td>algorithm</td>
      <td>72916</td>
    </tr>
    <tr>
      <th>200</th>
      <td>winforms</td>
      <td>72327</td>
    </tr>
    <tr>
      <th>201</th>
      <td>apache</td>
      <td>70032</td>
    </tr>
    <tr>
      <th>202</th>
      <td>matlab</td>
      <td>68705</td>
    </tr>
    <tr>
      <th>203</th>
      <td>performance</td>
      <td>67784</td>
    </tr>
    <tr>
      <th>204</th>
      <td>entity-framework</td>
      <td>65151</td>
    </tr>
    <tr>
      <th>205</th>
      <td>swing</td>
      <td>65048</td>
    </tr>
    <tr>
      <th>206</th>
      <td>postgresql</td>
      <td>65032</td>
    </tr>
    <tr>
      <th>207</th>
      <td>visual-studio</td>
      <td>64854</td>
    </tr>
    <tr>
      <th>208</th>
      <td>python-2.7</td>
      <td>63613</td>
    </tr>
    <tr>
      <th>209</th>
      <td>scala</td>
      <td>62468</td>
    </tr>
    <tr>
      <th>210</th>
      <td>linq</td>
      <td>62168</td>
    </tr>
    <tr>
      <th>211</th>
      <td>hibernate</td>
      <td>61346</td>
    </tr>
    <tr>
      <th>212</th>
      <td>list</td>
      <td>61315</td>
    </tr>
    <tr>
      <th>213</th>
      <td>css3</td>
      <td>61139</td>
    </tr>
    <tr>
      <th>214</th>
      <td>excel-vba</td>
      <td>57296</td>
    </tr>
    <tr>
      <th>215</th>
      <td>qt</td>
      <td>56533</td>
    </tr>
  </tbody>
</table>
<p>216 rows × 2 columns</p>
</div>




```python
style.use('ggplot')

sorted_short_df = df2.sort_values(by='Tag_Count',ascending=False).head(20).set_index('Language')
#sorted_short_df.plot(kind='bar')

sorted_short_df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tag_Count</th>
    </tr>
    <tr>
      <th>Language</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>javascript</th>
      <td>1322436</td>
    </tr>
    <tr>
      <th>javascript</th>
      <td>1322430</td>
    </tr>
    <tr>
      <th>javascript</th>
      <td>1322430</td>
    </tr>
    <tr>
      <th>java</th>
      <td>1211466</td>
    </tr>
    <tr>
      <th>java</th>
      <td>1211460</td>
    </tr>
    <tr>
      <th>java</th>
      <td>1211460</td>
    </tr>
    <tr>
      <th>c#</th>
      <td>1059652</td>
    </tr>
    <tr>
      <th>c#</th>
      <td>1059649</td>
    </tr>
    <tr>
      <th>c#</th>
      <td>1059649</td>
    </tr>
    <tr>
      <th>php</th>
      <td>1037622</td>
    </tr>
    <tr>
      <th>php</th>
      <td>1037622</td>
    </tr>
    <tr>
      <th>php</th>
      <td>1037622</td>
    </tr>
    <tr>
      <th>android</th>
      <td>951441</td>
    </tr>
    <tr>
      <th>android</th>
      <td>951441</td>
    </tr>
    <tr>
      <th>android</th>
      <td>951440</td>
    </tr>
    <tr>
      <th>jquery</th>
      <td>815756</td>
    </tr>
    <tr>
      <th>jquery</th>
      <td>815753</td>
    </tr>
    <tr>
      <th>jquery</th>
      <td>815753</td>
    </tr>
    <tr>
      <th>python</th>
      <td>702196</td>
    </tr>
    <tr>
      <th>python</th>
      <td>702187</td>
    </tr>
  </tbody>
</table>
</div>




```python
from bokeh.charts import Bar, output_file, show
from bokeh.embed import components
from bokeh.models import HoverTool

hover = HoverTool(names=["Language", "Tag_Count"])

plot = Bar(df2, label='Language', values='Tag_Count', title="Stack Overflow Popular Tags", width=1000,legend=False,tooltips=[('Tag_Count:', '@height'), ('Language:', '@Language')])

#output_file("stack_tag_sorted.html",title='Stack Overflow Popular Tags')

script,div = components(plot)

js = open('chart1.js','w')
js.write(script)
js.close()


css = open('style1.css','w')
css.write(div)
css.close()

#show(plot)
```
