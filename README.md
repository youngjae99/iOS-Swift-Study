#  iOS-Swift-Study
iOS/Swift development reference archiving


## Apple 공식
- [Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)
- [Swift Language Guide(한글판)](https://jusung.gitbook.io/the-swift-language-guide/)
  번역본 짱....
- [iOS Human Interface Guideline](https://developer.apple.com/design/human-interface-guidelines/ios/overview/themes/)

## Dev 참고 사이트

- [Raywenderlich](https://www.raywenderlich.com/ios/videos)
  튜토리얼 사이트. 영상 강의 굳. 유료결제
- [iOS 튜토리얼 사이트](https://www.ioscreator.com/)
- [iOS Dev 정리](https://github.com/giftbott/iOSDevLinks)
- [Stanford CS193P: Developing Apps for iOS](https://www.youtube.com/playlist?list=PLPA-ayBrweUzGFmkT_W65z64MoGnKRZMq)
  SoC Co-op 사전교육 내용 (App life-cycle과 ViewController life-cycle 중심)


### 2021.1.1 Study 시작
2021.03부터 시작할 NAVER maps iOS/Swift 인턴 대비 Swift iOS Study 시작!

**01.04 (Mon)**

Stanford CS193P Lecture 1: Introduction to iOS 11, Xcode 9 and Swift 4 수강

- Swift Object-Oriented Programming
- What's in iOS? : Core OS - Core Services - Media - Cocoa Touch
    - 이 강의에서는 Core Services에 대해서 집중적으로 배울 예정
- XCode 이해
- Optionals에 대해서 알게됨
- Reading Assignment1 (R1)

Raywenderlich

**2021.01.05 (Tue)**

Swift Document

- The Basics 까지 읽음
    - Optional

Stanford CS193P Lecture 2: MVC's

- MVC : Model, Controller, View 이 세가지로 나눌 수 있음
    - Model : What your application is(not visible)
    - Controller : How your Model is presented to the user (UI logic)
    - View : Your Controller's minions
    - MVC는 앱의 하나의 화면에 하나만 대응된다.
    - MVC 패턴의 장점 : 어플리케이션에서 세부분 각각에 대한 분업이 쉬워짐. 효율 up. 유지보수성, 어플리케이션의 확장성, 유연성 증가
    
    - Demo
    - MVC
    - struct vs class
        - 다른 언어와 다르게 Swift에서는 class와 struct가 거의 비슷한 역할.
        1. struct = inherit 불가, class는 가능
        2. struct는 value type, class는 reference type이다 (중요).
    - static methods and properties
    - more about Optionals
    - Dictionary<KeyType, ValueType>
    - UIStackView

**2021.01.06 (Wed)**

Swift Document

- **Basic Operators**
    - Nil-Coalescing Operator
    - Range Operators
- **Strings and Characters**
    - String 관련 여러 연산자들. 다른 언어들과 유사.
- **Collection Types**
    - Arrays
    - Sets
    - Dictionaries
- **Control Flow**
    - For-In Loops
    - If statement
    - switch
    - control transfer statements
- **Functions**
    
```swift
func greet(person: String) -> String {
	let greeting = "Hello, "+person+"!"
	return greeting
}

func someFunction(argumentLabel parameterName: Int) {
    // 함수 안애서 parameterName로 argumentLabel의 인자값을 참조할 수 있습니다.
}

func someFunction(_ firstParameterName: Int, secondParameterName: Int) {
    // 함수 안에서 firstParameterName, secondParameterName
    // 인자로 입력받은 첫번째, 두번째 값을 참조합니다.
}

func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temporaryA = a
    a = b
    b = temporaryA
}
```

- in-out parameters : c언어의 pointer과 유사
- Function Types : parameter type, return type으로 구성

**2021.01.07 (Thu)**

Raywenderlich Polishing the App 완강

Part3: A Custom Alert part

- Animation in SwiftUI
- Constants
- MagicNumbers

Part4: A Second Screen

- Size  Classes
- Displaying Multiple Screens
- App Icon and Display Name

**2021.01.08 (Fri)**

Swift Document

- Closures
    - Closures : code block으로 lambdas나 object c의 blocks랑 비슷. 상수나 변수의 참조를 capture해 저장 가능
    - 
- Enumerations (열거형)

    ```swift
    enum CompassPoint {
        case north
        case south
        case east
        case west
    }
    var directionToHead = CompassPoint.west
    directionToHead = .east
    ```

    - Raw Values
- Structures and Classes
    - 

    ```swift
    class SomeClass {
        // 클래스 내용은 여기에
    }
    struct SomeStructure {
        // 구조체 내용은 여기에
    }
    ```

    - 클래스와 구조체는 많은 측면에서 유사하다.
    - 클래스/구조체의 차이점
        - 클래스: 참조타입, 구조체와 열거형은: 값타입
        - 클래스와 구조체의 선택

- Properties
    - Stored Properties(저장 프로퍼티)

        lazy stored properties : 값이 처음으로 사용되기 전까지는 계산되지 않는 프로퍼티

    - Computed Properties(계산 프로퍼티)

        get 과 set으로 나타냄

        ```swift
        struct Rect {
            var origin = Point()
            var size = Size()
            var center: Point {
                get {
                    let centerX = origin.x + (size.width / 2)
                    let centerY = origin.y + (size.height / 2)
                    return Point(x: centerX, y: centerY)
                }
                set(newCenter) { 
                    origin.x = newCenter.x - (size.width / 2)
                    origin.y = newCenter.y - (size.height / 2)
                }
            }
        }

        // newCneter라고 인자 설정 안하면 newValue를 사용할 수 있음
        struct AlternativeRect {
            var origin = Point()
            var size = Size()
            var center: Point {
                get {
                    let centerX = origin.x + (size.width / 2)
                    let centerY = origin.y + (size.height / 2)
                    return Point(x: centerX, y: centerY)
                }
                set {
                    origin.x = newValue.x - (size.width / 2)
                    origin.y = newValue.y - (size.height / 2)
                }
            }

        //읽기전용 계산된 프로퍼티 : getter만 있고, setter를 제공하지 않는 경우
        struct Cuboid {
            var width = 0.0, height = 0.0, depth = 0.0
            var volume: Double {
                return width * height * depth
            }
        }
        let fourByFiveByTwo = Cuboid(width: 4.0, height: 5.0, depth: 2.0)
        print("the volume of fourByFiveByTwo is \(fourByFiveByTwo.volume)")
        // "the volume of fourByFiveByTwo is 40.0" 출력

        ```

        Property Observers

        - willSet
        - didSet

        ```swift
        class StepCounter {
            var totalSteps: Int = 0 {
                willSet(newTotalSteps) {
                    print("About to set totalSteps to \(newTotalSteps)")
                }
                didSet {
                    if totalSteps > oldValue  {
                        print("Added \(totalSteps - oldValue) steps")
                    }
                }
            }
        }
        let stepCounter = StepCounter()
        stepCounter.totalSteps = 200
        // About to set totalSteps to 200
        // Added 200 steps
        stepCounter.totalSteps = 360
        // About to set totalSteps to 360
        // Added 160 steps
        stepCounter.totalSteps = 896
        // About to set totalSteps to 896
        // Added 536 steps
        ```

        Global and Local Variables

        Type Properties : 특정 인스턴스에 속한 프로퍼티. 모든 인스턴스에 공통으로 사용되는 값을 정의할 때 유용

        - Type Property Syntax - static, class 딱 두개로 타입 프로퍼티 선언 가능

※ Swift는 Multi-paradigm language

OOP 개념에 대해서 [https://www.slideshare.net/plusjune/ss-46109239](https://www.slideshare.net/plusjune/ss-46109239)

- Class, Object, Instance
- 캡슐화(Encapsulation) : data + operation on data
- 상속성(Inheritance) : 상속 계층을 따라 특성(data, operation)을 공유
- 다형성(Polymorphism) : 다양한 형태에 동일한 명령을 사용

**프로그래밍 패러다임**

구조적 프로그래밍 Structured Programming - 기능적 분할, 절차중심

객체지향 프로그래밍 Object Oriented Programming - 객체 간 역할과 관계 중심, 객체중심

명령형 프로그래밍 

선언형 프로그래밍

함수형 프로그래밍

객체기반 프로그래밍

- Methods : class, struct, enum과 관련된 함수들
    - Instance Methods : 특정 class, struct, enum에 속한 메소드

        self property - 인자 이름이 프로퍼티 이름과 같은 경우 필수로 써주기

        mutating - 기본적으로 인스턴스 메소드 내에서 값 타입의 프로퍼티를 변경 불가. 이럴때 mutating을 쓰면 됨

        mutating 메소드 내에서 self할당

    - Type Methods

    ```swift
    class SomeClass {
        class func someTypeMethod() {
            // 타입 메소드 구현
        }
    }
    SomeClass.someTypeMethod()    // 타입 메소드 호출!
    ```

    ```swift
    struct LevelTracker{
    	static var highestUnlockedLevel = 1
    	var currentLevel = 1

    	static func unlock(_ level: Int){
    		if level>highestUnlockedLevel { highestUnlockedLevel = level }
    	}
    	static func isUnlocked(_ level: Int) -> Bool{
    		return (level <= highestUnlockedLevel)
    	}
    	
    	mutating func advance(to level: Int){
    		if LevelTracker.isunlocked(level){
    			currentLevel = level
    			return true
    		}
    		else{
    			return false
    		}
    	}
    }

    class Player{
    	var tracker = LevelTracker()
    	let playerName: String
    	func complete(level: Int){
    		LevelTracker.unlock(level+1)
    		tracker.advance(to: level+1)
    	}
    	init(name: String){
    		playerName = name
    	}
    }

    var player = Player(name: "Youngjae")
    player.complete(level: 1)
    print("highest unlocked level is now \(LevelTracker.highestUnlockedLevel)")
    if player.tracker.advace(to: 6){
    	print("player is now on level 6")
    } else{
    	print("level 6 has not yey been unlocked")
    }
    ```
    
**2021.01.09 (Sat)**

Swift Document

- Subscripts
    - assign / retrieve

    ```swift
    subscript(index: Int) -> Int {
        get {
            // 적절한 반환 값
        }
        set(newValue) {
            // 적절한 set 액션
        }
    }
    ```

- Inheritance - class의 특징
    - Base Class(기반 클래스) - 다른 어떤 클래스도 상속받지 않은 클래스
    - Subclassing = 상속

    ```swift
    class SomeSubclass: SomeSuperclass {
        // subclass definition goes here
    }
    ```

    - Overriding : 부모에서 상속받은것을 재정의 하는 것. 인스턴스 메소드, 타입 메소드, 인스턴스 프로퍼티, 타입 프로퍼티, 서브스크립트 모두 가능.
    - final : 오버라이딩 방지
- Initialization - 클래스, 구조체, 열거형 인스턴스를 사용하기 위해 준비 작업을 하는 단계

    ```swift
    init(){
    // perform some initialization here
    }
    ```

    - 내용이 너무 많아서 아직 다 안읽음

- Deinitialization - initializer 직전, 인스턴스가 소멸되기 직전에 호출

    ```swift
    deinit {
        // perform the deinitialization
    }
    ```

    - 초기화 파라미터
    - 기본 이니셜라이저
    
**2021.01.10 (Sun)**

Swift Document

- Optional Chaining - ?를 붙여서 표현, 강제언래핑 대신에 사용

    ```swift
    let roomCount = john.residence!.numberOfRooms
    // 이렇게 강제로 언래핑하면 residence가 nil이기 때문에 오류가 발생함

    if let roomCount = john.residence?.numberOfRooms {
        print("John's residence has \(roomCount) room(s).")
    } else {
        print("Unable to retrieve the number of rooms.")
    }
    // Prints "Unable to retrieve the number of rooms."
    ```

- Error Handling
    - 에러 발생 함수
    - do-catch
    - 옵셔널 이용
    - 에러 발생 중지
- Type Casting
    - 형 확인 : is
    - Downcasting : as? as!
    - Any, AnyObject
- Nested Types
    - 블랙잭 예시
    
**2021.01.11 (Mon)**

Stanford CS193P Lecture 9: View Controller Lifecycle and Scroll View

- View Controllers have a Lifecycle
    - viewWillAppear - just before your MVC appears (or re-appears) on the screen
    - viewDidAppear - after MVC has finished appearing on screen
    - viewWillDisappear - about to go off the screen
    - viewDidDisappear - MVC went off screen. rarely use
- Geometry
    - override func viewWillLayoutSubviews()
    - override func viewDidLayoutSubviews()
- Low Memory : override func didReceiveMemoryWarning() 메모리 부속 시 kill
- awakeFromNib()
- Summary (19:00)

Swift Document

- Extensions
    - 

    ```swift
    extension Double {
        var km: Double { return self 1_000.0 }
        var m: Double { return self }
        var cm: Double { return self / 100.0 }
        var mm: Double { return self / 1_000.0 }
        var ft: Double { return self / 3.28084 }
    }
    let oneInch = 25.4.mm
    print("One inch is \(oneInch) meters")
    // Prints "One inch is 0.0254 meters"
    let threeFeet = 3.ft
    print("Three feet is \(threeFeet) meters")
    // Prints "Three feet is 0.914399970739201 meters"
    ```

- Protocols

Raywenderlich

- UIKit Fundamentals
    - View controller introduction
    - Interface controls
    - Build Simple interface
    - IBAction vs IBOutlet
        - Interface Builder
        - IBOutlet
            - Outlet이란? delegate란?
    - keyboard and responder chain
    - Using image with PHPicker (PhotosUI import)
    - Adding alerts

**2021.01.12 (Tue)**

**2021.01.13 (Wed)**

Raywenderlich

- UIKit Controls

**2021.01.18 (Mon)**

Swift Document

- Generics
- Automatic Reference Counting

iOS App life-cylce

- App-based life-cycle
- Scene-based life-cycle

MVC → ViewController Lifecycle

- loadView, viewDidLoad,  viewWillAppear, viewDidAppear, viewWillDisappear, viewDidDisappear, viewDidUnload로 나눌 수 있음

발표 내용 준비

**2021.01.19 (Tue)**

Swift Document

- Memory Safety
- Access Control

**Co-op 사전교육 App life-cylce & ViewController life-cycle 발표**

[https://docs.google.com/presentation/d/11H1IDPnUkQLXngZ8BSjI_AelEI_tPdlbc0NO3qlHcPE/edit?usp=sharing](https://docs.google.com/presentation/d/11H1IDPnUkQLXngZ8BSjI_AelEI_tPdlbc0NO3qlHcPE/edit?usp=sharing)
