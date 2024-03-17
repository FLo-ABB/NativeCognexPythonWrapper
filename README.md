# 📷 🐍 NativeCognexPythonWrapper 🐍 📷

WORK IN PROGRESS, see the [Status](#status-) section for more information.

NativeCognexPythonWrapper is a Python wrapper for the Cognex native mode commands. It provides a simple and intuitive wrapper to interact with Cognex cameras. It's based on the Cognex native mode commands, which can be found in [Cognex Documentation Website](https://support.cognex.com/docs/is_590/web/EN/ise/Content/Communications_Reference/LoadFile.htm?tocpath=Communications%20Reference%7CNative%20Mode%20Communications%7CBasic%20Native%20Mode%20Commands%7CFile%20%26%20Job%20Commands%7C_____1).

## Table of Contents 📜

- [📷 🐍 NativeCognexPythonWrapper 🐍 📷](#--nativecognexpythonwrapper--)
  - [Table of Contents 📜](#table-of-contents-)
  - [Installation 🚀](#installation-)
  - [Usage 📚](#usage-)
  - [Contributing 🤝](#contributing-)
  - [License 📝](#license-)
  - [Status 🚧](#status-)
    - [File \& Job Commands (13 commands)](#file--job-commands-13-commands)
    - [Image Commands (4 commands)](#image-commands-4-commands)
    - [Settings \& Cell Value Commands (11 commands)](#settings--cell-value-commands-11-commands)
    - [Execution \& Online Commands (6 commands)](#execution--online-commands-6-commands)
  - [Key Performance Indicators 🎯](#key-performance-indicators-)
    - [Progress](#progress)

## Installation 🚀

Download the repository and import the src folder into your project. The wrapper is divided into two main modules: `utils` and `commands`. The `utils` module contains the low-level functions to open and close a socket, and to log into the Cognex camera. The `commands` module contains the high-level functions to interact with the camera, such as loading a file, setting the camera online, and getting the current online status. Look over the `sandbox.py` file to see how to use the wrapper.

## Usage 📚

Example of how to use the wrapper:
```python
from pycognex import NativeInterface


def main():
    try:
        # Create a socket connection to the Cognex In-Sight vision system and log in
        native_interface = NativeInterface('192.168.103.2', 'admin', '')
        exectution_and_online = native_interface.exectution_and_online
        file_and_job = native_interface.file_and_job

        # Load the job if it is not already loaded
        if exectution_and_online.get_online() == 1:
            exectution_and_online.set_online(0)
        file_and_job.load_file("item1.job")
        exectution_and_online.set_online(1)

        # Set the system online to be able to trigg the camera and get results
        if exectution_and_online.get_online() == 0:
            exectution_and_online.set_online(1)

        # Close the socket connection
        native_interface.close()

    except Exception as e:
        print(f"Error: {e}")
```

## Contributing 🤝

If you'd like to contribute, please fork the repository and use a feature
branch. Pull requests are warmly welcome.

## License 📝

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Status 🚧

### File & Job Commands (13 commands)

| Command     | Implemented | Tested |
| ----------- | ----------- | ------ |
| Load File   | Yes         | No     |
| Store File  | Yes         | No     |
| Read File   | Yes         | No     |
| Write File  | Yes         | No     |
| Delete File | Yes         | No     |
| Get File    | Yes         | No     |
| Set Job     | Yes         | No     |
| Store Job   | Yes         | No     |
| Read Job    | Yes         | No     |
| Write Job   | Yes         | No     |
| Delete Job  | Yes         | No     |
| Get Job     | Yes         | No     |

### Image Commands (4 commands)

| Command     | Implemented | Tested |
| ----------- | ----------- | ------ |
| Read BMP    | Yes         | No     |
| Read Image  | Yes         | No     |
| Write BMP   | Yes         | No     |
| Write Image | Yes         | No     |

### Settings & Cell Value Commands (11 commands)

| Command             | Implemented | Tested |
| ------------------- | ----------- | ------ |
| Get Value           | No          | No     |
| Set Integer         | No          | No     |
| Set Float           | No          | No     |
| Set Region          | No          | No     |
| Set String          | No          | No     |
| Get Info            | No          | No     |
| Read Settings       | No          | No     |
| Write Settings      | No          | No     |
| Store Settings      | No          | No     |
| Set IP Address Lock | No          | No     |
| Get IP Address Lock | No          | No     |

### Execution & Online Commands (6 commands)

| Command            | Implemented | Tested |
| ------------------ | ----------- | ------ |
| Set Online         | Yes         | No     |
| Get Online         | Yes         | No     |
| Set Event          | Yes         | No     |
| Set Event and Wait | Yes         | No     |
| Reset System       | Yes         | No     |
| Send Message       | Yes         | No     |

## Key Performance Indicators 🎯

| Indicator                     | Count |
| ----------------------------- | ----- |
| Total of commands             | 34    |
| Total of implemented commands | 23    |
| Total of tested commands      | 0     |

### Progress 

🟦🟦🟦🟦🟦🟦🟦⬛⬛⬛ : Implementation

⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛  : Testing
