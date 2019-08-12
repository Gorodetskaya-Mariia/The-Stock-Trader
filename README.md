# «The Stock Trader» (a Vue.js project)

The application contains from three pages («Home», «Stocks», «Portfolio»). You can buy as many stocks as you can afford on the page «Stocks». The page «Portfolio» displays all stocks which you have bought. Also, you may «Save» and «Load» your data. Click on «End Day» to update prices of every stock. You may sell your stocks and get a profit or a loss. You can find a similar information on the «Home» page.

## Technology stack and techniques used in project:
	* Vue Router
	* Vuex
	* Vue Resource and Firebase
	* Animation for Route transitions
	* Responsive Web Design
	* CSS Flexbox Layout

## What is done:
### Pages implemented:
> [Home page](https://vuejs-project-stock-trader.herokuapp.com/)<br>
> [Stocks](https://vuejs-project-stock-trader.herokuapp.com/stocks)<br>
> [Portfolio](https://vuejs-project-stock-trader.herokuapp.com/portfolio)<br>

### Project overview:
- Vue Router was installed for setting up routes. The project has three routes: to home page, to the portfolio and to the stocks page.
- Vuex: two modules were created, one for the Portfolio and one for Stocks. Each of these modules has its own state. There is nothing in a global state ( store.js ) because the stocks which are available were mapped to the stocks module (store/modules/stocks.js). The funds belong to the portfolio (store/modules/portfolio.js).
- Vue Resource is used to send requests to Firebase for fetching (GET Requests) and Saving Data (PUT Requests). So, you may «Save» and «Load» your data.
- Animation was used for animating the transition between routes. The router view is wrapped by transition with name «slide». Two classes were used to set up animations: «slide-enter-active» and «slide-leave-active».
- Price of every stock on «Stocks» and «Portfolio» pages can be updated by clicking on a button «End Day». It is achieved by a function which randomizes prices. They will be updated on «Stocks» and «Portfolio» pages immediately.

### Build Setup

``` bash
# install dependencies
npm install

# launch with hot reload at localhost:8080
npm run dev

# build for production with minifications
npm run build
```
<!-- ### Install

	* npm install --save vue-router
	* npm install --save vuex
	* npm install --save vue-resource -->
