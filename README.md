# Amazon Item Look Up

ItemLookUp is a simple Java class to scrape data for products in the Amazon store.<br>
For each item you should be able to get the following data: title, category, availability, formatted price, price value, url 
and ASIN code.

## Using the ItemLookUp class

You can get data for a single product or for a list of products.<br>
Each item is identified by its url.

```
// Use ItemLookUp(String) to get data for a single product.
// Use ItemLookUp(List<String>) to get data for a list of products.
```

The constructor loads the source code from each url and then saves it.<br>
<br>
Since it's more efficient to load the source code from each url in sequence, if you want to get the data for more than one 
product, it's suggested to use the second constructor as seen above.<br>
<br>
Note that connections shouldn't be too frequent. The second contructor automatically sets a waiting time between each 
connection. If you want, you can change the amount of time to wait, by calling the following constructor: 

```
// Use ItemLookUp(List<String>, long) to get data for a list of products<br> 
// and to wait the desired amount of time (in millis) between each connection.
```

When you have loaded all the source codes, you can parse the data by calling the following methods:

```
// List<String> getFormattedPrices()
// List<Float> getPriceValues()
// List<String> getCategories()
// List<String> getAvailabilities()
// List<String> getTitles()
// List<Item> getItems()
// Item getItem()
```

The last two methods let you get all the data for the complete collection of products you selected in the constructor, or for
just the first item. If you used the first contructor (by calling the class for just one product), it's suggested to use the
last method.

## The Item class

The last two methods return a list of Item, or an Item. Each Item collects all the data the ItemLookUp class could scrape from 
the Amazon web pages.<br>
<br>
Use the following methods to get the data from an Item object:

```
// String getTitle()
// String getCategory()
// String getAvailability()
// String getFormattedPrice()
// Float getPriceValue()
// String getItemUrl()
// String getAsinCode()
```

## Importing in your Android Studio project

Edit the <i>build.gradle (Project: your-project-name)</i> file in your Android Studio project, by adding this line:

```
maven { url 'https://jitpack.io' }
```

Add the line in the <i>allprojects > repositories</i> block. You should get something like this:

```
allprojects {
    repositories {
        jcenter()
        maven { url 'https://jitpack.io' }
    }
}
```

Edit the <i>build.gradle (Module: app)</i> file in your Android Studio project, by adding this line:

```
compile 'com.github.alessiovierti:amazon-item-lookup:-SNAPSHOT'
```

Add the line in the <i>dependencies</i> block. You should get something like this:

```
dependencies {
    // [...]
    compile 'com.github.alessiovierti:amazon-item-lookup:-SNAPSHOT'
}
```

Finally, sync the project and rebuild it.<br>
If you get any errors, try cleaning the project (<i>Build > Clean Project</i>).

## Built with

* [jsoup](https://jsoup.org) - The library used

## Authors

* **Alessio Vierti** - *Initial work*

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Know limitations

* The ItemLookUp class should work for the american and italian store. The currencies supported are euros and dollars, so you 
shouldn't try to get currency data from other stores. All the other data should be scraped fine.
