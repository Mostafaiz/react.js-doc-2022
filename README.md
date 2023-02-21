# شروعی بر react.js

در این قسمت، خلاصه درس ها به صورت داکیومنت و `Code` جهت یادگیری و یادآوری نوشته می شود.

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

استفاده از css در درون componnent 
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
