# ng2-rest-api
ng2-rest-api HTTP client to consume RESTful services. Built on Angular2/http with TypeScript. A rest api template for all api consumption.
**Note:** this solutions is not included in npm, so download and include it in your service folder.

## Installation

```sh
Download and include the api.service.ts file into your service folder of your application.
```

## Usage

```ts

import { Injectable } from '@angular/core';
import { URLSearchParams } from '@angular/http';
import { ApiService } from '../../../../services/api.service'; //include the downloaded service

import 'rxjs/add/operator/toPromise';


@Injectable()
export class ChartService {

	constructor(private apiService: ApiService) { }

	protected module: string = "chart/";

	//to get the chart data
	getChartData(endPoint:string,parameter?:any): Promise<any> {
		let params: URLSearchParams = new URLSearchParams();
		return this.apiService.get(this.module + endPoint,params)
			.then(res => res)
			.catch(err => err);
	}

}
```

### Using it in your component

``` ts
import { Component } from '@angular/core';
import { ChartService } from './chart.service'; //call the chart service from here

@Component({
  selector: 'chart',
  templateUrl: './view/chart.html',
  providers: [ChartService]  //include the service in the providers
})

export class ChartComponent {

  constructor(private chartService: ChartService) { }

  //get the line chart data from the api
  public _getLineChartData(): void {
	//call the chart service to get the data
	this.chartService.getChartData("chart/lineChart.json").then(res => {
	if(res && res.status=='SUCCESS'){
	  this.lineChartData = res.lineChartData;
	  this.lineChartLabels = res.lineChartLabels;
	  }
	}).catch(err => err);
  }



  //on page load
  ngOnInit() {

	//call the methods to get the data from the api
	this._getLineChartData();
  }
}
```
## API Docs

### RESTClient
#### Methods:
- `get(): --> for all get operrations
- `create(): --> for all post operations
- `update(): --> for all put operrations
- `delete(): --> for all delete operations


## About Author
* [Author URL] (http://ranjithprabhu.in)

I am passionate in playing with pixels, creating attractive designs which interact well with the user and love developing web apps. Have a good background in web design and development. Also having wonderful working experience with various interesting projects and participated in the development of the products to provide end to end solutions.


## License
Released under the MIT license.
