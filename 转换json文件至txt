import json

json_data = r"C:\Users\Administrator.X36KKQ2UTQSEZ5O\Desktop\json\instances_val2017.json"

with open(json_data) as f:
    info = json.load(f)

def find_lable(file_id,file_width,file_heigth):
    bbox_list = []
    path = "C:\\Users\\Administrator.X36KKQ2UTQSEZ5O\\Desktop\\res\\"
    for k,v in info.items():
        if k == 'annotations':
            for file in v:
                if file_id == file['image_id']:
                    xmin = round(file['bbox'][0], 2)
                    xmax = round(file['bbox'][0]+file['bbox'][2], 2)
                    ymin = round(file['bbox'][1], 2)
                    ymax = round(file['bbox'][1]+file['bbox'][3], 2)
                    proportion_xmin = str(round(xmin/file_width,2))
                    proportion_xmax = str(round(xmax/file_width,2))
                    proportion_ymin = str(round(ymin/file_heigth,2))
                    proportion_ymax = str(round(ymax/file_heigth,2))
                    ls = str(file['category_id'])+' '+proportion_xmin+' '+proportion_ymin+' '+proportion_xmax+' '+proportion_ymax
                    print(ls)
                    bbox_list.append(ls)
                    txt = open(path + str(file_id) + '.txt', 'a')
                    txt.write(ls + '\n')
                    txt.close()
    return bbox_list

def save_to_txt():
    txt = open("C:\\Users\\Administrator.X36KKQ2UTQSEZ5O\\Desktop\\res\\bbox-empty.txt", 'a')
    for k,v in info.items():
        if k == 'images':
            for file in v:
                box = find_lable(file['id'],file['width'],file['height'])
                file_name = file['file_name']
                bbox = str(box)
                if len(bbox) == 2:
                    txt.write('file_name:'+file_name+'\n')
    txt.close()

if __name__ == '__main__':
    save_to_txt()



