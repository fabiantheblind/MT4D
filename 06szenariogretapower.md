---
layout: twitterbootstraped
title: Szenario Great Power
bodyid: usage
---

<a name="10"></a>
###3.3 Das Beispiel greatPower
Ein weiters Skript, _greatPower.jsx_, welches aus nur einer Befehlszeile besteht und dennoch mächtig und auch ein wenig gefährlich ist.  
Wenn bei der Entwicklung eines anderen Skripts immer wieder neue Dokumente erzeugt werden, kann es schnell passieren, dass 10, 20 oder sogar 50 Dokumente geöffnet sind. Die Oberfläche von InDesign bietet nicht die Möglichkeit, alle geöffneten Dokumente zu schließen ohne zu speichern. Das bedeutet, dass bei 50 Dokumenten 50 mal beim Schließen entweder gespeichert, oder das Dokument verworfen werden muss. Mit _greatPower.jsx_ ist das möglich. Um dies auszuprobieren, erzeugen wir ein paar Dokumente mit dem Skript _createDocuments.jsx_. Es hat eine stark verkürzt Schreibweise und verwendet eine andere Art von Schleife: die `while` Schleife.  

[![Algo create Doc](images/algocreatedoc_thumb.jpg)](images/algocreatedoc.jpg)  

<script src="https://gist.github.com/2651812.js"> </script>

{% comment %}
	{% highlight js %}
		// createDocuments.jsx
		var counter = 0;
		var numberOfDocuments = 22;
		while(counter <= numberOfDocuments){
		app.documents.add({
		    documentPreferences:{
		        pageWidth:100,pageHeight:100
		        }
		    });
		var tf = app.activeDocument.pages.item(0).textFrames.add({
		    geometricBounds:[10,10,90,90],
		    contents:String(counter) + "Hello World"
		    });
		tf.characters.everyItem().properties = {
		    pointSize:42
		    };
		counter++;
		}
	{% endhighlight %}
{% endcomment %}


Um diese 23 Dokumente wieder zu schließen, benutzen sie "greatPower-I.jsx".  

[![Algo Great Power](images/algogreatpower_thumb.jpg)](images/algogreatpower.jpg)  

<script src="https://gist.github.com/2651815.js"> </script>

{% comment %}
	{% highlight js %}
	// Like Uncle Ben saz: "With great power comes great responsability!"
	app.documents.everyItem().close(SaveOptions.NO);
	{% endhighlight %}
{% endcomment %}

