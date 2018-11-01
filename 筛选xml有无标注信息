import os,shutil
import xml.etree.cElementTree as et
path = input('Path:')

def find_no_person_xml():
    domain = os.path.abspath(path)
    for xml in os.listdir(path):
        xml_path = os.path.join(domain, xml)
        tree=et.parse(xml_path)
        root=tree.getroot()
        object=root.findall('object')
        if len(object) == 0 :
            print("无标注信息")
        else:
            print("有标注信息")
            for property in object:
                name = property.find('name').text
                print('对象名:'+name)

def copy_no_person_xml():
    domain = os.path.abspath(path)
    new_domain = domain[:-3]
    new_dir = os.mkdir(os.path.join(new_domain, 'no_person_xml'))
    for xml in os.listdir(path):
        xml_path = os.path.join(domain, xml)
        tree=et.parse(xml_path)
        root=tree.getroot()
        object=root.findall('object')
        if len(object) == 0 :
            source_xml_path = xml_path
            source_xml_name = source_xml_path[len(path):-4]
            target_xml_path = new_domain + '\\no_person_xml\\' + source_xml_name + '.xml'
            shutil.copy(source_xml_path, target_xml_path)
            print("已拷贝未标注的xml文件")

def copy_no_person_img():
    domain = os.path.abspath(path)
    new_domain = domain[:-3]
    new_dir = os.mkdir(os.path.join(new_domain, 'no_person_img'))
    for xml in os.listdir(path):
        xml_path = os.path.join(domain, xml)
        tree = et.parse(xml_path)
        root = tree.getroot()
        object = root.findall('object')
        if len(object) == 0:
            source_xml_name = xml_path[len(path):-4]
            source_img_name = source_xml_name
            source_img_path = path[:-4]+'pic\\'+ source_img_name + '.jpg'
            target_img_path = new_domain + '\\no_person_img\\' + source_img_name + '.jpg'
            shutil.copy(source_img_path, target_img_path)
            print("已拷贝未标注的img文件")

find_no_person_xml()
copy_no_person_xml()
copy_no_person_img()
