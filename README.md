# carDetection

kitti数据集下载：http://dataset.f3322.net:666/share/kitti/

kitti数据集转yolov3格式：https://blog.csdn.net/qq583083658/article/details/86321987
https://blog.csdn.net/duanyajun987/article/details/83309474

https://www.cnblogs.com/xieqi/p/9818056.html

https://www.cnblogs.com/xieqi/p/9818056.html





计算mAP：
python2 reval_voc.py --voc_dir VOCdevkit --year 2007 --image_set test --classes data/kitti.names output


https://www.aiuai.cn/aifarm837.html


模型剪枝：
python sparsity_train.py --image_folder data/kitti.data --cfg cfg/prune_yolov3-kitti.cfg --weights backup/prune_yolov3-kitti_30000.weights



python new_prune.py --cfg cfg/yolov3-kitti.cfg --weights backup/yolov3-kitti_30000.weights
