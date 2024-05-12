# Minecraft Launcher Script

This script allows you to launch Minecraft with the Fabric loader. It takes the Minecraft version and directory from the user and uses the `minecraft_launcher_lib` library to launch Minecraft with the Fabric loader. The script prompts the user for the Minecraft version and directory. It then generates a UUID and launches Minecraft with the Fabric loader using the `minecraft_launcher_lib` library.

## Usage

1. Run the script.
2. Enter the Minecraft version and directory when prompted.
3. The script will launch Minecraft with the Fabric loader.

## Dependencies

- `minecraft_launcher_lib` library

## Example

```python
import minecraft_launcher_lib as mll
from typing import Dict, List, Text
from uuid import uuid1
import subprocess

def launch_minecraft(
    minecraft_version: Text,
    minecraft_directory: Text,
    options: Dict[Text, Text]) -> None:
    """Launch Minecraft with the given version and options.

    Args:
        minecraft_version: The Minecraft version to launch.
        minecraft_directory: The directory to launch Minecraft from.
        options: A mapping of option names to option values.
    """
    minecraft_command = mll.command.get_minecraft_command(
        minecraft_version, minecraft_directory, options)
    subprocess.run(minecraft_command)

if __name__ == "__main__":
    # Prompt the user for the Minecraft version and directory
    mc_version = input("Version: ")
    minecraft_directory = input("Minecraft directory: ")

    # Set the Minecraft nickname and version
    minecraft_nickname = "TriaX"
    minecraft_version = f"fabric-loader-0.15.11-{mc_version}"

    # Generate a UUID and launch Minecraft with the Fabric loader
    options = {
        "uuid": str(uuid1()),
        "username": minecraft_nickname,
        "token": ''
    }
    launch_minecraft(minecraft_version, minecraft_directory, options)
