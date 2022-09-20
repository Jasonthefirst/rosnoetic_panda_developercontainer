FROM chillerrobot/ros-noetic-moveit-panda:first

RUN apt-get install -y --no-install-recommends ros-noetic-rospy-message-converter
RUN pip3 install future panda-robot

RUN echo "source ./catkin_ws/devel/setup.bash" >> ~/.bashrc