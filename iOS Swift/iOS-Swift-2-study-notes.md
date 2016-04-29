# Rounding a double value to x number of decimal places in swift (precision)
Method 1. using round()  
precision is controlled by the number in the division
```
let a = 1.23456789
let b = Double(round(a*1000)/1000)
let c = Double(round(a*100)/100)

print(b) // 1.235
print(c) // 1.23
```
Method 2. One step further to wrap above into an extension
More Swfit extension [here](https://github.com/goktugyil/EZSwiftExtensions)
```
extension Double {
  // Rounds the double to decimal places value
  func roundToPlaces(places:Int) -> Double {
    let devisor = pow(10.0, Double(places))
    return round(self * divisor) / divisor
  }
}
```
Example which will returns Double rounded to 4 decimal places:
```
let x = Double(0.123456789).roundToPlaces(4) // 0.1235
```
Method 3. Use the ```String``` constructor which takes a ```format``` string:
```
print(String(format: "%.3f", 0.123456)) // 0.123
```
