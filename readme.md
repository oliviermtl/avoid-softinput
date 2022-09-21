# Minimal reproduction for failed android build w/ compileSdkVersion=33 and react-native-avoid-softinput

run ` yarn android`

if compileSdkVersion = 33 it does not build
if compileSdkVersion = 31 it builds properly

## Error messages

> Task :react-native-avoid-softinput:compileDebugKotlin FAILED
> Type mismatch: inferred type is Animator? but Animator was expected

## Fix

in android/src/main/java/com/reactnativeavoidsoftinput/AvoidSoftInputManager.kt
` override fun onAnimationEnd(animation: Animator?)`
has to be replaced by
` override fun onAnimationEnd(animation: Animator)`

### Testing the fix

`git checkout fix`
` yarn android`
