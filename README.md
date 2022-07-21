<h1 align="center">넷플릭스 로그인화면 클론 🎬</h1>

## ⭐️ 앱 소개
- 넷플릭스 로그인화면을 코드로 만들면서 델리게이트 패턴, 애니메이션, 모달의 사용법을 익힘
## ⭐️ 앱 화면
<img width="300px" height="600px" src="https://user-images.githubusercontent.com/70146658/179695227-a75970e9-12dc-4b63-8452-510644b5d51f.gif"/>



## ⭐️ 타이머 사용(target 방법)
```swift
  weak var timer: Timer?
  
  // 타이머를 실행하는 버튼
  @IBAction func startButtonTapped(_ sender: UIButton) {
        timer?.invalidate()
        timer = Timer.scheduledTimer(timeInterval: 1.0, target: self, selector: #selector(timerAction), userInfo: nil, repeats: true)
  }
  
  @objc func timerAction() {
  // 타이머 내부구현
  }

```

## ⭐️ 타이머 사용(클로저 방법)
```swift
  weak var timer: Timer?
  
  @IBAction func startButtonTapped(_ sender: UIButton) {
        timer?.invalidate()
        timer = Timer.scheduledTimer(withTimeInterval: 1.0, repeats: true, block: { [self] _ in
            // 내부 구현
        })
  }

```
- 클로저 방법같은 경우에는 강한 사이클 참조가 일어나는지 유의해서 코드를 작성해야 함.
- weak으로 timer를 선언해서 viewController에 있는 timer속성은 실제로 Timer인스턴스를 생성할 때 약한참조로 가르킨다. 
- 생성된 Timer인스턴스는 새롭게 생긴 클로저 영역을 참조하게 되고 클로저 영역은 viewController의 timer에 강한 참조를 함([self] 때문)






