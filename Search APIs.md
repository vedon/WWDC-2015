#Search APIs－App Deep Linking

在iOS 9 之前Spotlight 搜索功能是对开发者来说是透明的，但是现在开发者可以添加在Spotlight 或者Safari 的搜索结果，甚至在该app 没有安装的情况下也可以。

<img src="./resource/Screen Shot 2015-06-23 at 5.55.20 PM.png" alt="" width = "200">


本地没有安装Eventbrite ，可以在搜索结果的网页上显示下载app（不熟悉，请猛戳[Smart App Banner](https://developer.apple.com/library/mac/documentation/AppleApplications/Reference/SafariWebContent/PromotingAppswithAppBanners/PromotingAppswithAppBanners.html)）。


<img src="./resource/Screen Shot 2015-06-23 at 5.55.27 PM.png" alt="" width = "200">

## App Search 由 NSUserActivity,CoreSpotlight,Web Markup组成。

<img src="./resource/Screen Shot 2015-06-24 at 9.00.55 AM.png" alt="" width = "590">
### NSUserActivity 
在iOS8 就出现了，主要用户Handoff 功能，现在扩展了它的功能，使它能够像浏览器那样记录你的浏览记录。但是只能用在用户访问过的或者看见过的内容中。一旦某些内容被记录进NSUserActivity，就可以在Spotlight和Safari中同时被搜索到。

<img src="./resource/Screen Shot 2015-06-24 at 9.06.18 AM.png" alt="" width = "590">

而且还能通过设置'Eligible For Public Indexing'来让这些被Index的内容传到Apple的云端Cloud Index里，从而实现每个用户都能搜索到这个内容。同时Apple也强调了隐私的保护。并不是所有内容都是Public的，同一个内容需要在云端被Index超过一个限额（具体多少没有公布），才会最后成为Public的内容。所以用户不用担心自己看到的内容成为公众都能搜索的内容。

<img src="./resource/Screen Shot 2015-06-24 at 9.11.01 AM.png" alt="" width = "590">
<img src="./resource/Screen Shot 2015-06-24 at 9.15.30 AM.png" alt="" width = "590">
<img src="./resource/Screen Shot 2015-06-24 at 9.15.40 AM.png" alt="" width = "590">



NSUserActivity 让用户更加容易的查看他们以往查看的内容。一方面开发者们也可以充分利用这个功能，更好展现自己的app,让用户体验做到更加好。

### CoreSpotlight 
就像数据库那样，让开发者可以添加，删除，更新在应用内为用户保存的用于快速搜索的记录。内置的Mail，Notes等应用也是用这项技术来实现搜索应用内容的功能。一般会是推荐App内用户的文档，图片，信息，等等内容

<img src="./resource/Screen Shot 2015-06-24 at 9.27.32 AM.png" alt="" width = "590">
<img src="./resource/Screen Shot 2015-06-24 at 9.35.56 AM.png" alt="" width = "590">
<img src="./resource/Screen Shot 2015-06-24 at 9.33.09 AM.png" alt="" width = "590">
<img src="./resource/Screen Shot 2015-06-24 at 9.33.20 AM.png" alt="" width = "590">
<img src="./resource/Screen Shot 2015-06-24 at 9.33.28 AM.png" alt="" width = "590">

[**CoreSpotlight Demo**](https://github.com/vedon/WWDC-2015/tree/master/Demo)
### Web Markup 
这项功能允许苹果和名为：Applebot search engine 的搜索服务器搜索与app 相关的内容，让用户更加容易的使用搜索功能。支持 "deep linking" and universal link .结合苹果的 Smart App Banners,Twitter Cards 和 Fackbook App Links.

要使应用内的网页内容可被搜索，开发者需要设置：

> * 1）**Allow Apple to discover and crawl an app’s website with the Applebot.**
>
>  在iTunes Connect 提交应用的时候，在 Support URL 和 Marketing URL 填写链接。苹果会根据你所提供的URL 来搜索内容。
> 
> 	<img src="./resource/Screen Shot 2015-06-24 at 11.16.47 AM.png" alt="" width = "590">
> 
> * 2）**Ensure the app’s website has the Web markup for deep linking.**
> <img src="./resource/Screen Shot 2015-06-24 at 11.21.47 AM.png" alt="" width = "590">
> 
> 	Universal Link 是 iOS9 里面的新功能，可以用来取代 smart app banners。但使用 Universal Link 的前提是你的应用已经被安装了。所以建议继续使用smart app banners。
> <img src="./resource/Screen Shot 2015-06-24 at 11.25.15 AM.png" alt="" width = "590">
> <img src="./resource/Screen Shot 2015-06-24 at 11.44.18 AM.png" alt="" width = "590">
> 
> [详情请查看Seamless Link to your App](https://github.com/vedon/WWDC-2015/blob/master/Seamless%20Linking%20to%20your%20app.md)
> 
> * 3) **On the other end, make sure the app is set up to handle deep linking.**
> <img src="./resource/Screen Shot 2015-06-24 at 11.45.50 AM.png" alt="" width = "590">
> 
> * 4) **Add markup for rich data and structured data to be able to surface in search.** 搜索结果显示的内容不限于只有title 和 description 了。还可以包含图片，甚至是触发的有两种格式：
> 
>	 [Open Graph](http://ogp.me/): 
>
> 	<img src="./resource/Screen Shot 2015-06-24 at 11.52.02 AM.png" alt="" width = "590">
> 
> 	[Scheme.org](https://schema.org/):
> 
>	 <img src="./resource/Screen Shot 2015-06-24 at 11.51.25 AM.png" alt="" width = "590">
>	<img src="./resource/Screen Shot 2015-06-24 at 11.51.39 AM.png" alt="" width = "590">
>
> 	Demo
> 
> 	<img src="./resource/Screen Shot 2015-06-24 at 11.56.18 AM.png" alt="" width = "590">
> 
> 	**Supported schemas**
	 * AggregateRating
	 * Offers
	 * Price Range
	 * InteractionCount
	 * Organization
	 * Recipe
	 * SearchAction
	 * ImageObject
	 
> 	**Actions**
> Current supported actions are: 
> 
	* Dialing a phone number
 	* Getting directions to an address
 	* Playing audio or video
 	* <img src="./resource/Screen Shot 2015-06-24 at 1.55.01 PM.png" alt="" width = "590">
 	* <img src="./resource/Screen Shot 2015-06-24 at 1.55.07 PM.png" alt="" width = "590">
 	
 	

**CoreSpotlight** 让你的应用内的内容可以让用户更加容易搜索到。例如微信，可以把所有的聊天信息都加上index ，这样用户就可以在spotlight 里面搜索内容。**Web markup** ,可以让用户没有安装你的应用的前提下，搜索到你的应用的内容，因此提高app 的下载率。**NSUserActivity** 'Eligible For Public Indexing's 使被Index的内容传到Apple的云端Cloud Index里，可以让更多的用户搜索到Public Indexing's 的内容。三者其实可以协同工作的，同一个app，同一个内容被三者同时使用，可以通过设置统一的ID(URL) 来实现。

<img src="./resource/Screen Shot 2015-06-24 at 2.23.23 PM.png" alt="" width = "590">

搜索内容的排名对于用户和开发者来说是透明的，提高搜索的排名。可以通过以下几点。
> * 1) URL Popilarity. (URL 在应用内被点击或者出现的次数)
> * 2) Activities (应用内的相对用的content出现的频率，可以用过使用NSUserActivity来提高)
> * 3) Engagements.(用户与搜索的内容之间的交互，例如点击)

<img src="./resource/Screen Shot 2015-06-24 at 2.40.39 PM.png" alt="" width = "590">