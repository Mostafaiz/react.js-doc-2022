# شروعی بر react.js

در این قسمت، خلاصه درس ها به صورت داکیومنت و `Code` جهت یادگیری و یادآوری نوشته می شود
https://github.com/ferlobo1985/udmy-React-fullstack-01basics-project.

نود را نصب می کنیم و نمایش ورژن نود جی اس   
```
 node -v
 npm -v 
 yarn -v
 npx -v 
 npm list react 
 
```


 ```create-react-app```
 یک پکیج هست که باید از قبل نصب شده باشد بعد از نود 
 
 
 بعد با استفاده این پکیج ، نود را در پوشه خودمان نصب می کنیم . به این صورت  
``` npx create-react-app my-app```

بعد از دستور بالا کد زیر را می زنیم که وارد محیط و پوشه برنامه شویم 

```
  cd my-app
  npm start
```
  البته دستورات زیر را هم می توان اجرا کرد 
  ```
    npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!
    
  ```
  
  برای نصب تیلویند 
  ```
  npm install -D tailwindcss
npx tailwindcss init
  ```
  
  tailwind.config.js را هم ویرایش می کنیم 
  به contend کد زیر را اضافه می کنیم 
  ```
      "./src/**/*.{js,jsx,ts,tsx}",

   ```
   
   
  جهت استفاده از استایل زیر استفاده می کنیم 
  ```
  @tailwind base;
@tailwind components;
@tailwind utilities;
  ```
## جلسه 6

فایل نسخه 17 index.js

```javascript
import React from 'react';
import ReactDom from 'react-dom';

const App = () =>{
    return(
        <div>
            <h1>Hello mostafa</h1>
        </div>
    )
}

ReactDom.render(<App/>,document.getElementById('root'))
```
فایل نسخه 18 index.js


```javascript
import React from 'react';
import { createRoot } from 'react-dom/client';
import Header from './components/header';
import './styles/style.css'

const root = createRoot(document.getElementById('root'))
const App = () => {
    return (
        <div>
            <Header />
        </div>
    )
}

root.render(<App/>)
```

درباره var 

یکی اینکه امکان داشت دوباره تعریف بشه ، که شاید مشکل و باگ مخفی رو ایجاد کنه 

دوم اینکه var بیرون تابع به صورت گوبال و در داخل تابع به صورت محلی اجرا میشه 



درباره let 

متغیرهایی که با let تعریف میشن، دارای اسکوپ بلاکی (Block Scoped) هستن

متغیرهای let می‌تونن مقدار جدیدی بگیرن، ولی نمی‌تونن دوباره تعریف بشن

با توجه به اینکه متغیرهای let بلاک اسکوپ هستن، میشه داخل اسکوپ‌های مختلف متغیرهایی با همون نام رو با let تعریف کرد

برخلاف var که با مقدار undefined پیاده‌سازی میشن، متغیرهای let با هیچ مقداری پیاده‌سازی نمیشن. بنابراین وقتی متغیری رو می‌خوایم قبل از پیاده‌سازی استفاده کنیم، خطا می‌گیریم


درباره const 

متغیرهایی که با const (کانست) تعریف میشن، همون ویژگی‌هایی رو دارن که متغیرهای let دارن، با این تفاوت که مقدار متغیرهای const رو دیگه نمیشه تغییر داد.

متغیرهای const همیشه باید با یک مقدار پیاده‌سازی بشن
```javascript
const u;
// SyntaxError: missing = in const declaration
```

متغیرهایی که مقدار آبجکتی دارن فرق میکنه. وقتی یک متغیر const یک مقدار آبجکتی داره، آیتم‌های موجود در آبجکت رو میشه بدون هیچ مشکلی تغییر داد .  نمی‌تونیم کل آبجکت رو جایگزین کنیم
```javascript
const person = {
  name: "John",
  lastname: "Doe"
}

person.name = "Davood";

console.log(person); // { name: "Davood", lastname: "Doe" }
```


Hoisting در const درست مثل let هست. یعنی متغیرها به بالای حوزه خودشون میرن ولی پیاده‌سازی نمی‌شن. پس اگه متغیری رو قبل از اینکه پیاده‌سازی کنیم صدا بزنیم، خطا می‌گیریم.



خلاصه


متغیرهای var یا دارای حوزه سراسری هستن، یا حوزه تابعی. متغیرهای let و const دارای حوزه بلاکی هستن (Block Scoped).


متغیرهای var می‌تونن دوباره با var تعریف و همچنین مقداردهی بشن. متغیرهای let دوباره نمیتونن تعریف بشن، ولی می‌تونن دوباره مقداردهی بشن. متغیرهای const، نه می‌تونن دوباره تعریف و نه دوباره مقداردهی بشن.

متغیرهای var و let و const موقع عملیات Hoisting، بالای حوزه خودشون میرن، به طوری که متغیرهای var با مقدار undefined پیاده‌سازی میشن. درصورتی که توی let و const، متغیرها با هیچ مقداری پیاده‌سازی نمیشن.

وقتی متغیرهای var و let رو تعریف می‌کنیم، می‌تونیم بهشون مقدار ندیم و بعداً این کار رو انجام بدیم. ولی متغیرهای const رو همیشه باید با مقدار، پیاده‌سازی کنیم.


AF چیه؟
این توابع یک راه کوتاه‌تر برای داشتن Function Expression ها به حساب میان. در واقع این توابع نسخه‌ی جمع و جور شدهٔ توابع معمولی هستن. نحوه نوشتن اونها به صورت زیر هست:
```javascipt
() => "Hello!";
```

همونطور که گفتیم، AF ها نوعی Function Expression هستن. پس برای اینکه مثل یک تابع قابل استفاده باشن، اونها رو نسبت می‌دیم به یک متغیر:
```javascipt
const sayHello = () => "Hello!";

alert(sayHello());
```

نحوه‌ی پارامتر دادن به یک AF بصورت زیر هست:

```javascript
() => ...
param1 => ...
(param1, param2, ..., paramN) => ...
```


خط ۱ هیچ پارامتری نداریم. برای تابعی که هیچ پارامتری نداره باید از یک پرانتز باز و بسته استفاده کنیم

خط ۲ تابعی هست با یک پارامتر. اگه تابع فقط یک پارامتر داره قرار دادن پرانتز دور اون اختیاری هست

خط ۳ تابعی هست با دو یا چند پارامتر که باید اونها رو داخل پرانتز قرار بدیم


سادگی استفاده از AF ها هنگام استفاده از توابع Callback بیشتر مشخص میشه

```javascript
const numbers = [1, 2, 3];

const dup = numbers.map(num => num * 2);

alert(dup); // 2, 4, 6
```


خروجی تابع رو چطوری مشخص کنیم؟

عبارتی که جلوی => قرار می‌گیره بصورت خودکار return میشه:
```javascript
const give2 = () => 2;

alert(give2() + 2); // 4
```
اگه عبارت جلوی => طولانی هست می‌تونیم از پرانتز استفاده کنیم و اون عبارت رو ببریم توی یک خط جدا:


```javascript
const welcome = user => (
  `Welcome ${user}. This is a long text.
So I moved it into a separate line.
Hope you enjoy it.`
)

alert(welcome("Emily"));
```

اگه بدنه‌ی تابع چند خطی باشه، باید بدنه رو درون بلاک {...} قرار بدیم و برخلاف کدهای بالا باید بصورت دستی return کنیم:

```javascript
const give2 = () => {
   const x = 1;
   const y = 4;
   
   return x * y / 2;
}

alert(give2() + 2);
```


```javascript
const person = {
  mame: 'Amir'
}

export default person;
```
این کد شیء ما را export می کند تا بعدا آن را در فایلی import کنیم. کلیدواژه Default یعنی خروجی پیش فرض این فایل person است


مثال دیگری هم داریم. مثلا فایلی به نام utility.js داشته باشیم که در آن چندین چیز را export کنیم:

```
export const clean = () => {...}
export const baseData = 10;
```




حالا فایلی به نام app.js داریم که می خواهیم این دو فایل را در آن import کنیم بنابراین می گوییم:


```
import person from './person.js'
import prs from './person.js'

import {baseData} from './utility.js'
import {clean} from './utility.js'
```
از آنجا که در فایل person.js برای export کردن شیء person از کلیدواژه default استفاده کرده ایم در هنگام import فقط همان شیء person برای ما import می شود نه هیچ کد دیگری. بنابراین می توانیم هر اسمی که خواستیم برایش تعیین کنیم. در کد بالا من این شیء را دو بار و هر بار با نام های مختلف (person و prs) وارد (import) کرده ام؛ هر دو کد دقیقا یک کار را انجام می دهند. در این حالت تنها نام import شده به دست شما است و دیگر نمی توانید بگوییم به غیر از شیء person چیز دیگری را import کند


اما از آنجا که برای utility.js از default استفاده نکردیم باید مشخص کنیم که چه قسمتی را می خواهیم import کنیم. همانطور که می بینید در کد بالا با استفاده از curly braces توانسته ایم نام تابع و نام ثابت خود را مشخص کنیم تا import شوند. به این موارد named export می گوییم چرا که بر اساس نام import یا export می کند.


نکته: شما می توانید کد دوم را به صورت یک دستور بنویسید و مقادیر baseData و clean را با استفاده از کاما (ویرگول انگلیسی) جدا کنید.


البته اگر شما دوست دارید مانند حالت default از نام دلخواه خودتان برای import کردن named export ها استفاده کنید می توانید یک alias برای آن تعیین کنید. مثال:


```
import {clean as myFavoriteName} from './utility.js'
```

همچنین اگر چندین مقدار در فایلی دارید که می خواهید همه را با هم وارد کنید می توانید از حالت زیر استفاده کنید:

```
import * as bundled from './utility.js'

```

در این حالت bundled (که نام دلخواه ما بوده است) یک شیء جاوا اسکریپت خواهد بود که حاوی تمام const ها و اطلاعات دیگری است که از طرف فایل مبدا export شده باشند. بنابراین می توانید به این صورت به آن ها دسترسی داشته باشید

```
bundled.clean
bundled.baseData
```


قراردادن عبارات در JSX

در مثال زیر، ما یک متغیر به نام name تعریف می‌کنیم و سپس با قراردادن آن بین دو آکولاد، از آن در JSX استفاده می‌کنیم


```javascript
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
```


شما می‌توانید هر عبارت جاوااسکریپت معتبری را بین آکولادها در JSX قرار دهید. برای مثال، 2 + 2، user.firstName یا formatName(user)، همه عبارات معتبر جاوااسکریپت هستند.

در مثال زیر، ما نتیجه صدازدن یک تابع جاوااسکریپت به نام formatName(user) را درون یک المنت < h1> قرار می‌دهیم.
 
 ```javascript
 function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);
```
## جلسه 7

کد جلسه قبل بدون استفاده از `jsx` بصورت زیر می شود 
```javascript
import React from 'react';
import ReactDom from 'react-dom';

const App = () =>{
    return React.createElement('h1',{className:'title'},'Hello World');
}

ReactDom.render(<App/>,document.getElementById('root'))
```

اسامی ReactDom و React قابل تغییر هستند.

کد در حالت زیر که سینگل المنت است .کار می کنه اما اگه دوبار `h1` را تکرار کنیم کار نخواد کرد. ولی اگر بین `</><>` , `<React.Fragment></React.Fragment>` 

,`<div></div>` قرار بگیرد اجرا می شود 

```javascript
import React from 'react';
import ReactDom from 'react-dom';

const App = () =>(
            <h1>Hello mostafa</h1>
)

ReactDom.render(<App/>,document.getElementById('root'))
```
برای نوشتن `class` باید از `className`  استفاده کرد.
```javascript
const App = () =>(
    <div className='one'>
            <h1>Hello mostafa</h1>
            <h2>Hello mostafa</h2>
    </div>
 )
 ```
 
 ## جلسه 8 
![8](https://raw.githubusercontent.com/Mostafaiz/react.js-doc-2022/main/Screenshot%202023-02-21%20133037.png)

 
برای ساخت کامپوننت `Header`
```javascript
import React from 'react';

const Header = () =>{
    return <div>Header Hello</div>
}

export default Header;
```
کامپوننت ها در پوشه خاص خود ایجاد می شوند

![8](https://github.com/Mostafaiz/react.js-doc-2022/blob/837688bf0371688a67e321c315871c90d15a5e91/Screenshot%202023-02-21%20161942.png)

news_list_item.js
header.js
news_list.js

برای فراخوانی آن کامپونت دو خط زیر را در فایل ایندکس باید استفاده کرد 
```
import Header from './components/header';
```
```
<Header/>
```

مثال : در کد زیر  سال جاری را نمایش می دهد 
```
import React from 'react';

const Header = () => {

    const getTheYear=() => {
        const newDate=new Date();
        return newDate.getFullYear();
    }
    return (<div>
        
        the date is {getTheYear()}
    </div>
    )
}

export default Header;
```

## جلسه 9
#### class based component 

```javascript
import React from 'react';

class Header extends React.Component {

    render(){
        return (
            <div>
                     class Component
            </div>
        )
    }


}

export default Header;
```
خلاصه اش : 

```javascript
import React,{Component} from 'react';

class Header extends Component {

    render(){
        return (
            <div>
                     class Component
            </div>
        )
    }


}

export default Header;
```

#### function based componnent 
```javascript
import React from 'react';

const Header = () =>{

  
    return (
        <div>
                 the dat is {getTheYear()}
        </div>
    )
}

export default Header;
```

## جلسه 10

استفاده از css در درونcomponnent
نوع نوشتن استایل ها متفاوت است.

```javascript
class Header extends Component {

    render(){
        return (
            <header style={style.header}>
            <div className='logo'>Logo</div>
            <input></input>
           </header>
        )
    } 
}

let style={
    header:{
        background:"#03a9fa"
    },
    logo:{
        color:'#fff',
        fontFamily:'Anton',
        textAlign:'center'
    }
    
}
```

استفاده از css به صورت وارد کردن در کنار پوشه های سورس  

```javascript
import React from 'react';
import ReactDom from 'react-dom';
import Header from './components/header';
import './styles/style.css'

// const App = () =>{
//     return React.createElement('h1',{className:'title'},'Hello World');
// }

const App = () =>(
    <div className='one'>
            
            <Header/>

    </div>
 )


ReactDom.render(<App/>,document.getElementById('root'))
```


```
body {
    margin: 0;
}

header {
    background: #03a9fa;
    text-align: center;
}

.logo {
    color:#fff;
    font-family: Anton;
    text-align: center;
    font-size: 40px;
}

header input {
    font-size: 20px;
    margin: 20px 0px;
}
```

استغده از وارد کردن css در  index.html به صورت در کنار فایل های public  
```html
<link rel="stylesheet" type="text/css" href="style.css"/>

```

## جلسه 11
click event 

```javascript
import React,{Component} from 'react';

class Header extends Component {

    render(){
        return (
            // <header style={style.header}>
            <header
            onClick={() => console.log('i was clicked')}
            >
            <div className='logo'>Logo</div>
            <input></input>
           </header>
        )
    } 
}

export default Header;
```

inputchanged event
```javascript
import React,{Component} from 'react';

class Header extends Component {

    inputChangeHandler(){
        console.log('input changed')
    }


    render(){
        return (

            <header
            // onClick={() => console.log('iwas clicked')}
            >
            <div className='logo'>Logo</div>
            <input
            onChange={this.inputChangeHandler}
            ></input>
           </header>
        )
    } 
}

export default Header;
```


inputchanged event with show value in consol 
```javascript
import React, { Component } from 'react';

class Header extends Component {

    inputChangeHandler(event) {
        console.log(event.target.value)
    }


    render() {
        return (

            <header
            // onClick={() => console.log('iwas clicked')}
            >
                <div className='logo'>Logo</div>
                <input
                    onChange={this.inputChangeHandler}
                ></input>
            </header>
        )
    }
}

export default Header;
```


name va event ro chap mikone 
```
import React, { Component } from 'react';

class Header extends Component {

    inputChangeHandler(event , name) {
        console.log(event.target.value)
        console.log(name)
    }


    render() {
        return (

            <header
            // onClick={() => console.log('iwas clicked')}
            >
                <div className='logo'>Logo</div>
                <input
                    onChange={(e)=> this.inputChangeHandler(e,'ron')}
                ></input>
            </header>
        )
    }
}

export default Header;
```
## جلسه 12
گذاشتن محتویات ورودی در یک متغیر state و نمایش آن 
```javascript
import React,{Component} from 'react';

class Header extends Component {

    state ={
        name:'francis',
        title:'the keyword are:',
        keywords:'',
        count:'',
    }

    inputChangeHandler=(event)=>{
        this.setState({
        keywords: event.target.value
        })
    }

    render(){
        return (

            <header>        
            <div className='logo'>Logo</div>
            <input
            onChange={this.inputChangeHandler}
            />
            <div>{this.state.title}</div>
            <div>{this.state.keywords}</div>
           </header>
        )
    } 
}


export default Header;
```
اضافه کردن دکمه شمارنده 
```javascript
<div>{this.state.count}</div>
<button onClick={()=> this.addOne()}>Add One</button>  



    addOne(){
        this.setState({ count: this.state.count + 1 })
    }
```
## جلسه 13


صفحه اول به صورت کلاس ریترن می کنه مقدار هدر را در واقع قبلا با تابع بود الان با کلاس 
```javascript
import React, { Component } from 'react';
import { createRoot } from 'react-dom/client';
import Header from './components/header';
import './styles/style.css'

const root = createRoot(document.getElementById('root'))

class App extends Component {
    render(){
        return(
        <>
        <Header/>
        </>
        )
    }
}

root.render(<App/>)
```


اگر در کد بالا که در ایندکس دات جی اس است، جی سونی را فراخوانی کنیم و در کنسول نمایش دهیم به صورت زیر می شود . 

```javascript
import React, { Component } from 'react';
import { createRoot } from 'react-dom/client';
import Header from './components/header';
import './styles/style.css'
import JSON from './db/db.json'

const root = createRoot(document.getElementById('root'))

class App extends Component {
    render(){
        console.log(JSON)
        return(
        <>
        <Header/>
        </>
        )
    }
}

root.render(<App/>)
```

اضافه کردن کامپوننت نیوز لیست به صفحه اصلی و ارسال متغیر های استیت به صفحه کامپوننت ها
```javascript
import React, { Component } from 'react';
import { createRoot } from 'react-dom/client';   //import ReactDom from 'react-dom';

import Header from './components/header';
import NewsList from './components/news_list'; // اسم دلبخواهی هست

import './styles/style.css'
import JSON from './db/db.json'

const root = createRoot(document.getElementById('root'))

class App extends Component {


    state={
        news: JSON
    }
    render(){
        //console.log(this.state.news)   // اینجا جیسون را در استیت ریختیم 
        return(
        <>
        <Header/>

        
        {/* حال باید جیسون رو بدیم به کاپوننت زیر */}
        <NewsList 
        news={this.state.news}
        />
        </>
        )
    }
}

root.render(<App/>)
```
فایل نیوز لیست یا همون کامپوننت نیوز لیست 
```javascript
import React from 'react';

const newsList =(props) => {  //پراپس در واقع نیوز رو از ایندکس می گیره 
    return(
        <>
           {props.news.map((item)=>(
            <div key={item.id}>
               <h3>{item.title}</h3>
               <div>{item.feed}</div>
            </div>
           ))}

{/*اگر بجای بالا از پایینی استفاده کنیم باید ریترن کنیم  */}


            {/* 
            {props.news.map((item) => {
                return(
                <div>
                    <h3>{item.title}</h3>
                    <div>{item.feed}</div>
                </div>
                )
            })} */}

        </>
    )
}

export default newsList
// در واقع این فایل می خواد یک مقداری رو برگردونه از تابع نیوز لیست
```
خلاصه بالایی به صورت تمیز تر و مرتب تر 
```javascript
import React from 'react';

const newsList =(props) => {  //پراپس در واقع نیوز رو از ایندکس می گیره 

    const news = props.news.map((item) => (
        <div key={item.id}>
            <h3>{item.title}</h3>
            <div>{item.feed}</div>
        </div>
    ))


    return(
        <>
           {news}
        </>
    )
}

export default newsList
// در واقع این فایل می خواد یک مقداری رو برگردونه از تابع نیوز لیست
```
## جلسه 14

برای اینکه هر نیوز را جدا گانه فراخوانی کنیم کد را به صورت زیر تعییر می دهیم 

```javascript
import React from 'react';
import NewsItem from './news_list_item';


const newsList =(props) => {  //پراپس در واقع نیوز رو از ایندکس می گیره 


    const news = props.news.map((item) => (
    <NewsItem item={item} key={item.id} name="s" age="ss"/>
    ))

    return(
        <>
           {news}
        </>
    )
}

export default newsList
// در واقع این فایل می خواد یک مقداری رو برگردونه از تابع نیوز لیست
```

و بعد کامپوننت نیوز لیست را می سازیم 

```javascript
import React from "react";


const NewsItem =({item}) =>{

    return(
        <div class="news_item">
            <h3>{item.title}</h3>
            <div>
                {item.feed}
            </div>
        </div>

    )
}

export default NewsItem;
```

## جلسه 15

```javascript
import React,{Component} from "react";

class Footer extends Component{

    render(){
        return(
            <footer>
                {this.props.footerText}
            </footer>
        )
    }
}

export default Footer
```

در کامپونت بالا ویژگی پروپس در رندر ها همیشه قابل دسترس هست 

```javascript
import React, { Component } from 'react';
import { createRoot } from 'react-dom/client';   //import ReactDom from 'react-dom';

import Header from './components/header';
import NewsList from './components/news_list'; // اسم دلبخواهی هست
import Footer from './components/footer';

import './styles/style.css'
import JSON from './db/db.json'

const root = createRoot(document.getElementById('root'))

class App extends Component {


    state={
        news: JSON,
        footerText: 'i am footer'
    }
    render(){
        //console.log(this.state.news)   // اینجا جیسون را در استیت ریختیم 
        return(
        <>
        <Header/>

        
        {/* حال باید جیسون رو بدیم به کاپوننت زیر */}
        <NewsList 
        news={this.state.news}
        />
        <Footer footerText={this.state.footerText}/>
        </>
        )
    }
}

root.render(<App/>)
```
در کد بالا ارسال مقدار متغیر به فوتر

کد زیر را در بالا قرار می دهیم 
```javascript
const { news, footerText } = this.state ;
```

که به صورت زیر می شود
مزایای این تغییر این است که دیگر نیاز نیست this.state را بنویسیم همیشه 
```javascript

import React, { Component } from 'react';
import { createRoot } from 'react-dom/client';   //import ReactDom from 'react-dom';

import Header from './components/header';
import NewsList from './components/news_list'; // اسم دلبخواهی هست
import Footer from './components/footer';

import './styles/style.css'
import JSON from './db/db.json'

const root = createRoot(document.getElementById('root'))

class App extends Component {


    state={
        news: JSON,
        footerText: 'i am footerrrr'
    }

    
    render(){
        //console.log(this.state.news)   // اینجا جیسون را در استیت ریختیم 
        const { news, footerText } = this.state ;
        return(
        <>
        <Header/>

        
        {/* حال باید جیسون رو بدیم به کاپوننت زیر */}
        <NewsList 
        news={news}
        />
        <Footer footerText={footerText}/>
        </>
        )
    }
}

root.render(<App/>)
```
## جلسه 16
برای گذاشتن children ، در قسمت نیوز کد را به صورت زیر تغییر می دهیم 

```javascript
        <NewsList 
        news={news}
        >
       <br/>
       <h1>i am children</h1>
            </NewsList>
```

و در کامپوننت نیوز ، {props.children} را اضافه می کنیم .  
```javascript
    return(
        <>
           {news}
           {props.children}
        </>
    )
```

## جلسه 17 
دو کد زیر با م برابر اند در استایل دهی 
```javascript
import React, { Component } from 'react';

class Header extends Component {

    state = {
        active : false,
        keywords: '',

    }

    inputChangeHandler = (event) => {
        this.setState({
            keywords: event.target.value
        })
    }

    render() {
        return (

            <header style={style.background}>
                <div className='logo'>Logo</div>
                <input
                    onChange={this.inputChangeHandler}
                />
                {this.state.keywords}

            </header>
        )
    }
}

let style={
    background: {
        background:'green'
    }
}
export default Header;
```

```javascript
import React, { Component } from 'react';

class Header extends Component {

    state = {
        active : false,
        keywords: '',

    }

    inputChangeHandler = (event) => {
        this.setState({
            keywords: event.target.value
        })
    }

    render() {
        return (

            <header style={{background:'red'}}>
                <div className='logo'>Logo</div>
                <input
                    onChange={this.inputChangeHandler}
                />
                {this.state.keywords}

            </header>
        )
    }
}


export default Header;
```


دو راه نوشتن دستور if 
```javascript
        if(this.state.active){
            //true
        }else{
            //false
        }

        this.state.active ? '':''
```

در کد زیر اگر اکتیو ترو بود رنگ قرمز اگر فالس بود رنگ سبز
```javascript
import React, { Component } from 'react';

class Header extends Component {

    state = {
        active : false,
        keywords: '',

    }

    inputChangeHandler = (event) => {
        this.setState({
            keywords: event.target.value
        })
    }

    render() {

        return (

            <header style={{background:`${this.state.active ?'red':'green'}`}}>
                <div className='logo'>Logo</div>
                <input
                    onChange={this.inputChangeHandler}
                />
                {this.state.keywords}

            </header>
        )
    }
}


export default Header;
```
در کد زیر اگر ولیو خالی بود مقدار اکتیو فالس می شود . و اگر پر بود مقدار اکتیو ترو می شود. 
```javascript
import React, { Component } from 'react';

class Header extends Component {

    state = {
        active : false,
        keywords: '',

    }

    inputChangeHandler = (event) => {
        const value =event.target.value === ''?false : true;
        this.setState({
            active:value,
            keywords: event.target.value
        })
    }

    render() {

        return (

            <header style={{background:`${this.state.active ?'red':'green'}`}}>
                <div className='logo'>Logo</div>
                <input
                    onChange={this.inputChangeHandler}
                />
                {this.state.keywords}

            </header>
        )
    }
}


export default Header;
```
کد بالا رو به کد زیر تغییر می دهیم که نوشتن متن در تکس باکس ، کلاس هدر به اکتیو و نات اکتیو تغییر می کند .
```javascript
import React, { Component } from 'react';

class Header extends Component {

    state = {
        active : 'active',
        keywords: '',

    }

    inputChangeHandler = (event) => {
        const value =event.target.value === ''?'active' : 'not-active';
        this.setState({
            active:value,
            keywords: event.target.value
        })
    }

    render() {

        return (

            // <header style={{background:`${this.state.active ?'red':'green'}`}}>
            <header className={this.state.active}>
                <div className='logo'>Logo</div>
                <input
                    onChange={this.inputChangeHandler}
                />
                {this.state.keywords}

            </header>
        )
    }
}


export default Header;
```
