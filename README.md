# Conceptos_kotlin

package org.example

// Cómo almacenar una función en una variable

/*fun main() {

    val trickFunction = ::trick

}

fun trick() {

    println("No treats!")

}
*/
//Cómo volver a definir la función con una expresión lambda

/*fun main (){

    val trickFunction = trick

    trick()

    trickFunction()

}

val trick = {

    println ("No treats!")

}*/
//Cómo usar funciones como un tipo de datos

/*fun main (){

    val trickFunction = trick

    trick()

    trickFunction()

    treat()
}

val trick = {

    println ("No treats!")

}

val treat:()->Unit = {

    println("have a treat!")
}*/

//Cómo usar una función como tipo de datos que se muestra


/*fun main (){

    val treatFunction= trickOrTreat(false)

    val trickFunction= trickOrTreat(true)

    treatFunction()

    trickFunction()
}

fun trickOrTreat(isTrick: Boolean): ()->Unit {

  if(isTrick){

    return trick

     } else {

    return treat

  }

}

val trick = {

    println ("No treats!")

}

val treat = {

    println("have a treat!")

}*/

//Cómo pasar una función a otra como un argumento

/*fun main (){

    val coins: (Int) -> String = { quantity ->

       "$quantity quarters "

    }

    val cupcake: (Int) -> String = {

       "have a cupcake!"

    }

    val treatFunction = trickOrTreat(false, coins)

    val trickFunction = trickOrTreat(true, cupcake)

    treatFunction()

    trickFunction()

}

fun trickOrTreat(isTrick: Boolean , extraTreat: (Int) -> String): ()->Unit {

  if(isTrick){

       return trick

     } else {

         println(extraTreat(5))

       return treat

  }

}

val trick = {

    println ("No treats!")

}

val treat = {

    println("Have a treat!")

}*/

//Tipos de funciones anulables


/*fun main (){

    val coins:(Int)->String ={ quantity->

        "$quantity quarters "

    }

    val treatFunction= trickOrTreat(false, coins)

    val trickFunction= trickOrTreat(true, null)

    treatFunction()

    trickFunction()

}


fun trickOrTreat(isTrick: Boolean , extraTreat: ((Int) -> String)?): ()->Unit {

  if(isTrick){

    return trick

     } else {if (extraTreat != null) {

      println(extraTreat(5))

  }
    return treat

  }

}

val trick = {

    println ("No treats!")

}

val treat = {

    println("have a treat!")
}*/

// Cómo escribir expresiones lambda con sintaxis abreviada}

/*fun main (){

    val coins: (Int)->String ={

        "$it quarters "

    }

    val treatFunction= trickOrTreat(false, coins)

    val trickFunction= trickOrTreat(true, null)

    treatFunction()

    trickFunction()

}

fun trickOrTreat(isTrick: Boolean , extraTreat: ((Int) -> String)?): ()->Unit {

  if(isTrick){

    return trick

     } else {if (extraTreat != null) {

      println (extraTreat(5))

  }

    return treat

  }

}

val trick = {

    println ("No treats!")

}

val treat = {

    println("have a treat!")
}*/

//Cómo pasar una expresión lambda directamente a una función

/*fun main (){

    val treatFunction= trickOrTreat(false, { "$it quarters" })

    val trickFunction= trickOrTreat(true, null)

    treatFunction()

    trickFunction()

}

fun trickOrTreat(isTrick: Boolean , extraTreat: ((Int) -> String)?): ()->Unit {

  if(isTrick){

    return trick

     } else {if (extraTreat != null) {

      println (extraTreat(5))

  }
    return treat

  }

}

val trick = {

    println ("No treats!")

}

val treat = {

    println("have a treat!")
}*/

//Cómo usar la sintaxis de expresión lambda al final

/*fun main (){

    val treatFunction= trickOrTreat(false){ " $it quarters" }

    val trickFunction= trickOrTreat(true, null)

    treatFunction()

    trickFunction()

}

fun trickOrTreat(isTrick: Boolean , extraTreat: ((Int) -> String)?): ()->Unit {

  if(isTrick){

    return trick

     } else {if (extraTreat != null) {

      println (extraTreat(5))

  }
    return treat

  }

}

val trick = {

    println (" No treats!")

}

val treat = {

    println(" have a treat!")

}*/

// Cómo usar la función repeat()

/*fun main (){

    val treatFunction= trickOrTreat(false){ " $it quarters" }

    val trickFunction= trickOrTreat(true, null)

    repeat(4){

        treatFunction()

    }

    trickFunction()

}

fun trickOrTreat(isTrick: Boolean , extraTreat: ((Int) -> String)?): ()->Unit {

  if(isTrick){

    return trick

     } else {if (extraTreat != null) {

      println (extraTreat(5))

  }
    return treat

  }

}

val trick = {

    println (" No treats!")

}

val treat = {

    println(" have a treat!")

}*/
