import os
from concurrent.futures import ProcessPoolExecutor
import cv2
import datetime,time

a_time = datetime.datetime.now() + datetime.timedelta(minutes=240)  # 设定时间
addr = ['http://hzrtmp03.ys7.com:9088/livestream/501436305_1_1_1_0.flv',
        'http://hzrtmp01.ys7.com:9088/livestream/487288088_1_1_1_0.flv',
        'http://hzrtmp01.ys7.com:9088/livestream/753518135_1_1_1_0.flv',
        'http://hzrtmp03.ys7.com:9088/livestream/501436516_1_2_1_0.flv']    # 视频流连接
name_list = ['a1','b1','c1','d1']  # 文件名
# lengths_list = [768,768,1280,1280]   # 视频分辨率：宽
# withes_list= [432,432,720,720]  # 视频分辨率：高
count = 1   # 连接失败次数
num = 1   # 第几个文件
res = True  # 连接状态
clock = True    # 时间状态

# 录制视频
def record(rtsp_url,name):
    global clock,count,num,file_name
    cap = cv2.VideoCapture(rtsp_url)
    print(cap.isOpened(),':' + name,str(datetime.datetime.now()))   # 检查连接状态并打印
    size = (int(cap.get(cv2.CAP_PROP_FRAME_WIDTH)), int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT)))
    fourcc = -1   # 视频编码
    out_path = r'D:\%s.avi'%name
    # fourcc = cv2.VideoWriter_fourcc(*'XVID')   # 视频编码
    # out_path = r'D:\%s.avi'%name
    # fourcc = cv2.VideoWriter_fourcc(*'AVC1')   # 视频编码
    # out_path = r'D:\%s.mp4'%name
    out = cv2.VideoWriter(out_path, fourcc, 20, size)
    while True:
        ret, frame = cap.read()
        if ret == True:
            out.write(frame)    # 写入视频帧
            if datetime.datetime.now() > a_time:
                print(name,':Time is up!!!!!!!!!')
                clock = False
                break
        else:
            if datetime.datetime.now() > a_time:
                print(name,':Time is up!!!!!!!!!')
                clock = False
                break
            print('False:'+ name)
            num = num+1
            count = count + 1
            file_name = name[:1] + str(num)
            break
    cap.release()
    out.release()
    cv2.destroyAllWindows()
    res = False
    return clock,count,res,file_name

# 检查录制状态
def check(rtsp_url,name):
    global res
    info = record(rtsp_url,name)
    while True:
        if info[0] == False:    # 计时结束
            break
        elif info[1] > 10:  # 超出连接次数
            print('Over count limit!!!')
            break
        elif info[2] == False:  # 连接失败
            res = True  # 重置连接状态
            print('Reopen:' + info[3])
            info = record(rtsp_url, info[3])
            time.sleep(5)

if __name__ == '__main__':
    ProcessPoolExecutor(os.cpu_count()).map(check,addr,name_list)
