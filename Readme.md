# SegueHandlerType

A "Protocol Oriented Programming" approach to storyboard segue management.

## Usage

First of all, you need to define a *SegueIdentifier* enum, with all segues of your controller. The raw value have to be the exact identifier used in storyboard.

Once this is done, you can use the two methods provided by the protocol:

+ *segueIdentifierForSegue(segue: UIStoryboardSegue) -> SegueIdentifier* , returns the *SegueIdentifier* value for the current segue. Attention: if the segue is not handled your app will crash!
+ *performSegueWithIdentifier(segueIdentifier: SegueIdentifier, sender: AnyObject?)* , perform a specific segue

## Example 

Here is a simple example.

```
class HomeViewController: UIViewController, SegueHandlerType {
 
    enum SegueIdentifier : String {
        case ShowRed = "ShowRed"
        case ShowBlue = "ShowBlue"
        case ShowMagic = "ShowMagic"
    }
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
 
    // MARK: - Navigation
 
    override func prepareForSegue(segue: UIStoryboardSegue, sender: AnyObject?) {
        switch segueIdentifierForSegue(segue) {
        case .ShowRed:
            // logic here
        case .ShowBlue:
            // logic here
        case .ShowMagic:
            // logic here
        }
    }
    
    // MARK: - Actions
    
    @IBAction func doSomethingMagic() {
        performSegueWithIdentifier(.ShowMagic, sender: nil)
    }
}
```