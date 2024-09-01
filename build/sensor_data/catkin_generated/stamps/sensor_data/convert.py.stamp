#!/usr/bin/env python3

import rospy
import tf
from sensor_msgs.msg import Imu
from std_msgs.msg import Float64MultiArray

def call_back(data: Imu):
    roll, pitch, yaw =  tf.transformations.euler_from_quaternion((
        data.orientation.x,
        data.orientation.y,
        data.orientation.z,
        data.orientation.w
    ))
    rospy.loginfo(f" \nConverted Values:  \nRoll: {roll}, Pitch: {pitch}, Yaw: {yaw}")
    angles = (roll, pitch, yaw)

def talker():
    angles = ()
    pub = rospy.Publisher('imu_angles', Float64MultiArray, queue_size=10)
    rospy.init_node("imu_publisher")
   # freq = rospy.Rate(1) # 1 Hz
   # while not rospy.is_shutdown():
   #     call_back(data: Imu)
   #     freq.sleep()

    rospy.init_node("converter")
    rospy.Subscriber("/imu",Imu,call_back)
    pub.publish(angles)
    rospy.loginfo(f"Published: {angles}")
    rospy.spin()

if __name__ == '__main__':
    try:
        talker()
    except rospy.ROSInterruptException:
        pass