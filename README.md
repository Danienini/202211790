# 202211790
numbers to words
/*202211790*/
fun main() {
    print("Enter an integer: ")
    val number = readLine()?.toIntOrNull()

    if (number == null || number < 0 || number > 999_999_999_999) {
        println("")
        return
    }

    val result = convertNumberToWords(number)
    println("Number in words: $result")
}

fun convertNumberToWords(number: Int): String {
    if (number == 0) {
        return "zero"
    }

    val units = arrayOf("", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine")
    val tens = arrayOf("", "", "twenty", "thirty", "forty", "fifty", "sixty", "seventy", "eighty", "ninety")
    val teens = arrayOf("ten", "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen")

    return when {
        number < 10 -> units[number]
        number < 20 -> teens[number - 10]
        number < 100 -> tens[number / 10] + if (number % 10 != 0) " " + units[number % 10] else ""
        number < 1000 -> units[number / 100] + " hundred" + if (number % 100 != 0) " " + convertNumberToWords(number % 100) else ""
        number < 1000000 -> convertNumberToWords(number / 1000) + " thousand" + if (number % 1000 != 0) " " + convertNumberToWords(number % 1000) else ""
        else -> convertNumberToWords(number / 1000000) + " million" + if (number % 1000000 != 0) " " + convertNumberToWords(number % 1000000) else ""
    }
}

