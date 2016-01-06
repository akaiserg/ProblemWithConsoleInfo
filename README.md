# Problem With Console info

I used to trust  blindly  that console.info  showed  the values correctly  until I ran into  this problem.

 
I have the following  code:

```javascript
var Module1= function(){
        "use strict";
        this.generateArrayObject=function(){
            var arrayObj=[];            
            arrayObj.push({a:1,b:2});
            arrayObj.push({a2:null,b2:null});            
            return arrayObj;
        }
    };
});

 var m1= new Module1();
 // getting the array
 var aObj= m1.generateArrayObject();
 console.info(aObj);//[{a:1,b:2},{a2:"New value 1",b2:null}]
 aObj[1].a2="New value 1";
 console.info(aObj);//[{a:1,b:2},{a2:"New value 1",b2:null}]
```

The logic  would be  that the first console.info   shouldn't  show the value 'New value 1', but it does. It is due to console.log() being queued up, and it prints a later value of the array or object.

This problem can be seen in Chrome, Firefox and Opera. An easy solution  is to  use  JSON.stringify or use console.table if you have a few values only.



### For more information

 * [console.log() shows the changed value of a variable before the value actually changes](http://stackoverflow.com/questions/11284663/console-log-shows-the-changed-value-of-a-variable-before-the-value-actually-ch)
 * [chromium](https://code.google.com/p/chromium/issues/detail?id=508719)
 * [Bizarre console.log behaviour in Chrome Developer Tools [duplicate]](http://stackoverflow.com/questions/4198912/bizarre-console-log-behaviour-in-chrome-developer-tools) 
 * [Is Chrome's JavaScript console lazy about evaluating arrays?](http://stackoverflow.com/questions/4057440/is-chromes-javascript-console-lazy-about-evaluating-arrays)


#### Note: 

Chrome actually shows   information about  it.

![alt text](https://chromium.googlecode.com/issues/attachment?aid=5087190000001&name=snapshot-tooltip-proposed.png&token=ABZ6GAd_Qvj65oo9HS_BSYnRvCRbTGLjdA%3A1452036803149&id=508719&mod_ts_token=ABZ6GAcUd0aEzRCOXD19T-jo2ULjfeJAvg%3A1452036803149&inline=1)
