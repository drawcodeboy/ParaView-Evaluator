
## ParaView Evaluator
```
1. ParaView ��ġ
2. ȯ�� ���� ���� <code>C:\Program Files\ParaView 5.13.1\bin</code> -> <code>pvpython</code>
3. config.json ���� ������ ���, �ó����� ����
    ������ ��� �����ڴ� ������ '/'�� �Ǿ��־�� ��.
4. pvpython main.py ��ɾ� ����
```
## VisIT Evaluator
1. ȯ�溯��-User ������ PYTHONPATH �����, C:\Users\User\LLNL\VisIt3.4.2\lib\site-packages\visit �߰�
2. ȯ�溯��-�ý��� ������ Path���� Python 3.9���� ��� �߰�
```
# Move path where exists main_visit.py
# Should modify config.json 'vis', 'Interact' or 'Screenshot'
config.json ���� ������ ���, �ó����� ����
    ������ ��� �����ڴ� ������ '/'�� �Ǿ��־�� ��.
visit -cli -s main_visit.py # no Screenshots
visit -cli -s -nowin main_visit.py # Screenshots
```