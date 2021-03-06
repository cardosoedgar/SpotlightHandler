# SpotlightHandler
A simple way to index your application making it visible on Spotlight Search

#0.1.4 Update
Define what App icon will be used in index search. If pass "nil", the search will be indexed with icon named "AppIcon"

# Pod

Podfile
```
pod "SpotlightHandler"
```

Terminal
```
pod install
```

# Usage
The first step is to make your ViewController a subclass of BaseIndexableViewController like shown below:

```
#import "BaseIndexableViewController.h"

@interface ViewController : BaseIndexableViewController


@end
```

That way, the Spotlight settings are already visible in the Interface Builder
![alt tag](https://cloud.githubusercontent.com/assets/14286416/13165288/07415f88-d6a3-11e5-82a9-a996be52e7e4.png)
#
Then just fill the fields in the way that you prefer

![alt tag](https://cloud.githubusercontent.com/assets/14286416/13165289/07498f64-d6a3-11e5-98d3-27a8f84b8e6e.png)
#
(Don't forgot to turn on the Spot Indexable field) =)

#AppDelegate
Finally, let's add a method in our AppDelegate class, that will be responsible by identify the Spotlight's action and show the selected controller

```
- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray * _Nullable))restorationHandler
{
    if ([userActivity.activityType isEqualToString:CSSearchableItemActionType]) {
        NSString *uniqueIdentifier = userActivity.userInfo[CSSearchableItemActivityIdentifier];
        
        [SpotlightHandler openController:uniqueIdentifier];
    }
    
    return YES;
}
```
