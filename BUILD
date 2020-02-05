load("//engine/build:isaac.bzl", "isaac_app")

isaac_app(
    name = "joystick",
    app_json_file = "joystick.app.json",
    data = [
        "joystick.config.json",
        "joystick.graph.json",
        "raspimouse.config.json",
        "raspimouse.graph.json",
    ],
    modules = [
        "navigation",
        "flatsim",
        "planner",
        "viewers",
        "sensors:joystick",
    ],
)
