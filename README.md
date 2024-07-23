<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
<h1>Control Touchscreen Button Plugin</h1>
<img src="https://github.com/Matjanikow/TouchScreenButtonControl/blob/master/addons/touchscreenbuttoncontrol/icon.svg" alt="Plugin Icon" style="width:100px;height:100px;">


<h2>Descripción</h2>
<p>Control Touchscreen Button Plugin es un requiere Godot 4. Proporciona un nodo de botón táctil identico al <a href="https://docs.godotengine.org/en/stable/classes/class_touchscreenbutton.html">TouchScreenButton2D</a> nativo de Godot, pero diseñado para trabajar en la jerarquía de nodos <code>Control</code> en vez de <code>Node2D</code>. Este nodo es ideal para interfaces de usuario y HUDs en juegos móviles.</p>

<h2>Características</h2>
<ul>
    <li>Implementa un botón táctil como nodo <code>Control</code>.</li>
    <li>Soporte completo para eventos táctiles.</li>
    <li>Fácil integración con el sistema de UI de Godot.</li>
</ul>

<h2>Instalación</h2>
<ol>
    <li>Descarga o clona este repositorio en tu proyecto de Godot.</li>
    <li>Copia la carpeta <code>addons//touchscreenbuttoncontrol</code> a la carpeta <code>addons</code> de tu proyecto.</li>
    <li>Abre tu proyecto en Godot.</li>
    <li>Ve a <code>Project -> Project Settings -> Plugins</code>.</li>
    <li>Activa el plugin <code>TouchScreenButtonControl</code>.</li>
</ol>

<h2>Uso</h2>
<ol>
    <li>En el editor de Godot, agrega un nuevo nodo <code>TouchScreenButtonControl</code> a tu escena.</li>
    <li>Configura las propiedades del nodo según tus necesidades.</li>
</ol>

<h2>Conflictos y Agradecimientos</h2>
<p>La base de mi trabajo fue basado en codigo del canal de youtube <a href="https://github.com/Mustache-Games/Godot-Interactive-Touchscreen-Button/tree/main">Mustache Games</a>. Esa fue mi punto de partida para crear y extender esta idea en un plugin.</p>

  ```gdscript
  func press():
  	var event = InputEventAction.new()
  	event.action = input_action
  	event.pressed = true
  	Input.parse_input_event(event)
  	released = false
  ```
<p>Luego encontré que esta solución no funcionaba, ya que los observers que manejan<code>Input.get_vector</code> no manejan este tipo de input</p>
<p>Agradezco finalmente a <a href="https://x.com/okarinargento">facundo tkaczyk</a> para ayudarme a conseguir este approach final </p>

 ```gdscript
func press():
	var input_event : InputEvent = InputMap.action_get_events(input_action)[0]
	input_event.pressed = true
	Input.parse_input_event(input_event)
	released = false
  ```

<h2>Autor</h2>
<p><a href="https://matata.work/">Matata.exe</a> </p>

</body>
</html>
