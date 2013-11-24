# motion-cgrect-bug

Example app demonstrating 'uninitialized constant CGRect (NameError)' with Webkit framework included.

## Results with RubyMotion 2.16

The app compiles and runs fine without ```app.frameworks += ['Webkit']```. 
With the framework included I'm seeing this problem:

```
$ rake
     Build ./build/MacOSX-10.9-Development
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/calculations.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/handler.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/constraint.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/core_extensions/ca_layer.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/core_extensions/view_getters.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/stylesheet_extensions/transform.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/teacup_view.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/style.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/layout.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/merge_defaults.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/stylesheet.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/restyle.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/stylesheet_extensions/constraints.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/teacup_controller.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/teacup_util.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup/version.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/core_extensions/ns_view.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/core_extensions/ns_view_controller.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/core_extensions/ns_window_controller.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/core_extensions/ns_window.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/core_extensions/teacup_handlers.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/dummy.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/style_extensions/autoresize.rb
   Compile /Users/jonasbruunnielsen/.rvm/gems/ruby-1.9.3-p385/bundler/gems/teacup-9134f78f3f2d/lib/teacup-osx/handler.rb
   Compile ./app/menu.rb
   Compile ./app/app_delegate.rb
    Create ./build/MacOSX-10.9-Development/motion-nsrect-test.app/Contents
    Create ./build/MacOSX-10.9-Development/motion-nsrect-test.app/Contents/MacOS
      Link ./build/MacOSX-10.9-Development/motion-nsrect-test.app/Contents/MacOS/motion-nsrect-test
    Create ./build/MacOSX-10.9-Development/motion-nsrect-test.app/Contents/PkgInfo
    Create ./build/MacOSX-10.9-Development/motion-nsrect-test.app/Contents/Info.plist
      Copy ./resources/Credits.rtf
    Create ./build/MacOSX-10.9-Development/motion-nsrect-test.dSYM
       Run ./build/MacOSX-10.9-Development/motion-nsrect-test.app/Contents/MacOS/motion-nsrect-test
2013-11-24 21:02:49.662 motion-nsrect-test[47278:303] uninitialized constant CGRect (NameError)
2013-11-24 21:02:49.664 motion-nsrect-test[47278:303] *** Terminating app due to uncaught exception 'NameError', reason: 'uninitialized constant CGRect (NameError)
'
*** First throw call stack:
(
	0   CoreFoundation                      0x00007fff8ffe841c __exceptionPreprocess + 172
	1   libobjc.A.dylib                     0x00007fff8c31ee75 objc_exception_throw + 43
	2   motion-nsrect-test                  0x0000000100e4dcde _ZL10__vm_raisev + 334
	3   motion-nsrect-test                  0x0000000100e4dd84 rb_vm_raise + 148
	4   motion-nsrect-test                  0x0000000100d7ce59 rb_exc_raise + 9
	5   motion-nsrect-test                  0x0000000100d79bf4 rb_name_error + 228
	6   motion-nsrect-test                  0x0000000100e03d17 rb_mod_const_missing + 87
	7   motion-nsrect-test                  0x0000000100e21941 rb_vm_dispatch + 4929
	8   motion-nsrect-test                  0x0000000100e04924 rb_const_get_0 + 948
	9   motion-nsrect-test                  0x0000000100d3d3f3 vm_get_const + 259
	10  motion-nsrect-test                  0x0000000100d44148 rb_scope + 168
	11  motion-nsrect-test                  0x0000000100d45405 MREP_EF4256714B684ECBAC537EE22E054DA3 + 2549
	12  motion-nsrect-test                  0x0000000100c239a7 RubyMotionInit + 599
	13  motion-nsrect-test                  0x0000000100c23a1f main + 79
	14  libdyld.dylib                       0x00007fff9137d5fd start + 1
	15  ???                                 0x0000000000000001 0x0 + 1
)
libc++abi.dylib: terminating with uncaught exception of type NameError
((null))> 
================================================================================
The application terminated. A crash report file may have been generated by the
system, use `rake crashlog' to open it. Use `rake debug=1' to restart the app
in the debugger.
================================================================================
```
