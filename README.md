# PointCloudGridCutting

本项目主要用于点云切割，将点云切割成网格，然后对每个网格进行处理。

## 1. 环境配置（仅做参考）
~~~
python = 3.9
numpy = 1.22.4
open3d = 0.8.0
~~~

## 2. 参数说明
~~~
        This class is used to cut the point cloud into x_block * y_block blocks
        :param x_block: number of blocks in x direction
        :param y_block: number of blocks in y direction
        :param point_cloud: input point cloud
        :param output_path: output path (optional)
        :param output_file_type: output file type （default is ".ply"）
~~~
- `x_block` : 网格的x方向的个数
- `y_block` : 网格的y方向的个数
- `point_cloud` : 输入的点云
- `output_path` : 输出的路径(可选)
- `output_file_type` : 输出的文件类型（默认为".ply"）

## 3. 使用方法
~~~
from CloudPointGridCutting import CloudPointGridCutting
import open3d as o3d

if __name__ == '__main__':
    point_cloud = o3d.io.read_point_cloud("data/bunny.ply")
    x_block = 4
    y_block = 4
    cloud_point_grid_cutting = CloudPointGridCutting(x_block, y_block, point_cloud, 'output')
    blocks = cloud_point_grid_cutting.grid_cutting()
    cloud_point_grid_cutting.output_files()
~~~

将相对应的参数输入进去之后，调用`grid_cutting`方法，将点云切割成网格，然后调用`output_files`方法，将切割后的网格输出到指定的路径。

