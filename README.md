mis
===

miscellaneous 

* [Tiago Pereira, 1000x10 Log at Público as of 28 Julho 2019](http://jonasalmeida.github.io/mis/TiagoPereira.json)

``` javascript
TP=[] // async calls will accumulate array results here

getTP = async function(i){
    return await (await fetch(`https://www.publico.pt/api/list/utilizador/perfil/25241b78-c64c-409f-8520-b7efcd02fe04?page=${i}`)).json()
}

getTPs = async function(n,i,xx){
    n=n||1000
    i=i||1
    xx=xx||[]
    if(i<=n){
        let xi = await getTP(i)
        xx=xx.concat(xi)
        console.log(i,xi,xx.length,Date())
        //debugger
        getTPs(n,(i+1),xx)
    }else{
        TP=xx
    }
    return TP
}

getTPs()
```
