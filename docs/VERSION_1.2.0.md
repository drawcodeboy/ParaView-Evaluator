1. ȯ�溯��-User ������ PYTHONPATH �����, C:\Users\User\LLNL\VisIt3.4.2\lib\site-packages\visit �߰�
2. ȯ�溯��-�ý��� ������ Path���� Python 3.9���� ��� �߰�
3. VSCode���� PYTHONPATH, Path�� ���� �� �ϰ� ���� -> �̰� �ϴ� Windows ��ü CMD ����.
* * *
<code>visit_commands.py</code>�� ��� �����ص�
visit -cli�� ���� �����ؼ� ��ɾ� ������ ��
-nowin ���� ���̿� ���� �ð� �ٸ����� �����Ѵ�.
```
# Should modify config.json 'vis', 'Interact' or 'Screenshot'
visit -cli -s main_visit.py # no Screenshots
visit -cli -s -nowin main_visit.py # Screenshots
```