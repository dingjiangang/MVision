# 点云识别
## 基于对应分组的三维物体识别

        基于pcl_recognition模块的三维物体识别。
        具体来说，它解释了如何使用对应分组算法，
        以便将3D描述符匹配阶段之后获得的一组点到点对应集集合到当前场景中的模型实例中。
        每个集群，代表一个可能的场景中的模型实例，
        对应的分组算法输出的
        变换矩阵识别当前的场景中，
        模型的六自由度位姿估计 6DOF pose estimation 。
        【5】计算法线向量  近邻邻域内 协方差矩阵PCA 降维到二维平面 计算法线向量
           PCA降维原理 http://blog.codinglabs.org/articles/pca-tutorial.html
           前面说的是二维降到一维时的情况，假如我们有一堆散乱的三维点云,则可以这样计算法线：
           1）对每一个点，取临近点，比如取最临近的50个点，当然会用到K-D树
           2）对临近点做PCA降维，把它降到二维平面上,可以想象得到这个平面一定是它的切平面(在切平面上才可以尽可能分散）
           3）切平面的法线就是该点的法线了，而这样的法线有两个，取哪个还需要考虑临近点的凸包方向
        【6】下采样滤波使用均匀采样（可以试试体素格子下采样）得到关键点
        【7】为keypoints关键点计算SHOT描述子
        【8】按存储方法KDTree匹配两个点云（描述子向量匹配）点云分组得到匹配的组 描述 点对匹配关系
        【9】参考帧霍夫聚类/集合一致性聚类得到 匹配点云cluster  平移矩阵和 匹配点对关系
        【10】分组显示 平移矩阵 T 将模型点云按T变换后显示 以及显示 点对之间的连线
##
