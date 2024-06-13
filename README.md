# Conceptos_kotlin

package org.example

//nformación sobre variables anulables y no anulables

/*fun main() {

    var favoriteActor: String? = "Sandra oh"
    
    println(favoriteActor)


    favoriteActor = null
    
    println(favoriteActor)
    
}*/

//Escribe un valor Int anulable

/*fun main() {

    var number: Int? = 10
    
    println(number)


    number= null
    
    println(number)
    
}*/

//Usa el operador de llamada segura ?..

/*fun main() {

    var favoriteActor: String? = null
    
    println(favoriteActor?.length)
    
}*/

//Usa el operador de aserción no nulo de !!

/*fun main() {

    var favoriteActor: String? = "Sandra Oh"
    
    println(favoriteActor!!.length)
}*/

//Usa los condicionales if/else

/*fun main() {

    var favoriteActor: String? = null
    
    if (favoriteActor != null) {
    
        println("The number of characters in your favorite actor's name is ${favoriteActor.length}.")
        
    }else {
    
        println("You didn't input a name.")
    }

}*/

//Expresiones if/else

/*fun main() {

    var favoriteActor: String? = "Sandra Oh"

    val lengthOfName = if(favoriteActor != null) {
    
        favoriteActor.length
        
    } else {
    
        0
        
    }
    
    println("The number of characters in your favorite actor's name is $lengthOfName.")
}*/

//Usa el operador Elvis ?:

/*fun main() {

    val favoriteActor: String? = "Sandra Oh"

    val lengthOfName = favoriteActor?.length ?: 0

    println("The number of characters in your favorite actor's name is $lengthOfName.")
}*/

