# VERSION 1.1.0
## Contributions
1. Python Shell �� �ᵵ �Ǵ� ����� ã�Ƴ�. ���ʿ� <code>pvpython</code> ���������� ParaView ��ġ�� �� �����ϰ� �־��� (<code>pvbatch</code>�� ��������)
    * �� �ܼ��� ���ȭ ����
    * �׷��� Python ���� ���̺귯���� ��� �Ұ���, �õ��Ϸ��� <a href="https://discourse.paraview.org/t/how-can-i-install-and-import-other-modules-inside-pvpython/3067">���� ��ü�� ���Ӱ� �ϸ鼭 �߰��ؾ� �Ѵ�</a>�� ���� �־���.
2. ParaView ���� trace ����� Ȱ���� �ڵ� �� ���� �ð� ��ȭ

## Install
```
1. ParaView ��ġ

2. ȯ�� ���� ���� <code>C:\Program Files\ParaView 5.13.1\bin</code> -> <code>pvpython</code>

3. git clone --branch v1.1.0 https://github.com/drawcodeboy/ParaView-Evaluator.git ��ɾ� ����

4. config.json ���� ������ ���, �ó����� ����

5. pvpython main.py <--scenario> <--scenario-subtype> ��ɾ� ����
```
## Set <code>config.json</code>
```
Scenario
0 = Draw Data
1 = Draw Vector Field
2 = Draw ISO Contour
3 = Draw Stream Line
    3.1 = Stream Tracer
    3.2 = Stream Tracer -> Tube
    3.3 = Stream Tracer -> Glyph
4 = Draw Clip
5 = Draw Slice
6 = Perform Data Scenario
    6.1 = Data Extraction
    6.2 = Data Time Plot (Data Extraction -> Plot Selection Over Time)
    6.3 = Data Time Plot (Plot Over Line)

N.M (N = --scenario, M = --scenario-subtype)
```