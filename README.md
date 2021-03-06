# Tab-Bar

タブバーの練習<br>
UITabBarControllerを使用

## プレビュー
<img src="https://i.gyazo.com/cb0e228a07f6e025d6bf3db6bdc33406.png" width="400">

```swift
import UIKit

class ViewController: UIViewController {
    
    private let button: UIButton = {
        let button = UIButton(frame: CGRect(x: 0, y: 0, width: 200, height: 52))
        button.setTitle("Log In", for: .normal)
        button.backgroundColor = .white
        button.setTitleColor(.black, for: .normal)
        
        return button
    }()

    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .systemBlue
        view.addSubview(button)
        button.addTarget(self, action: #selector(didTapButton), for: .touchUpInside)
    }

    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
        button.center = view.center
    }
    
    @objc func didTapButton() {
        let tabBarVC = UITabBarController()
        
        let vc1 = UINavigationController(rootViewController: FirstViewController())
        let vc2 = UINavigationController(rootViewController: SecondViewController())
        let vc3 = UINavigationController(rootViewController: ThirdViewController())
        let vc4 = UINavigationController(rootViewController: FourthViewController())
        let vc5 = UINavigationController(rootViewController: FifthViewController())
        
        vc1.title = "Home"
        vc2.title = "Contact"
        vc3.title = "Help"
        vc4.title = "About"
        vc5.title = "Settings"
        
        tabBarVC.setViewControllers([vc1, vc2, vc3, vc4, vc5], animated: false)
        
        let images = ["house", "bell", "person.circle", "star", "gear"]
        
        guard let items = tabBarVC.tabBar.items else {
            return
        }
        
        for x in 0..<items.count {
            items[x].badgeValue = "1"
            items[x].image = UIImage(systemName: images[x])
        }
        
        tabBarVC.modalPresentationStyle = .fullScreen
        present(tabBarVC, animated: true)
    }
    
}

class FirstViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .red
        
    }
}

class SecondViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .lightGray
        
    }
}

class ThirdViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .purple
        
    }
}

class FourthViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .green
        
    }
}

class FifthViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .orange
        
    }
}
```
