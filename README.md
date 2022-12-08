# mapviz-custom

## mapviz/mapviz/launch/mapviz.launch

initialize_origin.py는 GPS 좌표를 받아 WGS84 좌표계를 ROS TF트리에 연결하므로 <param name="local_xy_origin" value="auto"/>로 변환해주면 첫 수신한 GPS 값을 원점으로 사용한다.

<remap from="fix" to="your/gps/topic"/>을 추가하면 내가 사용하는 GPS 보드가 수신한 GPS값을 토대로 Mapviz를 사용할 수 있다.
---
