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

## Confirm Detailed Code
```
# trace generated using paraview version 5.13.1
#import paraview
#paraview.compatibility.major = 5
#paraview.compatibility.minor = 13

#### import the simple module from the paraview
from paraview.simple import *
#### disable automatic camera reset on 'Show'
paraview.simple._DisableFirstRenderCameraReset()

# create a new 'Open FOAM Reader'
runfoam = OpenFOAMReader(registrationName='run.foam', FileName='C:\\Users\\User\\Desktop\\Interships\\KDW\\ETRI_04\\data\\241003\\foam\\foam\\run.foam')

# get animation scene
animationScene1 = GetAnimationScene()

# update animation scene based on data timesteps
animationScene1.UpdateAnimationUsingDataTimeSteps()

# get active view
renderView1 = GetActiveViewOrCreate('RenderView')

# show data in view
runfoamDisplay = Show(runfoam, renderView1, 'UnstructuredGridRepresentation')

# trace defaults for the display properties.
runfoamDisplay.Representation = 'Surface'

# reset view to fit data
renderView1.ResetCamera(False, 0.9)

# get the material library
materialLibrary1 = GetMaterialLibrary()

# show color bar/color legend
runfoamDisplay.SetScalarBarVisibility(renderView1, True)

# update the view to ensure updated data information
renderView1.Update()

# get color transfer function/color map for 'p'
pLUT = GetColorTransferFunction('p')

# get opacity transfer function/opacity map for 'p'
pPWF = GetOpacityTransferFunction('p')

# get 2D transfer function for 'p'
pTF2D = GetTransferFunction2D('p')

# create a new 'Glyph'
glyph1 = Glyph(registrationName='Glyph1', Input=runfoam,
    GlyphType='Arrow')

# show data in view
glyph1Display = Show(glyph1, renderView1, 'GeometryRepresentation')

# trace defaults for the display properties.
glyph1Display.Representation = 'Surface'

# show color bar/color legend
glyph1Display.SetScalarBarVisibility(renderView1, True)

# update the view to ensure updated data information
renderView1.Update()

# hide data in view
Hide(runfoam, renderView1)

#================================================================
# addendum: following script captures some of the application
# state to faithfully reproduce the visualization during playback
#================================================================

# get layout
layout1 = GetLayout()

#--------------------------------
# saving layout sizes for layouts

# layout/tab size in pixels
layout1.SetSize(1816, 869)

#-----------------------------------
# saving camera placements for views

# current camera placement for renderView1
renderView1.CameraPosition = [0.06283199787139893, 0.009999999776482582, 0.27974034561993477]
renderView1.CameraFocalPoint = [0.06283199787139893, 0.009999999776482582, 0.02094399929046631]
renderView1.CameraParallelScale = 0.06698142323301427


##--------------------------------------------
## You may need to add some code at the end of this python script depending on your usage, eg:
#
## Render all views to see them appears
# RenderAllViews()
#
## Interact with the view, usefull when running from pvpython
# Interact()
#
## Save a screenshot of the active view
# SaveScreenshot("path/to/screenshot.png")
#
## Save a screenshot of a layout (multiple splitted view)
# SaveScreenshot("path/to/screenshot.png", GetLayout())
#
## Save all "Extractors" from the pipeline browser
# SaveExtracts()
#
## Save a animation of the current active view
# SaveAnimation()
#
## Please refer to the documentation of paraview.simple
## https://www.paraview.org/paraview-docs/latest/python/paraview.simple.html
##--------------------------------------------
```