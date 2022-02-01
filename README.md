# شروعی بر react.js

در این قسمت، خلاصه درس ها به صورت داکیومنت و `Code` جهت یادگیری و یادآوری نوشته می شود.


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
```javascript
import React from 'react';
import ReactDom from 'react-dom';

const App = () =>(
            <h1>Hello mostafa</h1>
)

ReactDom.render(<App/>,document.getElementById('root'))
```
کد در حالت بالا کار می کنه اما اگه دوبار `h1` را تکرار کنیم کار نخواد کرد. ولی از بین `</><>` , ` <React.Fragment></React.Fragment>` ,`<div></div>` قرار بگیرد اجرا می شود 
برای نوشتن `class` باید از `className`  استفاده کرد.
```javascript
const App = () =>(
    <div className='one'>
            <h1>Hello mostafa</h1>
            <h2>Hello mostafa</h2>
    </div>
 )
 ```
