# mapviz-custom

## mapviz/mapviz/launch/mapviz.launch

initialize_origin.py는 GPS 좌표를 받아 WGS84 좌표계를 ROS TF트리에 연결하므로 <param name="local_xy_origin" value="auto"/>로 변환해주면 첫 수신한 GPS 값을 원점으로 사용한다.

<remap from="fix" to="your/gps/topic"/>을 추가하면 내가 사용하는 GPS 보드가 수신한 GPS값을 토대로 Mapviz를 사용할 수 있다.

---
<launch>

  <node pkg="mapviz" type="mapviz" name="mapviz"></node>

  <node pkg="swri_transform_util" type="initialize_origin.py" name="initialize_origin" >
    <param name="local_xy_frame" value="/map"/>
    <param name="local_xy_origin" value="swri"/>
    <rosparam param="local_xy_origins">
      [{ name: swri,
         latitude: 29.45196669,
         longitude: -98.61370577,
         altitude: 233.719,
         heading: 0.0},
         
       { name: back_40,
         latitude: 29.447507,
         longitude: -98.629367,
         altitude: 200.0,
         heading: 0.0}]
    </rosparam>
  </node>

  <node pkg="tf" type="static_transform_publisher" name="swri_transform" args="0 0 0 0 0 0 /map /origin 100"  />

</launch>

---
