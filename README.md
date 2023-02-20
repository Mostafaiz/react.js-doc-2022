# شروعی بر react.js

در این قسمت، خلاصه درس ها به صورت داکیومنت و `Code` جهت یادگیری و یادآوری نوشته می شود.

نمایش ورژن نود جی اس   
```
 node -v
 
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
کد در حالت زیر کار می کنه اما اگه دوبار `h1` را تکرار کنیم کار نخواد کرد. ولی اگر بین `</><>` , `<React.Fragment></React.Fragment>` ,`<div></div>` قرار بگیرد اجرا می شود 

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
![8](https://raw.githubusercontent.com/Mostafaiz/react.js-doc-2022/main/image.png)
 
برای ساخت کامپوننت `Header`
```javascript
import React from 'react';

const Header = () =>{
    return <div>Header Hello</div>
}

export default Header;
```
برای فراخوانی آن کامپونت
```
import Header from './components/header';
```
```
<Header/>
```

## جلسه 9
#### class based component 

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
