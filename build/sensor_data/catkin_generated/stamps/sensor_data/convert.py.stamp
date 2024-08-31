#!/usr/bin/env python3

import rospy
import tf
from sensor_msgs.msg import Imu



def call_back(data: Imu):
    roll, pitch, yaw =  tf.transformations.euler_from_quaternion((
        data.orientation.x,
        data.orientation.y,
        data.orientation.z,
        data.orientation.w
    ))
    rospy.loginfo("Converted Values: \nRoll: %.2f, Pitch: %.2f, Yaw: %.2f" % (roll, pitch, yaw))

def subscribe():
    rospy.init_node("converter")
    rospy.Subscriber("/imu",Imu,call_back)
    rospy.spin()

if __name__ == "__main__":
    subscribe()