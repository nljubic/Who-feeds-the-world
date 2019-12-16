## Introduction <a name="preface"></a>

### What are the insights of this data story?

<div style="float: right; width: 45%; margin: 5% 5% 5% 5%;" w3-include-html="plots/wordcloud2.html"></div>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Since the Neolithic Revolution, agriculture **feeds the world's population**. Even today, the agricultural sector **employs a large part of humanity** and is a **major point of the economy** of developed and developing countries. In the history of mankind, the **economic growth of countries** has almost always been accompanied by the development of agriculture and the **agricultural economy**, *i.e.* **production, imports and exports**.

<div style="clear: right; width: 100%;"></div>

### Which important events had a significant influence on the agriculture and the economy for the historical period from 1970 to 2015?

<div style="float: left; width: 45%; margin: 5% 5% 5% 5%;" w3-include-html="plots/ussrdiss.html"></div>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; There was the **Cold war** from 1945 to 1990 with two **economic superpowers** (USA and USSR). The USSR had been dissolved in 1991. The Japanese economic miracle occured from 1945 to 1990 and allowed Japan to come out of the disastrous state in which it was at the exit of the WW2 and become one of the worlds largest economies. There have been 2 big oil crises, in 1973 and 1979. There have been many wars (Middle East wars 1973-2000 e.g. Yom Kippur War 1973, Islamic Revolution in Iran 1979, Iran–Iraq war 1980-1988, Gulf war 1990-1991, Yugoslav wars 1991-2001...). The **third Agricultural Revolution** (also known as Green revolution) occurs form 1960 to 1990 and improved agricultural productions thanks to fertilizers and chemicals.

<div style="clear: left; width: 100%;"></div>

### Which countries have highest GDP? How did GDP evolved during the last decades?

<div style="float: right; width: 45%; margin: 5% 5% 5% 5%;"> 
  <div class="slidecontainer">
    <input type="range" min="1970" max="2015" value="2000" class="slider" id="myRange">
    <span id="map"></span>
  </div>
  <script>
    var slider = document.getElementById("myRange");
    var output = document.getElementById("map");
    output.innerHTML = slider.value.toString()+'\n<object style="width: 100%; height: 400px;" type="text/html" data="plots/'+slider.value.toString()+'GDP.html" ></object>';
    slider.oninput = function() {
      output.innerHTML = this.value.toString()+'\n<object style="width: 100%; height: 400px;" type="text/html" data="plots/'+this.value.toString()+'GDP.html" ></object>'
    }
  </script>
  <style>
.slidecontainer {
  width: 100%;
}

.slider {
  -webkit-appearance: none;
  width: 100%;
  height: 15px;
  border-radius: 5px;
  background: #d3d3d3;
  outline: none;
  opacity: 0.7;
  -webkit-transition: .2s;
  transition: opacity .2s;
}

.slider:hover {
  opacity: 1;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #4CAF50;
  cursor: pointer;
}

.slider::-moz-range-thumb {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #4CAF50;
  cursor: pointer;
}
</style>
</div>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; In 1970, the countries with highest GDP were **United States**, **Germany**, **Japan**, **France**, **United Kingdom** and **Italy**. Japan overtook Germany in 1971. Around the 90s, Italy and UK have been fighting for 5th place in the ranking. From 1996 to 2006 the UK surpassed France. China entered the top 6 in 1999 in place of Italy and got 2nd in ranking in 2009. In average, **GDP increased** during this period.

<div style="clear: right; width: 100%;"></div>

### What is the structure of international trade ?

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The GDP are **highly correlated** from one country to another. Globally, they **almost all increased the same way**. This can be explain by the fact that countries have **strong enough trading relations** to make the GDP evolve the same way. Furthermore, one can identify **main regions** in which the trading relations are more important.

## Agricultural and economical features <a name="sources"></a>

### What are the most important features in the sense of the most influence on the Gross Domestic Product ? 

	In order to discover those features we proceed with different features selection methods: 
- Knowledge based: 
We have at out disposal three different kind of features: production, import export. E.g. : The import of maize in tonnes (for all countries,  every year). The export of avocado (for all countries, every year). 
Firstly we only look at the production features. From those we only select a subset. They are selected according to the amount they contribute to the total of the world production. We select the top 20 features, ie the 20 features that contribute the most to the total amount  of produced goods in the world. 
Secondly, we select in the import and export type features the corresponding features to the production type. We end up with 60 features in total, 20 production type, 20 import type and 20 export type. 

We proceed after to an other selection method. We are interested in features that are correlated to the GDP in order to have an interpretable model. 
- Filter method:

We decide to only keep features that are sufficiently correlated to the GDP. We choose a decide a threshold to reduce to approximately 10 features.

- Embedded method:

We fit a LASSO model. It does, while fitting, a feature selection by putting relevant weights to the kept features and a zero weight to the rejected features.  

We find that the  goods that most influences the GDP are soybean, tomatoes, Maize, Wheat , Cattle live animals and pigs amongst other. 

It is an interesting result that is easily understandable. Take soybean for example. This crop is one of the most produced. The mains exporter are the US, Brasil and Argentina and the main importer is China. Around 330 millions tonnes of soybean was produced in 2018. It is vastly used to feed animals. It is thus coherent to see such an important good be selected by our model. We see also that wheat, oats, cattle live and pigs are present. This again is easily understandable. It is sufficient to look at our eating habit to convince ourself that those goods plays an important role in the GDP. Below is the full list of the selected features,. 

	- Soybeans Crops Production tonnes
	- Tomatoes Crops Production tonnes
	- Maize Crops Production tonnes
	- Turkeys Livestock production Head
	- 'Maize Food export quantities tonnes
	- Maize, green Food export quantities tonnes
	- Wheat Food export quantities tonnes
	- Cattle Live animals import quantities Head
	- Oats Food import quantities tonnes
	- Pigs Live animals import quantities Head
	- Tomatoes Food import quantities tonnes
	- Turkeys Live animals import quantities Head

## Improve economy with agriculture <a name="results"></a>

### What is green maize?

It’s maize that is mainly harvested so it can be either directly fed to animals or conserved through “silage” and fed to them in winter. Maize is native to central America and thanks to genetic selection & hybridization it can now be grown everywhere in the world. Among the forage foods that are grown for animal feed, they’re very high energy and easy maintenance, since they only need to be harvested once. They also require high fertilizer, herbicide and pesticide levels and 

### Which countries are net exporters of green maize??
We see that in 1980 no country in the world was a strong net exporter of green maize. Starting from the mid 80s.

### Which countries are net importers of tomatoes?

### Which countries import oats?

## Conclusion <a name="conclusion"></a>

<!--- <div w3-include-html="plots/wordcloud1.html"></div> -->

<!--- <div w3-include-html="plots/map2.html"></div> -->

<!--- <div w3-include-html="plots/map1.html"></div> -->

