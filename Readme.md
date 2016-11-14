# SegueHandlerType

A "Protocol Oriented Programming" approach to storyboard segue management.

## Requirements

It works only with Swift 3.0 (Xcode 8+)

## Usage

First of all, you need to define a *SegueIdentifier* enum, with all segues of your controller. The raw value has to be the exact identifier used in storyboard.

Once this is done, you can use the two methods provided by the protocol:

+ *segueIdentifier(for segue: UIStoryboardSegue) -> SegueIdentifier* , returns the *SegueIdentifier* value for the current segue. Attention: if the segue is not handled your app will crash!
+ *performSegue(with segueIdentifier: SegueIdentifier, sender: Any?)* , perform a specific segue

## Example 

Here is a simple example.

```
class HomeViewController: UIViewController, SegueHandlerProtocol {
 
    enum SegueIdentifier : String {
        case showRed = "ShowRed"
        case showBlue = "ShowBlue"
        case showMagic = "ShowMagic"
    }
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
 
    // MARK: - Navigation
 
    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        switch segueIdentifier(for: segue) {
        case .showRed:
            // logic here
        case .showBlue:
            // logic here
        case .showMagic:
            // logic here
        }
    }
    
    // MARK: - Actions
    
    @IBAction func doSomethingMagic() {
        performSegue(withIdentifier: .showMagic, sender: nil)
    }
}
```