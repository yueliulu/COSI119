# How to Define Your Own Message Types?
author: Liulu Yue <br />
description: This FAQ documents specific instructions to define a new Message, as well as solutions to some issues you might encounter in your message defining process.

## How to create a new message type?
After created a ROS package, our package is constructed by a src folder, a CMakeLists.txt file, and a package.xml file. We need to create a msg folder to hold all of our new msg file. Then in your msg folder, create a new file <new_message>.msg, which contains fields you needed for this message type. <br />
For each fields in your msg file, define the name of the field and the type of the field (usually use std_msgs/<Type> or geometry_msgs/<Type>). <br \>
  For example, if you want your message to have a list of string and an integer, you msg file should look like:
  <pre><code>std_msgs/String[] list
std_msgs/Int16 int
  </code></pre>

## How to let the new message type recognized by ROS?
There are some modifications you need to make to CMakeLists.txt and package.xml in order to let the new message type recognized by ROS.
1. Make sure message_generation is in find_package().
2. Uncomment add_message_files() and add your .msg file name to add_message_files().
3. Uncomment generate_messages()
4. Modify catkin_package() to
<pre><code>
catkin_package(
  CATKIN_DEPENDS message_runtime
)
</code></pre>
5. Uncomment include in include_directories()
## How to use the newly created message type?


