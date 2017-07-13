You must install the Android release V1.5 or higher to access the 40pin GPIO properly.

This process explains how to make an Android app which can access IO ports.
You need to install Google Android SDK/NDK on your host PC first to start below steps.

Insert this line into your ~/.bashrc file.

export NDK_PATH=/home/xxx/android-ndk-r10d
1. Download the wiringPi library and example App source code.

https://github.com/codewalkerster/example-wiringPi

$ git clone https://github.com/codewalkerster/example-wiringPi -b odroidc
2. Build a JNI library

$ cd example-wiringPi
$ cd jni
$ ndk-build
Android NDK: WARNING: APP_PLATFORM android-19 is larger than android:minSdkVersion 16 in /media/codewalker/projects/wiringpi/android/example-wiringPi_c/AndroidManifest.xml    
[armeabi] Compile thumb  : wiringPi <= wiringPi.c
/media/codewalker/projects/wiringpi/android/example-wiringPi_c/jni/wiringPi/wiringPi.c:147:0: warning: "PAGE_SIZE" redefined
 #define PAGE_SIZE   (4*1024)
 ^
In file included from /home/codewalker/projects/android-ndk-r11b/platforms/android-21/arch-arm/usr/include/sys/ucontext.h:33:0,
                 from /home/codewalker/projects/android-ndk-r11b/platforms/android-21/arch-arm/usr/include/signal.h:51,
                 from /home/codewalker/projects/android-ndk-r11b/platforms/android-21/arch-arm/usr/include/poll.h:34,
                 from /media/codewalker/projects/wiringpi/android/example-wiringPi_c/jni/wiringPi/wiringPi.c:59:
/home/codewalker/projects/android-ndk-r11b/platforms/android-21/arch-arm/usr/include/sys/user.h:37:0: note: this is the location of the previous definition
 #define PAGE_SIZE 4096
 ^
/media/codewalker/projects/wiringpi/android/example-wiringPi_c/jni/wiringPi/wiringPi.c: In function 'interruptHandler':
/media/codewalker/projects/wiringpi/android/example-wiringPi_c/jni/wiringPi/wiringPi.c:2263:7: warning: return makes pointer from integer without a cast
       return wiringPiFailure (WPI_FATAL, "wiringPiISR: wiringPi has not been initialised. Unable to continue.\n") ;
       ^
[armeabi] Compile thumb  : wiringPi <= wiringShift.c
[armeabi] Compile thumb  : wiringPi <= piHiPri.c
[armeabi] Compile thumb  : wiringPi <= piThread.c
[armeabi] Compile thumb  : wiringPi <= wiringPiSPI.c
[armeabi] Compile thumb  : wiringPi <= wiringPiI2C.c
[armeabi] Compile thumb  : wiringPi <= softPwm.c
[armeabi] Compile thumb  : wiringPi <= softTone.c
[armeabi] Compile thumb  : wiringPi <= mcp23008.c
[armeabi] Compile thumb  : wiringPi <= mcp23016.c
[armeabi] Compile thumb  : wiringPi <= mcp23017.c
[armeabi] Compile thumb  : wiringPi <= mcp23s08.c
[armeabi] Compile thumb  : wiringPi <= mcp23s17.c
[armeabi] Compile thumb  : wiringPi <= sr595.c
[armeabi] Compile thumb  : wiringPi <= pcf8574.c
[armeabi] Compile thumb  : wiringPi <= pcf8591.c
[armeabi] Compile thumb  : wiringPi <= mcp3002.c
[armeabi] Compile thumb  : wiringPi <= mcp3004.c
[armeabi] Compile thumb  : wiringPi <= mcp4802.c
[armeabi] Compile thumb  : wiringPi <= mcp3422.c
[armeabi] Compile thumb  : wiringPi <= max31855.c
[armeabi] Compile thumb  : wiringPi <= max5322.c
[armeabi] Compile thumb  : wiringPi <= sn3218.c
[armeabi] SharedLibrary  : libwiringPi.so
[armeabi] Install        : libwiringPi.so => libs/armeabi/libwiringPi.so
[armeabi] Compile thumb  : wiringPiDev <= ds1302.c
[armeabi] Compile thumb  : wiringPiDev <= maxdetect.c
[armeabi] Compile thumb  : wiringPiDev <= piNes.c
[armeabi] Compile thumb  : wiringPiDev <= gertboard.c
[armeabi] Compile thumb  : wiringPiDev <= piFace.c
[armeabi] Compile thumb  : wiringPiDev <= lcd128x64.c
[armeabi] Compile thumb  : wiringPiDev <= lcd.c
[armeabi] Compile thumb  : wiringPiDev <= piGlow.c
[armeabi] SharedLibrary  : libwiringPiDev.so
[armeabi] Install        : libwiringPiDev.so => libs/armeabi/libwiringPiDev.so
[armeabi] Compile thumb  : wpi_android <= wpi_android.c
[armeabi] SharedLibrary  : libwpi_android.so
[armeabi] Install        : libwpi_android.so => libs/armeabi/libwpi_android.so
[~/projects/wiringpi/android/example-wiringPi_c/jni]$ 
3. Import project * build it on the Android SDK.
