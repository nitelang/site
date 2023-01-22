+++
title = "Nite Lang"
[data]
baseChartOn = 3
colors = ["#627c62", "#11819b", "#ef7f1a", "#4e1154"]
columnTitles = ["Section", "Status", "Author"]
fileLink = "content/projects.csv"
title = "Projects"

+++
<center>
{{< tip "warning" >}}
We're still in in the planning stage; Things may and are even likely to change! It's all psuedo-code atm after all.
Feel free to open a [PR](https://github.com/nitelang/nite/pulls), raise an [issue](https://github.com/nitelang/rfcs/issues/new/choose "Open a Github Issue")(s) or request new feature(s). {{< /tip >}}
</center>

{{< block "grid-2" >}}
{{< column >}}

# A **Light**er Lua.
#### Lua is a beautiful language, with a dirty mouth.
## Our goal is to clean it up -- even if it takes all Nite.
By providing a more modern, succinct, and 'tasteful' syntax; That's 'cleanly transpiled'.
As-in the IR it generates is effectively just regular old Lua. The goal is to maximize
readibility, while maintaining as-much compatiblity as-possible. We want to be a 
"better Lua" but we still, decisively want to be Lua.

In the immediate though, the focus is on shrinking the surface syntax. There's a lot of 
[easy gains]() to be made here -- to catch up with contemporary scripting-languages 
(goodbye, local and/or function keywords). There's also some more lofty / optimistic 
ideas like automatic `end` resolution (where we can effectively emulate at-option 
signficant identation), call & assignment blocks (through the new "feed" `,,` and `;;` 
"me" operators), which become a lot more important since we scope 'explicit by default',
and a few more ideas I'm not confident-enough in them to share yet. lol

Outside of "just syntax". we plan to at least experiment with some features that would
effectively make Nite a superset of Lua. These are always optional, and often try to build 
off ideas already present in the ecosystem. At minimum the goal would be gradual-typing,
but some stuff like deeper metaprogramming x DSL creation are on the table (yes, pun intended).
And we effectively want to provide a full extended standard & vendor library via [mid](https://github.com/nitelang/mid).

**Nite In A Few Points:**
- Works as a drop-in replacement for Lua.
- Has notably shorter keywords than Lua.
- Rejiggers a few keywords when it makes sense.
- Adds custom operators to cut down on noise.
- Isn't global-by-default, but explicit-by-default.
- Intends to implement opt-in significant identation.
- Intends to have a first-class HCR & REPL experience.
- Intends to offer deep syntax-extension / DSL creation.
- Intends to at-least mess around with deeper metaprogramming.
- Intends to provide optional type hinting and/or optional pragmas.
- Intends to have some kind of standard system for  namespacing.
- Intends to provide first-class editor support for Lite & VSCode.
- (For The Most-Part) Transpiles into regular old Lua.
- Runs wherever a standard compliant Lua implementation does.
- Supports Lua 5.1 And Beyond.

{{< button "/docs/getting-started/" "Getting Started" >}}{{< button "https://github.com/nitelang/nite/releases" "Latest Release" >}}
{{< /column >}}

{{< column >}}


<center>
{{< tip >}}
Nite is imagining a brighter, lighter, and more cohessive future for the Lua ecosystem.
{{< /tip >}}
</center>


![diy](/images/bulb.jpg)

<center>

```
Star Light, Star Bright,
First Star I See Tonight,
I Wish I May, I Wish I Might,
Have This Wish I Wish Tonight.
```
</center>


```nite
#!/usr/bin/env nite
spc nite.examples.moongl.hello_window

use moongl as gl
 ,, moonglfw as glfw

|| settings
var SCR_WIDTH, SCR_HEIGHT = 800, 600

|| process all input: query GLFW whether relevant keys are pressed/released
|| this frame and react accordingly
ful process_input(window)
   if glfw.get_key(window, 'escape') == 'press' then
       glfw.set_window_should_close(window, true)
 fin

|| glfw: whenever the window size changed (by OS or user resize) this callback function executes
ful framebuffer_size_callback(window, width, height)
    || make sure the viewport matches the new window dimensions; note that width and 
    || height will be significantly larger than specified on retina displays.
    gl.viewport(0, 0, width, height)
end

|| glfw: initialize and configure
glfw ;;
 ,, window_hint('context version major', 3)
 ,, window_hint('context version minor', 3)
 ,, window_hint('opengl profile', 'core')

|| glfw window creation
var window = glfw.create_window(SCR_WIDTH, SCR_HEIGHT, "LearnOpenGL")
glfw.make_context_current(window)
gl.init() || this loads all OpenGL function pointers
glfw.set_framebuffer_size_callback(window, framebuffer_size_callback)

|| render loop
while not glfw.window_should_close(window) do
   || input
   process_input(window)
   || swap buffers and poll IO events (keys pressed/released, mouse moved etc.)
   glfw ;;
    ,, swap_buffers(window)
    ,, glfw.poll_events()
end
```

This Example Was Adapted; [See Original Source](https://github.com/stetre/moongl/blob/master/examples/learnopengl/1.getting_started/1.1.hello_window.lua).

{{< /column >}}
{{< /block >}}
