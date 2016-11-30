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
		@Component({
		  selector: 'to-do',
		  viewProviders: [TodoRESTClient],
		})
		@View({
		  templateUrl: 'components/to-do-template.html',
		})
		export class ToDoCmp {

		  constructor(todoRESTClient: TodoRESTClient) {
		  }
		  
		  //Use todoRESTClient   
		}
```
## API Docs

### RESTClient
#### Methods:
- `getBaseUrl(): string`: returns the base url of RESTClient
- `getDefaultHeaders(): Object`: returns the default headers of RESTClient in a key-value pair

### Class decorators:
- `@BaseUrl(url: string)`
- `@DefaultHeaders(headers: Object)`

### Method decorators:
- `@GET(url: String)`
- `@POST(url: String)`
- `@PUT(url: String)`
- `@DELETE(url: String)`
- `@Headers(headers: Object)`

### Parameter decorators:
- `@Path(key: string)`
- `@Query(key: string)`
- `@Header(key: string)`
- `@Body`

# License

MIT
