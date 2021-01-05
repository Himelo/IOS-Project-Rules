<p align="center" width="100%">
  <img width="200px" src="https://user-images.githubusercontent.com/46745325/103060932-0649d600-45ed-11eb-84d8-9ceb0ad6b931.png"></img>
</p>

> 프로젝트 진행이 힘들다 생각하시면, 당근을 넣어 주세요 🥕 
## IOS 프로젝트 진행을 위한 Himelo Rules

>###### 우리의 난리치는 코드를 피하기위해서 시작도 전에 정리하고자 규칙을 정해볼까 합니다..
> >###### 선생님들도 번뜩이는 아이디어가 생기신다면 추가해 주시길 부탁드립니다...
---------------

###### Sections  

- [Caution](#caution)
- [Naming Rule](#naming-rule)
  - Constants
  - Variables
- [Types](#types)
- [Parameters and Results](#parameters-and-results)
  - Function
  - [Struct](#struct)
- [Coding Style](#coding-style)
 
 ## Caution
 ***스토리보드 파일 절대 공동 작업 금지***
 
 ***습관성 클릭 및 드래그 금지***
 
 ***다른사람 스토리보드 건들면 텍사스데브라질 쏘기***
 
 ## Naming Rule
 상수와 변수를 구분하여 선언해 주세요.
 xcode project 내에서, <kbd>⌥ Option</kbd> + click 으로 선언한 상수 또는 변수의 정확한 type을 확인할 수 있습니다.
 ##### Camel case를 따라 작성해주도록 합시다
 > 함수 이름은 아직 정하진 않았지만, 너무 자기 맘대로 하지는 않았음 좋겠습니다. 자료 조사좀 더 하고 자세한 규칙 정해봅시다.
 > > ex) 로그인 버튼을 터치했을 때 실행하는 함수
 ```swift
   func onPress_UserLogin(){...}  // x
   func handleLoginButtonPress(){...} // 0
 ```

> 상수/변수 이름은 Camel case rule에 따라 잘 작성해주십쇼.
단일 명사로 이름을 지을 때 단순한 (count, name, userID 등)   
네이밍은 편하게 지어주세요.   
그런데 단순 명사로 표현하기 힘들때, 길어도 더 이해하기 쉽게 작성좀 부탁드립니다. 괴롭습니다.
```swift
  /// nOfC 가 뭐지?
  let nOfC = 12;
  let numberOfCarrot = 12;
  
  /// to 가 뭐지?
  func printHello(to: String) {
    print ("Hello " + to)
  }
  printHello(to: "원영")
```
> 또한 상수/변수를 구분하여 선언해주세요.
```swift
  // Constant
  let numberOfCarrot = 5;
  
  // Variable
  var numberOfCarrot = "10";
```
> Class, Struct와 enum은 대문자로 시작해서 선언합시다.
```swift
  // Struct
  struct Rectangle {
    let width: Int
    let height: Int
    
    var area: Int {
        return width * height
    }
    
    func isBiggerThan(_ rectangle: Rectangle) -> Bool {
        return area > rectangle.area
    }
  }
  
  // Enum
  // enum은 복수형은 사용하지 않습니다.
  enum FoodChoice{
    case apple, orange, banana
    
    switch self{
    case .apple
      return "🍎"
    case .orange
      return "🍊"
    case .banana
      return "🍌"
    }
  }
```
---------------

## Types
선언한 상수/변수에 대하여 해당 타입을 정확히 명시해 주세요.
함수나 배열에도 마찬가지에요. 파라미터와 인자에도 정확한 타입을 명시해주세요.
```swift
 let numberOfCarrot : Int = 5;
 var currentState : String = "logged";
 let array : [Int] = [1,2,3,4,5];
 func handleUserActionOnPress(state : String) { ... };
 
 // 간단하게 인자를 명시할 때도 마찬가지로요
 func example(num : Int) -> Int{
    return num;
  }
  print(example(num: 10));
```
> swift에서는, 프로그래머의 귀찮은 타입 명시를 그나마 편안하게 하기 위해서 다음과 같이 _ 문자를 통해
> 타입 입력을 제한할 수 있는데 우리는 하지 맙시다.
```swift
func printHelloTo(_ name: String) {
    print("Hello " + name + "🥕");
}
```

> 개발할때, 안정적인 프로그램을 만들고자 변수보다는 ***상수***를, Class보다는 ***Struct***을 써주세요.

## Parameters and Results

### Struct

> Struct의 custom initalizer 사용법
```swift
  struct Rectangle {
    let width: Int
    let height: Int
    
    var area: Int {
        return width * height
    }
    
    init(myWidth: Int, myHeight: Int){
      area = myWidth * myHeight + 10
    }
    
    func isBiggerThan(_ rectangle: Rectangle) -> Bool {
        return area > rectangle.area
    }
  }
```

> Struct 내부의 property 값을 바꾸는 method는 mutating을 사용해야합니다.
```swift
  struct Odometer {
    var count: Int = 0
    
    mutating func increment() {
      count += 1
    }
  }
  
  var odometer = Odometer()
  odometer.increment()
```

## Coding Style
강의에 나온것 같이(App Dev 19강) Outlet은 `viewDidLoad()`위에 Action은 아래에 작성합시다.
```swift
  class ViewController: UIViewController {
    @IBOutlet weak var toggle: UISwitch!
    @IBOutlet weak var slider: UISlider!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }

    @IBAction func buttonTapped(_ sender: Any) {
        print("Button was tapped!")
        
        if toggle.isOn{
            print("The switch is on!")
        } else {
            print("The switch is off!")
        }
    }
  }
```
