```shell
# Computazione del pi greco
var cloud= [type="azure", language="nodejs", threads=100]

var ch = [type="channel"] on cloud                       
            
func hit(i){                                                          
var r = [type="random"]              
   var x = r.nextDouble()                          
   var y = r.nextDouble()     
   var msg=0
   if((x*x)+(y*y)<1.0){msg=1}      
   ch!msg   
}  

func estimation(){            
   var sum = 0        
   var crt = 0        
   for i in [0:1000000] {     
   	sum += ch? as Integer      
   	crt += 1  
}
   println "pi estimation: "+ (sum*4.0)/crt  
}

fly hit in [0:1000000] on cloud thenall estimation

```