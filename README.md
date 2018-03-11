# FCND - 3D Motion Planning

This the _3D Motion Planning_ project for Udacity's Flying Car Nanodegree course.

Mark Anderson // Feb 2018 cohort

## Rubric items

### Explain the Starter Code

#### import

new
import argparse
import msgpack
from enum import auto
from planning_utils import a_star, heuristic, create_grid
from udacidrone.frame_utils import global_to_local

old
from udacidrone.connection import WebSocketConnection

#### States
use auto() to automatically uniquely enumerate states
add PLANNING state

#### init
rename all_waypoints to waypoints

#### local_position_callback
remove call to self.calculate_box before call to self.waypoint_transistion()
add print statement to print target, local
change references from self.all_waypoints to self.waypoints

#### velocity_callback
no differencece

####  state
deal with addition of PLANNING state
old
ARMING -{takeoff_transition}-> TAKEOFF
new
ARMING -{plan_path}-> PLANNING -{takeoff_transition}-> TAKEOFF

#### arming_transistion
move self.flight_state = States.ARMING from last thing executed to first thing excuted
move self.arm() before self.take_control()
remove call to self.set_home_position

#### takeoff_transition
move self.flight_state = States.TAKEOFF from last thing executed to first thing excuted
remove hardcoding of target altitude
assume self.target_position already set

####  waypoint_transition
move self.flight_state = States.WAYPOINT from last thing executed to first thing excuted
use heading parameter in self.cmd_position instead of hardcode to 0

#### landing_transition
move self.flight_state = States.LANDING from last thing executed to first thing excuted

#### disarming_transition
move self.flight_state = States.DISARMING from last thing executed to first thing excuted

#### manual_transition
move self.flight_state = States.MANUAL from last thing executed to first thing excuted

#### start
call self.connection.start() instead of super().start()

####  main
allow address and port to be specified by command line arguments
sleep(1) instead of sleep(2)

#### plan_path
new.  generates waypoints and send them to simulator with send_waypoints

##### send_waypoints
new.  called from plan_path. use msgpack.dumps to write waypoints as data to simulator


### Implementing Your Path Planning Algorithm

#### set_home_postion

#### determine your local position relative to global home

#### change start point for planning to current local position

#### add flexibility to the desired goal location

#### Write your search algorithm

#### Cull waypoints from the path

### Executing the flight

[//]: # (Mark Anderson // Feb 2018 cohort // 2018_03Mar_10)
