# شروعی بر react.js

در این قسمت، خلاصه درس ها به صورت داکیومنت و `Code` جهت یادگیری و یادآوری نوشته می شود
https://github.com/ferlobo1985/udmy-React-fullstack-01basics-project.

نود را نصب می کنیم و نمایش ورژن نود جی اس   
```
 node -v
 npm -v 
 yarn -v
 npx -v 
 
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

```
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

```
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

```
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

```
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
```
const { news, footerText } = this.state ;
```

که به صورت زیر می شود 
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
