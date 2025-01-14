# ParaView Evaluator using PvPython
* <b>Latest: v1.1.0</b>
    * <a href="docs/VERSION_1.1.0.md">v1.1.0 Documentation</a>
    * <a href="docs/VERSION_1.0.0.md">v1.0.0 Documentation</a>
## functions
```
# ������ ��������, �ð��� �� ���� ����
OpenFOAMReader(registrationName="������ �̸�(Pipeline Browser����)",
               FileName="������ ���� ��ġ ���")

# get animation scene, ���� �ľ� �� ��
animationScene1 = GetAnimationScene()

# update animation scene based on data timesteps, ���� �ľ� �� ��
animationScene1.UpdateAnimationUsingDataTimeSteps() 

# Layout#1 �ϳ� ����, â ���� �Ŷ� ���� ��
renderView1 = GetActiveViewOrCreate('RenderView')

# ���Ⱑ ������ ȭ�鿡 ���� �κ� (�������ϴ� �κ�)
runfoamDisplay = Show(data, renderView1, 'UnstructuredGridRepresentation')

# ȭ�� ǥ���� ��� �ϰڴٴ� �ǹ��� ��
runfoamDisplay.Representation = 'Surface'

# �ľ� �� ��
renderView1.ResetCamera(False, 0.9)

# ���⼭ ȭ�� ǥ�� ������ �ߴ� �κ��� ����Ǵ� ��
runfoamDisplay.SetScalarBarVisibility(renderView1, True) # ���⼭ ���� �ȴ�.

# Render View�� ������ ���⼭ ������Ʈ�Ǵ� �� �ϴ�.
renderView1.Update()

## �ľ� �� ��
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

# get layout
layout1 = GetLayout()

#--------------------------------
# saving layout sizes for layouts

# layout/tab size in pixels
layout1.SetSize(1816, 869)

#-----------------------------------
# saving camera placements for views

# current camera placement for renderView1
renderView1.CameraPosition = [0.08451644302948183, -0.21068666041447617, -0.11248287853191463]
renderView1.CameraFocalPoint = [0.06283199787139893, 0.009999999776482582, 0.02094399929046631]
renderView1.CameraViewUp = [0.05780590149651594, -0.5123557263579088, 0.8568255875150057]
renderView1.CameraParallelScale = 0.06698142323301427

# ȭ�� ���� ��
Interact()
```