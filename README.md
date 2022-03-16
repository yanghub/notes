

[TOC]



## *创建ui项目

初始化angular项目  G:\project\angularui\

```bash
i => install == 安装
-S => save == 保存
-D =>devDependencies => 写入devDependencies，发布到生产环境
-g =>global => 全局安装

ng new angularui //样式选择less
cd angularui   //进到项目目录
cnpm i     //通过cnpm安装依赖
ng serve --open  //运行或npm start
```

### 命令创建页面

在src/app路径下创建四个 Component文件

```bash
ng g component pages/home    //相当于ng generate component pages/home
ng g component pages/create
ng g component pages/complete
ng g component pages/general/testpages
ng g component theme/asides/app-asideA   //产品菜单
ng g component theme/asides/app-asideB   //计划菜单
ng g component theme/asides/app-asideC  //物流菜单
ng g component theme/asides/app-asideD   //制造菜单
ng g component theme/asides/app-asideE  //资金菜单
ng g component theme/asides/app-asideF   //协作菜单
ng g component theme/asides/app-asideG   //查控菜单
ng g component theme/asides/app-asideH   //配置菜单

ng g component theme/components/app-aside-header
ng g component theme/components/app-aside-footer
```



包含以下组件

```bash
npm install @clr/icons @clr/ui @clr/angular
npm install rxjs       //rxjs
npm install --save  redux   //redux
npm install @ngrx/core @ngrx/store @ngrx/effects --save-dev  //统一引入

//一键引入
npm install rxjs redux @ngrx/core @ngrx/store @ngrx/effects --save-dev
```

原始项目导入

G:\workspace\uidemo\下的testangui.rar复制到G:\project\angularui解压改名字

```
cd G:\project\angularui\demo

cnpm install
npm start     //运行
```

### webpack打包

[webpack官方](https://webpack.js.org/)

## 引入axios

```bash
npm install axios --save
```



## *绑定elementui组件

[element官方文档](https://element-angular.faas.ele.me/guide/install)

```javascript
npm i --save element-angular
```

在styles.css中引入

```css
@import "~element-angular/theme/index.css";
```

引入ElModule在app.module.ts中

```javascript
import { ElModule } from 'element-angular';

// import 模块导入
ElModule.forRoot(),
```

html使用

```html
<div class="page">
    <el-collapse [model]="[]" class="list">
        <el-collapse-item  *ngFor="let item of menus" label={{item.name}} value={{item.id}}>
            <div class="details" *ngFor="let detailsList of item.details">
                {{detailsList}}
            </div>
        </el-collapse-item>
    </el-collapse>
</div>
```

## *绑定ng-zorro-antd样式

导入模块

```
$ ng new PROJECT_NAME
$ cd PROJECT_NAME
$ ng add ng-zorro-antd
或（以上方式太慢，一般用 cnpm直接在项目中添加）
$ npm install ng-zorro-antd --save
```

[github源码](https://github.com/fs-coder/ng-admin-starter)

[ng-zorro官方中文文档](https://ng.ant.design/docs/introduce/zh)

### 安装组件

手动引入

```bash
$ npm install ng-zorro-antd --save
```

### 引入样式

#### 使用全部组件样式

该配置将包含组件库的全部样式，如果只想使用某些组件请查看 [使用特定组件样式](https://ng.ant.design/docs/getting-started/zh#使用特定组件样式) 配置。

在 `angular.json` 中引入了

```json
{
  "styles": [
    "node_modules/ng-zorro-antd/ng-zorro-antd.min.css"
  ]
}
```

在 `style.css` 中引入预构建样式文件

```css
@import "~ng-zorro-antd/ng-zorro-antd.min.css";
```

在 `style.less` 中引入 less 样式文件

```less
@import "~ng-zorro-antd/ng-zorro-antd.less";
```

#### 使用特定组件样式

> 由于组件之间的样式也存在依赖关系，单独引入多个组件的 CSS 可能导致 CSS 的冗余。

使用特定组件样式时前需要先引入基本样式(所有组件的共用样式)。

在 `style.css` 中引入预构建样式文件

```css
@import "~ng-zorro-antd/style/index.min.css"; /* 引入基本样式 */
@import "~ng-zorro-antd/button/style/index.min.css"; /* 引入组件样式 */
```

在 `style.less` 中引入 less 样式文件

```less
@import "~ng-zorro-antd/style/entry.less"; /* 引入基本样式 */
@import "~ng-zorro-antd/button/style/entry.less"; /* 引入组件样式 */
```

### 引入组件模块

最后你需要将想要使用的组件模块引入到你的 `app.module.ts` 文件和[特性模块](https://angular.cn/guide/feature-modules)中。

以下面的 `NzButtonModule` 模块为例，先引入组件模块：

```ts
import { NgModule } from '@angular/core';
import { NzButtonModule } from 'ng-zorro-antd/button';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    NzButtonModule
  ]
})
export class AppModule { }
```

然后在模板中使用：

```html
<button nz-button nzType="primary">Primary</button>
```



## *配置启动

控制台

```bash
>G:
cd G:\project\angularui
ng new  newdemo    //（名字任意取，小写），开始新建项目：                                       
//通过key选择一个css样式，scss
//按两下ctrl  +c，停止运行
cd newdemo    //进入项目目录
cnpm i        //（下载package.json里面的依赖包）：  
ng serve     //ng启动
或
npm start    //npm启动,vs code中使用，ctrl+`  打开控制台
```

最后成功打开项目：http://localhost:4200可以直接访问

### 配置端口

在根文件夹下的 package.json 文件

这里有一个 "start" 属性，更改这里的值：

```json
"scripts": {
  "ng": "ng",
  "start": "ng serve --port 4203 --env=dev",
  "build": "ng build --env=prod",
  "test": "ng test",
  "lint": "ng lint",
  "e2e": "ng e2e"
},
```

[路由配置](https://www.cnblogs.com/1156063074hp/p/10637414.html)

[angular官方文档简中](https://angular.cn/)

## *绑定路由跳转

[路由跳转](https://blog.csdn.net/wrs120/article/details/78612692)

### 生成路由

```
ng generate module app-routing --flat --module=app
```

/app-routing.module.ts 

```ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HeroesComponent } from './heroes/heroes.component';

const routes: Routes = [
  { path: 'heroes', component: HeroesComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

`path`: 用来匹配浏览器地址栏中 URL 的字符串。

`component`: 导航到该路由时，路由器应该创建的组件。

`@NgModule` 元数据会初始化路由器，并开始监听浏览器地址的变化。

app.component.html则改为

```
<h1>{{title}}</h1>
<router-outlet></router-outlet>
<app-messages></app-messages>
```

### 添加仪表盘（命令添加页面）

使用 CLI 添加一个 `DashboardComponent`：

```
ng generate component dashboard
```

导航到仪表盘app-routing.module.ts 

````
const routes: Routes = [
  { path: '', redirectTo: '/dashboard', pathMatch: 'full' },
  { path: 'dashboard', component: DashboardComponent },
  { path: 'detail/:id', component: HeroDetailComponent },
  { path: 'heroes', component: HeroesComponent }
];

````

仪表盘添加dashboard.component.html

```
<a *ngFor="let hero of heroes" class="col-1-4"
    routerLink="/detail/{{hero.id}}">
  <div class="module hero">
    <h4>{{hero.name}}</h4>
  </div>
</a>
```

更改src/app/heroes/heroes.component.html (list with links)

```
 <ul class="heroes">
  <li *ngFor="let hero of heroes">
    <a routerLink="/detail/{{hero.id}}">
      <span class="badge">{{hero.id}}</span> {{hero.name}}
    </a>
  </li>
</ul>
```

清除死数据

src/app/heroes/heroes.component.ts (cleaned up)

```ts
export class HeroesComponent implements OnInit {
  heroes: Hero[];

  constructor(private heroService: HeroService) { }

  ngOnInit() {
    this.getHeroes();
  }

  getHeroes(): void {
    this.heroService.getHeroes()
    .subscribe(heroes => this.heroes = heroes);
  }
}
```

 获取创建本组件的路由

hero-detail为详情页

 从这个路由中提取出 `id`

 通过 `HeroService` 从服务器上获取具有这个 `id` 的英雄数据。

src/app/hero-detail/hero-detail.component.ts

```ts
import { ActivatedRoute } from '@angular/router';
import { Location } from '@angular/common';

import { HeroService }  from '../hero.service';

//构造器中添加
constructor(
  private route: ActivatedRoute,
  private heroService: HeroService,
  private location: Location
) {}
```

路由参数获取id

src/app/hero-detail/hero-detail.component.ts

```
ngOnInit(): void {
  this.getHero();
}

getHero(): void {
  const id = +this.route.snapshot.paramMap.get('id');
  this.heroService.getHero(id)
    .subscribe(hero => this.hero = hero);
}
```

添加服务src/app/hero.service.ts (getHero)

```
getHero(id: number): Observable<Hero> {
  //新添加服务
  this.messageService.add(`HeroService: fetched hero id=${id}`);
  return of(HEROES.find(hero => hero.id === id));
}
```

反引号 ( ` ) 用于定义 JavaScript 的模板字符串字面量，以便嵌入 `id`。

添加返回方法src/app/hero-detail/hero-detail.component.ts (goBack)

```
goBack(): void {
  this.location.back();
}
```

页面src/app/hero-detail/hero-detail.component.html (back button)

```
<button (click)="goBack()">go back</button>
```



## *绑定元素数据

### 绑定元素

app.component.ts下

```ts
export class AppComponent {
  // title = 'agraui';
}
```

则在app.component.html绑定

```html
<h1>{{title}} </h1>
```





UpperCasePipe把文本转换成全大写形式。

```
<h2>{{hero.name | uppercase}} Details</h2>
```

src/app下定义Hero.ts

```ts
export interface Hero {
  id: number;
  name: string;
}
```

则ts中引用为

```ts
import { Component, OnInit } from '@angular/core';
import { Hero } from '../hero';   //导入Hero

@Component({
  selector: 'app-heroes',
  templateUrl: './heroes.component.html',
  styleUrls: ['./heroes.component.css']
})
export class HeroesComponent implements OnInit {
  hero: Hero = {
    id: 1,
    name: 'Windstorm'
  };

  constructor() { }

  ngOnInit() {
  }

}
```

则html中

```html
<h2>{{hero.name | uppercase}} Details</h2>
<div><span>id: </span>{{hero.id}}</div>
<div><span>name: </span>{{hero.name}}</div>
```



## *表单绑定及双向绑定

[表单绑定官方文档](https://angular.cn/guide/dynamic-form)

[双向绑定](https://www.cnblogs.com/yiweiyihang/p/12131008.html)

**[(ngModel)]** 是 Angular 的双向数据绑定语法。

需要在app.module.ts导入包

```ts
import { FormsModule } from '@angular/forms'; // <-- NgModel lives here
```

### *ngFor循环绑定事件，*****ngif选择

```html
*ngFor="let hero of heroes"
//"*"不可少，hero循环数据heroes
```

src/app外定义Hero.ts的Hero对象

```
// 这里是定义对象

export interface Hero {
  id: number;
  name: string;
}
```

src\app\mock-heroes.ts中定义数据

```
import { Hero } from './hero';

export const HEROES: Hero[] = [
  { id: 1, name: '小羊' },
  { id: 2, name: '小李' },
  { id: 3, name: '小毛' },
  { id: 4, name: '不易' },
  { id: 5, name: '很好' },
  { id: 6, name: '刷卡的那' },
  { id: 7, name: '打啊打' },
  { id: 8, name: '啊发放' },
  { id: 9, name: '发发' },
  { id: 10, name: '发发是' },
];
```

src\app\heroes\heroes.component.ts中引入数据

```
import { Hero } from '../hero'; //引入对象
import { HEROES } from '../mock-heroes'; //导入数据源HEROES

export class HeroesComponent implements OnInit {
  // public hero = 'Windstorm';
  selectedHero: Hero;    //通过selectedHero选择Hero
  onSelect(hero: Hero): void {   
    this.selectedHero = hero;  //定义点击绑定指向Hero
  }
  hero: Hero = {
    id: 1,
    name: 'Windstorm',
  };
  heroes = HEROES;  //指向数据源

  constructor() {}

  ngOnInit(): void {}
}
```



### (click)绑定点击事件

```html
(click)="onSelect(hero)"
```

*ngIf="selectedHero"绑定selectedHero，{{选择的元素写法，名称.id}}

[class.selected]="hero === selectedHero"为css样式绑定

*ngFor="let hero of heroes"循环ts中指向的heroes数据

class="heroes"绑定css样式

[(ngModel)]="selectedHero.name"   文本选择[(ngModel)]

```
<h2>My Heroes</h2>
<ul class="heroes">
  <li *ngFor="let hero of heroes"
    [class.selected]="hero === selectedHero"
    (click)="onSelect(hero)">
    <span class="badge">{{hero.id}}</span> {{hero.name}}
  </li>
</ul>

<div *ngIf="selectedHero">

  <h2>{{selectedHero.name | uppercase}}</h2>
  <div><span>id: </span>{{selectedHero.id}}</div>
  <div>
    <label>name:
      <input [(ngModel)]="selectedHero.name" placeholder="name"/>
    </label>
  </div>

</div>
```

1.app.module.ts中：

```
import { FormsModule } from "@angular/forms";
imports:{
FormsModule
]
```

### *添加服务

创建hero服务

```sh
ng generate service hero
ng generate service services/product/product
```

hero.service.ts获取数据

```ts
//导入
import { Hero } from './hero';
import { HEROES } from './mock-heroes';

export class HeroService {
  getHeroes(): Hero[] {
    return HEROES;     // 返回数据
  }
  constructor() {}
}

```

页面的component.ts文件导入服务即可

导入的数据则这样写

```ts
  heroes: Hero[]; // 使用服务定义为声明
  // 构造器传入私有hero服务
  constructor(private heroService: HeroService) {}

  getHeroes(): void {
    this.heroes = this.heroService.getHeroes(); // 从服务获取数据
  }

  ngOnInit(): void {
    this.getHeroes(); // 服务此处调用
  }
```

同步操作

src/app/heroes/heroes.component.ts

```ts
this.heroes = this.heroService.getHeroes();
```

### 异步获取Observer

server.ts导入rxjs

```ts
import { Observable, of } from 'rxjs';
....
getHeroes(): Observable<Hero[]> {
  return of(HEROES);
}
```

component.ts

```ts
getHeroes(): void {
  this.heroService.getHeroes()
      .subscribe(heroes => this.heroes = heroes);
}
```

### 创建 `MessageService`

```
ng generate service message/websocketservice
```

### 创建消息页面

```
ng g component messages
```

message.service.ts

```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class MessageService {
  messages: string[] = [];

  add(message: string) {
    this.messages.push(message);
  }

  clear() {
    this.messages = [];
  }
}
```

hero.service.ts导入包

```ts
import { MessageService } from './message.service';

constructor(private messageService: MessageService) { }

getHeroes(): Observable<Hero[]> {
  this.messageService.add('HeroService: fetched heroes');  //添加消息
  return of(HEROES);
}
```

messages/messages.component.html

```html
<div *ngIf="messageService.messages.length">

  <h2>Messages</h2>
  <button class="clear"
          (click)="messageService.clear()">clear</button>
  <div *ngFor='let message of messageService.messages'> {{message}} </div>

</div>
```

 `*ngIf` 只有在有消息时才会显示消息区。

 `*ngFor` 用来在一系列 `<div>` 元素中展示消息列表。

   Angular 的[事件绑定](https://angular.cn/guide/template-syntax#event-binding)把按钮的 `click` 事件绑定到了 `MessageService.clear()`。

改动/heroes.component.ts

```ts
import { Component, OnInit } from '@angular/core';

import { Hero } from '../hero';
import { HeroService } from '../hero.service';
import { MessageService } from '../message.service';  // 导入包

@Component({
  selector: 'app-heroes',
  templateUrl: './heroes.component.html',
  styleUrls: ['./heroes.component.css']
})
export class HeroesComponent implements OnInit {

  selectedHero: Hero;

  heroes: Hero[];
// 构造器添加
  constructor(private heroService: HeroService, private messageService: MessageService) { }

  ngOnInit() {
    this.getHeroes();
  }

  onSelect(hero: Hero): void {
    this.selectedHero = hero;
    this.messageService.add(`HeroesComponent: Selected hero id=${hero.id}`); // 添加消息
  }

  getHeroes(): void {
    this.heroService.getHeroes()
        .subscribe(heroes => this.heroes = heroes);
  }
}
```

最后src/app/app.component.html添加展示

```html
<app-messages></app-messages>
```

### 案例：

HTML

```html
<h2>人员登记系统</h2>
<div class="people_list">
    <ul>
        <li>姓名：<input type="text" id="username" [(ngModel)]="peopleInfo.username" value="form_input" /></li>
        <li>性别：

            <input type="radio" value="1" name="sex" id="sex1" [(ngModel)]="peopleInfo.sex"><label for="sex1">男</label>
            <input type="radio" value="2" name="sex" id="sex2" [(ngModel)]="peopleInfo.sex"><label for="sex2">女</label>
        </li>
        <li>城市：
            <select name="city" id="city" [(ngModel)]="peopleInfo.city">
                <option [value]="item" *ngFor="let item of peopleInfo.cityList">{{item}}</option>
            </select>
        </li>
        <li>爱好：
            <span *ngFor="let item of peopleInfo.hobby;let key=index;">
                <input type="checkbox" [id]="'check'+key" [(ngModel)]="item.checked" />
                <label [for]="'check'+key">{{item.title}}</label>
                &nbsp;&nbsp;
            </span>
        </li>
        <li>
            备注：
            <textarea name="mark" id="mark" cols="30" rows="5" [(ngModel)]="peopleInfo.mark"></textarea>
        </li>

    </ul>
    <button (click)="doSubmit()" class="submit">获取表单的内容</button>

    <br />
    <br />
    <br />

    <pre>
        {{peopleInfo|json}}
    </pre>
</div>
```

ts

```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-form',
  templateUrl: './form.component.html',
  styleUrls: ['./form.component.scss']
})
export class FormComponent implements OnInit {

  public peopleInfo: any = {
    username: "",
    sex: "1",
    cityList: ["北京", "上海", "深圳"],
    city: "北京",
    hobby: [
      {
        title: "吃饭",
        checked: false
      },
      {
        title: "睡觉",
        checked: false
      },
      {
        title: "敲代码",
        checked: true
      }
    ],
    mark:""
  }
  constructor() { }

  ngOnInit() {
  }
  doSubmit() {
    let usernameDom: any = document.getElementById('username');
    console.log(usernameDom.value);
  }

}
```

scss

```
h2{
    text-align: center;
}
.people_list{
    // background-color:red;
    width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px snow blue;
    li{
        height: 50px;
        line-height: 50px;
        .form_input{
            width: 300px;
            height: 40px;
        }
    }
    .submit{
        width: 100px;
        height: 30px;
        float: right;
        margin-top: 120px;
    }
}
```

## *表单获取后台数据(nrgx)

### 使用假数据组件

```
cnpm install angular-in-memory-web-api --save
```

### 创建生成类 （服务ts）

`src/app/in-memory-data.service.ts`：

```
ng generate service InMemoryData
```

将 `in-memory-data.service.ts` 改为以下内容：

src/app/in-memory-data.service.ts`      `

```ts
import { Injectable } from '@angular/core';
import { InMemoryDbService } from 'angular-in-memory-web-api';
import { Hero } from './hero';

@Injectable({
  providedIn: 'root',
})
export class InMemoryDataService implements InMemoryDbService {
  createDb() {
      //  假数据来源
    const heroes = [
      { id: 1, name: '小羊' },
      { id: 2, name: '小李' },
      { id: 3, name: '小毛' },
      { id: 4, name: '不易' },
      { id: 5, name: '很好' },
      { id: 6, name: '刷卡的那' },
      { id: 7, name: '打啊打' },
      { id: 8, name: '啊发放' },
      { id: 9, name: '发发' },
      { id: 10, name: '发发是' },
    ];
    return {heroes};
  }
//重写genId方法，以确保英雄总是有id。
//如果heroes数组为空，
//下面的方法返回初始值(11)。
//如果heroes数组不是空的，下面的方法将返回最高的值
//英雄id + 1。
  genId(heroes: Hero[]): number {
    return heroes.length > 0 ? Math.max(...heroes.map(hero => hero.id)) + 1 : 11;
  }
}
```

添加模组src/app/app.module.ts (HttpClientModule import)添加到imports数组中

```ts
import { HttpClientModule }    from '@angular/common/http';
import { HttpClientInMemoryWebApiModule } from 'angular-in-memory-web-api';
import { InMemoryDataService }  from './in-memory-data.service';
......
// imports中添加
@NgModule({
  imports: [
  HttpClientModule,
  HttpClientInMemoryWebApiModule.forRoot(
    InMemoryDataService, { dataEncapsulation: false }
  )
})
```

`in-memory-data.service.ts` 文件已代替了 `mock-heroes.ts` 文件，可删除。

服务器就绪后，丢弃内存 Web API，应用的请求直接传给服务器。

### 请求数据

src/app/hero.service.ts (import HTTP symbols)服务中调用

```ts
import { Injectable } from '@angular/core';
import { Hero } from './hero';
import { HEROES } from './mock-heroes';
import { Observable, of } from 'rxjs';
import { MessageService } from './message.service';
// 导入此包
import { HttpClient, HttpHeaders } from '@angular/common/http';

@Injectable({
  providedIn: 'root',
})
export class HeroService {
  private heroesUrl = 'api/heroes'; // 请求地址url

  getHero(id: number): Observable<Hero> {
    // 此处获取到 服务
    this.messageService.add(`HeroService: fetched hero id=${id}`);
    return of(HEROES.find((hero) => hero.id === id));
  }

  /** GET 请求 */
  getHeroes(): Observable<Hero[]> {
    return this.http.get<Hero[]>(this.heroesUrl);
  }
  // 日志
  private log(message: string) {
    this.messageService.add(`HeroService: ${message}`);
  }

  constructor(
    private http: HttpClient,
    private messageService: MessageService
  ) {}
}

```

### 错误处理

src/app/hero.service.ts导包

```
import { Injectable } from '@angular/core';
import { Hero } from './hero';
import { HEROES } from './mock-heroes';
import { Observable, of } from 'rxjs';
import { MessageService } from './message.service';
import { HttpClient, HttpHeaders } from '@angular/common/http';
import { catchError, map, tap } from 'rxjs/operators';

@Injectable({
  providedIn: 'root',
})
export class HeroService {
  private heroesUrl = 'api/heroes'; // 请求地址url

  getHero(id: number): Observable<Hero> {
    const url = `${this.heroesUrl}/${id}`; // 通过url获取
    return this.http.get<Hero>(url).pipe(
      tap((_) => this.log(`fetched hero id=${id}`)),
      catchError(this.handleError<Hero>(`getHero id=${id}`))
    );
  }
  
  private handleError<T>(operation = 'operation', result?: T) {
  // 处理错误
    return (error: any): Observable<T> => {
      // TODO:将错误发送到远程日志
      console.error(error); // log输出到控制台

      // 待办事项:更好地为用户转换错误
      this.log(`${operation} failed: ${error.message}`);

      // 通过返回一个空结果让应用程序继续运行。
      return of(result as T);
    };
  }

  /** GET 请求 */
  getHeroes(): Observable<Hero[]> {
    return this.http.get<Hero[]>(this.heroesUrl).pipe(
      tap((_) => this.log('fetched heroes')),
      catchError(this.handleError<Hero[]>('getHeroes', []))
    );
  }

  private log(message: string) {
    this.messageService.add(`HeroService: ${message}`);
  }

  constructor(
    //  HttpClient 注入到构造函数中一个名叫 http 的私有属性
    private http: HttpClient,
    private messageService: MessageService
  ) {}
}

```

修改实现

src/app/hero-detail/hero-detail.component.ts (save)

```ts
save(): void {
  this.heroService.updateHero(this.hero)
    .subscribe(() => this.goBack());
}


```

put添加到服务src/app/hero.service.ts (update)

```
/** PUT方法 */
updateHero(hero: Hero): Observable<any> {
  return this.http.put(this.heroesUrl, hero, this.httpOptions).pipe(
    tap(_ => this.log(`updated hero id=${hero.id}`)),
    catchError(this.handleError<any>('updateHero'))
  );
}
```

页面src/app/hero-detail/hero-detail.component.html (save)

```
<button (click)="save()">save</button>
```

## *demo展示绑定api插件
