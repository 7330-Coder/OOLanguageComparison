# Chapter 6 : Instance Reference Name in Data Type
In Swift, the keyword self is used to access instance properties and methods.
```
struct Weather {

  let windSpeed: Int    // miles per hour
  let chanceOfRain: Int // percent

  init(windSpeed: Int, chanceOfRain: Int) {
    self.windSpeed = windSpeed
    self.chanceOfRain = chanceOfRain
  }

  func isDayForWalk() -> Bool {
    let comfortableWindSpeed = 5
    let acceptableChanceOfRain = 30
    return self.windSpeed <= comfortableWindSpeed
      && self.chanceOfRain <= acceptableChanceOfRain
  }

}
```
It is also used to access type properties and methods.
```
struct Const {  
  static let minLimit = 0
  static let maxLimit = 250
  static func getLimitRange() -> ClosedRange<Int> {
    return self.minLimit...self.maxLimit    
  }
}
print(Const.getLimitRange()) // => 0...250  
```