# creativeNinja
phonegap ios9.2 notification Problem


phonegap localnotification plugin 
https://github.com/katzer/cordova-plugin-local-notifications has some problems with IOS9.2.

Follow step by step to produce local notification for you individial event.

Both cases are included

#1 when app is not in foreground

2# when app is in foreground

//-----------------implementation file-----------------------------ios----------

#import "localNotification.h"

@implementation localNotification

-(void)customLocalNotification:(CDVInvokedUrlCommand*)command
{
    NSLog(@"local notification called");
    NSString * message =[command.arguments objectAtIndex:0];
    UILocalNotification* localNotification = [[UILocalNotification alloc] init];
    localNotification.fireDate = [NSDate dateWithTimeIntervalSinceNow:10];
    localNotification.alertTitle = @"Hurre";
    localNotification.alertBody = message;
    localNotification.applicationIconBadgeNumber = 1;
    localNotification.timeZone = [NSTimeZone defaultTimeZone];
    localNotification.soundName = UILocalNotificationDefaultSoundName;
    [[UIApplication sharedApplication] presentLocalNotificationNow:localNotification];
}
@end





//--------------------Headder file-----------------------------


#import <Cordova/CDVPlugin.h>

@interface localNotification : CDVPlugin
{
    
}
- (void) customLocalNotification:(CDVInvokedUrlCommand*)command;

@end





-------------------------------Javascript plugin calling-------------------------------

cordova.exec(function(){alert('success');}, function(){alert('fail')}, "localNotification", "customLocalNotification",[message]);
                                                                    
               }).fail(function(error)
                       {
                       //  alert(" hi beacon");
                       console.log("listchallenges get fail", arguments);
                       });



Add this javascript as a plugin file and add this to your windows object or cordova.

and that function from your javascript app.js code.


or you can also call the function like this.







I will add more functions and methods so you could perform more task like scheduling and other features.
##########Thanks
