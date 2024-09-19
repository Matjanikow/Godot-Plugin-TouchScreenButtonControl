<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
<h1>Godot Plugin: Control Touchscreen Button Plugin</h1>
<img src="https://github.com/Matjanikow/TouchScreenButtonControl/blob/master/addons/touchscreenbuttoncontrol/icon.svg" alt="Plugin Icon" style="width:100px;height:100px;">

<h2>Description</h2>
<p>Control Touchscreen Button Plugin requires Godot 4. It provides a touch button node identical to Godot's native <a href="https://docs.godotengine.org/en/stable/classes/class_touchscreenbutton.html">TouchScreenButton2D</a>, but designed to work within the <code>Control</code> node hierarchy instead of <code>Node2D</code>. This node is ideal for user interfaces and HUDs in mobile games.</p>

<h2>Features</h2>
<ul>
    <li>Implements a touch button as a <code>Control</code> node.</li>
    <li>Full support for touch events.</li>
    <li>Easy integration with Godot's UI system.</li>
</ul>

<h2>Installation</h2>
<ol>
    <li>Download or clone this repository into your Godot project.</li>
    <li>Copy the <code>addons/touchscreenbuttoncontrol</code> folder into your project's <code>addons</code> folder.</li>
    <li>Open your project in Godot.</li>
    <li>Go to <code>Project -> Project Settings -> Plugins</code>.</li>
    <li>Enable the <code>TouchScreenButtonControl</code> plugin.</li>
</ol>

<h2>Usage</h2>
<ol>
    <li>In the Godot editor, add a new <code>TouchScreenButtonControl</code> node to your scene.</li>
    <li>Configure the node's properties according to your needs.</li>
</ol>

<h2>Conflicts and Acknowledgments</h2>
<p>The basis of my work was derived from code by the YouTube channel <a href="https://www.youtube.com/@MustacheTutorials">Mustache Games</a>. This was my starting point to create and extend this idea into a plugin.</p>

  ```gdscript
  func press():
      var event = InputEventAction.new()
      event.action = input_action
      event.pressed = true
      Input.parse_input_event(event)
      released = false
```
<p>Later, I found that this solution did not work as the observers handling <code>Input.get_vector</code> do not manage this type of input.</p>
<p>Special thanks to <a href="https://x.com/okarinargento">Facundo Tkaczyk</a> for helping me achieve this final approach.</p>

```gdscript

func press():
    var input_event: InputEvent = InputMap.action_get_events(input_action)[0]
    input_event.pressed = true
    Input.parse_input_event(input_event)
    released = false
```
<h2>Author</h2>
<p><a href="https://matata.work/">Matata.exe</a></p>
</body>
</html>
