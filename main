import json
import os

personnel_info = {}


def load():
    _store_file = open('store.json', 'r')
    data = _store_file.read()
    if data == '':
        data = '''{
            "data": []
        }'''
        print('还没有数据哦！')
    else:
        data1 = json.loads(data);
        row = data1['data']
        if len(row) == 0:
            print('还没有数据哦！')
        for i,person in enumerate(row):
            if i == 0:
                s = 'identifier\t'
                for k, v in person.items():
                    s += k + '\t'
                print(s)
            s1 = str(i) + '\t\t'
            for k, v in person.items():
                s1 += v + '\t'
            print(s1)
    global personnel_info
    personnel_info = json.loads(str(data))
    _store_file.close()

    
def save():
    global personnel_info
    data = json.dumps(personnel_info)
    _store_file = open('store.json', 'w')
    _store_file.write(data)
    _store_file.close()

    
def edit():
    name = input('input name to edit')
    global personnel_info
    for person in personnel_info['data']:
        if person['name'] == name:
            personnel_info['data'].remove(person)
            name = input('input name: ')
            age = input('input age: ')
            height = input('input height: ')
            weight = input('input weight: ')
            tel = input('input Telephone: ')
            person = {
                'name': name,
                'age': age,
                'height': height,
                'weight': weight,
                'tel': tel,
            }
            personnel_info['data'].append(person)
            return
    print("can't find person with name %s" % name)

    
def add():
    name = input('input name: ')
    age = input('input age: ')
    height = input('input height: ')
    weight = input('input weight: ')
    tel = input('input Telephone: ')
    person = {
        'name': name,
        'age': age,
        'height': height,
        'weight': weight,
        'tel': tel,
    }
    global personnel_info
    personnel_info['data'].append(person)

    
def delete():
    name = input("input name to delete: ")
    global personnel_info
    for person in personnel_info["data"]:
        if person['name'] == name:
            personnel_info['data'].remove(person)
            return
    print("can't find person with name %s", name)


def find():
    name = input('input name to find: ')
    for person in personnel_info['data']:
        if person['name'] == name:
            s = '\t'
            for k, v in person.items():
                s += k + '\t'
            print(s)
            s1 = str('') + '\t'
            for k, v in person.items():
                s1 += v + '\t'
            print(s1)
            return
    print("can't find name: %s" % name)

    
def help():
    print("command: add | print | find | exit |save |delete")

    
def print_info():
    global personnel_info
    data = json.dumps(personnel_info, indent=4)
    print(data)

    
if __name__ == '__main__':
    load()
    help()
    while True:
        command = input('input command: ')
        if command == 'help':
            print("command: add | print | find | exit |save |delete")
        elif command == 'add':
            add()
        elif command == 'print':
            print_info()
        elif command == 'find':
            find()
        elif command == 'save':
            save()
        elif command == 'delete':
            delete()
        elif command == 'edit':
            edit()
        elif command == 'exit':
            save()
            break
        else:
            print('unkown command %s' % command)
            help()
