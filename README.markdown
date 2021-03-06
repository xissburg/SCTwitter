The SCTwitter framework is to facilitate the implementation of twitter, simpler and cleaner using blocks

![]( http://www.lucascorrea.com/sctwitter2.png)

Installation
=================
Run the command

	git clone https://github.com/lucascorrea/SCTwitter.git

Then we need to get the submodules

	git submodule update --init --recursive



Getting Started
=================
Now we need to copy the `SCTwitter.h` `SCTwitter.m` and `Twitter+OAuth` for your project.
	
Now in it's `AppDelegate` need to add credentials ConsumerKey and ConsumerSecret

	#import "SCTwitter.h"
	@implementation AppDelegate

	- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
	{       
    		//Your application credentials ConsumerKey and ConsumerSecret Twitter
    		[SCTwitter initWithConsumerKey:@"D6vneoIuMP0pdBZJAV7gg" consumerSecret:@"wWc59eahiaES9ZCZ7wp28Rw4hcURG4fmIXvvwJiaR8"];
    		return YES;
	}


In your project will build on Settings > Header Search Paths - and add this line below
	
	${SDKROOT}/usr/include/libxml2

Finally add the framework

	libxml2.dylib

Methods
===========

There is 12 methods:

	+ (BOOL)isSessionValid;
	+ (void)loginViewControler:(UIViewController *)aViewController callback:(void (^)(BOOL success))aCallback;
	+ (void)logoutCallback:(void(^)(BOOL success))aCallback;
	+ (void)postWithMessage:(NSString *)message callback:(void (^)(BOOL success, id result))aCallback;
	+ (void)getPublicTimelineWithCallback:(void (^)(BOOL success, id result))aCallback;
	+ (void)getUserTimelineFor:(NSString *)username sinceID:(unsigned long)sinceID startingAtPage:(int)page count:(int)count callback:(void (^)(BOOL success, id result))aCallback;
	+ (void)getUserInformationCallback:(void (^)(BOOL success, id result))aCallback;
	+ (void)getUserInformationFor:(NSString *)username callback:(void (^)(BOOL success, id result))aCallback;
	+ (void)directMessage:(NSString *)message to:(NSString *)username callback:(void (^)(BOOL success, id result))aCallback;
	+ (void)retweetMessageUpdateID:(NSString *)updateID callback:(void (^)(BOOL success, id result))aCallback;
	+ (void)postWithMessage:(NSString *)message uploadPhoto:(UIImage *)image callback:(void (^)(BOOL success, id result))aCallback;
	+ (void)postWithMessage:(NSString *)message uploadPhoto:(UIImage *)image latitude:(double)lat longitude:(double)lng callback:(void (^)(BOOL success, id result))aCallback;


Example Usage
=============

To use the component is very easy. Import the header for your class.

	#import "SCTwitter.h"
	@implementation ViewController

	#pragma mark - Button Action
	- (IBAction)login:(id)sender {    
	 [SCTwitter loginViewControler:self callback:^(BOOL success){
    
     }];
	}
	
	- (IBAction)postBackgroundButtonAction:(id)sender 
	{
    	[SCTwitter postWithMessage:messageText.text callback:^(BOOL success, id result) {
    
    	}];
    }
    
    - (IBAction)userTimelineButtonAction:(id)sender 
	{
	    [SCTwitter getUserTimelineFor:@"lucasc0rrea" sinceID:0 startingAtPage:0 count:200 callback:^(BOOL success, id result) {
        if (success) {
            //Return array NSDictonary
            NSLog(@"%@", result);
        } 
    	}];
	}
	
	- (IBAction)directMessageButtonAction:(id)sender 
	{
 	   [SCTwitter directMessage:messageText.text to:nil callback:^(BOOL success, id result) {

	        if (success) {
        	    //Return array NSDictonary
    	        NSLog(@"%@", result);
	        }else{
          	  NSLog(@"Error : %@", result);
        	}
    	}];
	}

License
=============

SCTwitter is licensed under the MIT License:

Copyright (c) 2012 Lucas Correa (http://www.lucascorrea.com/)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
