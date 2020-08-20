![Darknet Logo](http://pjreddie.com/media/files/darknet-black-small.png)

# Darknet #
Darknet is an open source neural network framework written in C and CUDA. It is fast, easy to install, and supports CPU and GPU computation.

For more information see the [Darknet project website](http://pjreddie.com/darknet).

For questions or issues please use the [Google Group](https://groups.google.com/forum/#!forum/darknet).

自分の備忘録としてのgoogle colab上での実行コードです.


colab上にディレクトリをコピーして本ディレクトリに入る

!make

!wget https://pjreddie.com/media/files/darknet53.conv.74

from google.colab import drive
drive.mount('/content/drive')

%%bash
chmod 777 darknet
./darknet detector \
        train \
        cfg/whill.data \
        cfg/whill-frozen.cfg \
        /content/drive/My\ Drive/darknet/darknet53.conv.74 > /content/log
        
%cp /content/drive/My\ Drive/darknet/backup/whill-* /content/drive/My\ Drive/darknet/results/

%cp /content/log /content/drive/My\ Drive/darknet/results/

%%bash
./darknet detector test cfg/whill.data cfg/whill.cfg /content/drive/My\ Drive/darknet/results/whill-frozen_final.weights /content/drive/My\ Drive/darknet/data/whill/medi00051.jpg
