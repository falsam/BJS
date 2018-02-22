![](http://falsam.com/sbbjs/wiki/lib/exe/fetch.php?media=logo.png)

Writing in progress ....


**■ Engine**
* SetEnginePath(EnginePath.s = "sbbjs")
* InitEngine(Callback, CanvasOutput = #PB_Ignore)  
* RenderLoop(Callback)  
* RenderWorld() 
* CreateSceneShoot(Camera, Width, Height, Precision.f=1) 
* ShowAxis(size)
  
**■ Scene**
* Value = CreateScene()  
* Value = SceneWidth()
* Value = SceneHeight()
* SceneGravity(x.f = 0, y.f = -0.9, z.f = 0)   
* ClearScene(color)  
* onMouseMove(CallBack)
* Value = SceneMouseX(Scene)
* Value = SceneMouseY(Scene) 
* BeforeRender(CallBack)
* SetCurrentScene(Scene, Camera)  
* ImportScene(Name.s, Path.s, FileName.s, Callback)  
* ExportScene(Scene, FileName.s)
* SceneDebug()  
   
**■ Environment**
* AmbientColor(Color.i)
* SkyBox(name.s, sky.s, size.i = 200)  
* Fog(Color, Intensity.f = 0.01 , StartDistance.f = 20.0, EndDistance.f = 60.0)
* CreateWater(Name.s, Texture.s, Width.f, Depth.f, SubDivs.i)  
* WaterRenderList(Water, Mesh)  
* SetWater(Mesh, WindForce.f = -5, WaveHeight.f = 0.05, BumpHeight.f = 0.05, Color = 0, ColorBlendFactor.f = 0.1)

Example : http://falsam.com/sbbjs/terrain.html
  
**■ Light**
You can define four types of light.

**#BJS_Point** A point light is a light defined by an unique point in world space. The light is emitted in every direction from this point.

**#BJS_Directional** A directional light is defined by a direction (what a surprise!). The light is emitted from everywhere in the specified direction, and has an infinite range. 

**#BJS_Spot** A spot light is defined by a position, a direction, an angle, and an exponent. These values define a cone of light starting from the position, emitting toward the direction.

The angle, in degrees, defines the size (field of illumination) of the spotlight's conical beam , and the exponent defines the speed of the decay of the light with distance (reach).

**#BJS_Hemispheric** A hemispheric light is an easy way to simulate an ambient environment light. A hemispheric light is defined by a direction, usually 'up' towards the sky. However it is by setting the color properties that the full effect is achieved.(Default)

There are three properties of lights that affect color. Two of these diffuse (#BJS_Diffuse gives the basic color to an object) and specular (#BJS_Specular produces a highlight color on an object) apply to all four types of light, the third, groundColor (#BJS_GroundColor), only applies to an Hemispheric.

* Light = CreateLight(id.s, x.f, y.f, z.f, intensity.f = 1, mode.i = #BJS_Hemispheric)
* SpotLightRange(Light, InnerAngle.f, Exponent.f)
* LightDirection(Light, x.f, y.f, z.f)
* MoveLight(Light.i, x.f, y.f, z.f, Mode = #PB_Relative)
* EnableLight(Light, Value.b)
* SetLightColor(Light, Type, Color) 
* Intensity.f = GetLightIntensity(Light)
* SetLightIntensity(Light, Intensity.f)

Example : http://falsam.com/sbbjs/light.html

**■ Shadow**
* ShadowGenerator = InitShadow(Light, RenderSize = 1024)
* ShadowEmitter(ShadowGenerator, Mesh)
* RenderShadows(Mesh, Value.b = #True)

Keep in mind that this shadow generator can only be used with one light. If you want to generate shadows from another light, then you will need to create another shadow generator.

Example : http://falsam.com/sbbjs/shadow.html

**■ Camera** 
* Value = CreateCamera(id.s, x.f, y.f, z.f, Type = #BJS_Free)  
* CameraLookAtMesh(Camera, MeshObject)  
* CameraLookAt(Camera, x.f, y.f, z.f)
* ActiveCamera(Camera)
* MoveCamera(Camera, x.f, y.f, z.f, Mode = #PB_Absolute)
* Value.f = CameraX(Camera)
* Value.f = CameraY(Camera)
* Value.f = CameraZ(Camera)
* RotateCamera(Camera, x.f, y.f, z.f, Mode = #PB_Absolute)  
* CameraMapKey(Camera, Key, Value = #PB_Ignore)
* DisableControlCamera(Camera, Value.b = #All)
* CameraCollision(Camera, Value = #True)
* CameraGravity(Camera, Value = #True)
* CameraBodySize(Camera, x.f = 1, y.f = 1, z.f = 1)
* Value.f = GetCameraBeta(Camera)
* Value.f = GetCameraAlpha(Camera)
* Value.f = GetCameraRadius(Camera)
* SetCameraBeta(Camera, Value.f)
* SetCameraAlpha(Camera, Value.f)
* SetCameraRadius(Camera, Value.f)

**■ Texture**
* Value = LoadTexture(FileName.s)
* Value = LoadCubeTexture(FileName.s)
* Value = LoadVideoTexture(Names.s, FileName.s)
  
**■ Material**
* Material = CreateMaterial(Name.s, Image.s, BackFaceCulling = #False)
* ScaleMaterial(Material, UScale.f, VScale.f)
* ScrollMaterial(Material, UOffset.f, VOffset.f)
* SetMaterialColor(Material, Type, Color)
* SetMaterialTexture(Material, Type, FileName.s)
* SetMaterialAttribute(Material, Attribut, Value.f)
* Value = CloneMaterial(Material)
* SetMeshMaterial(Mesh, Material)  
  
**■ Mesh**
* Mesh = CreateSphere(Name.s, Size.f, Subdivs.i = 16)  
* Mesh = CreateGround(Name.s, Width.f, Depth.f, Subdivs=2)
* Mesh = CreateBox(Name.s, Width.f, Height.f, Depth.f)
* Mesh = CreatePlane(Name.s, Width.f, Height.f)
* Mesh = CreateCylinder(Name.s, Height.f, DiamTop.f, DiamBottom.f, Tessellation.i = 30, HeightSubdivs.i = 1)
* Mesh = CreateTorus(Name.s, Diameter, Thickness, Tesselation = 32)
* Mesh = CreateIcoSphere(Name.s, Radius, RadiusY, Subdivs = 16)
* Mesh = CreateTube(Name.s, Array VectorsArray.NewVector(1), Radius.f, Tessellation = 32, RadiusFunction = #PB_Ignore)
* Mesh = CreateTerrain(Name.s, HeightmapPath.s, Width.f, Depth.f, Subdivs.i, MinHeight.f, MaxHeight.f)
* CreateMeshBody(Mesh, Type, Mass.f = 1.0, Restitution.f = 1.0, Friction = 0.1)
* ApplyMeshImpulse(Mesh, x.f, y.f, z.f)
* Value = GetMeshName(Mesh)
* FreeMesh(Mesh)
* MoveMesh(Mesh, x.f, y.f, z.f, Mode = #PB_Absolute)
* RotateMesh(Mesh, x.f, y.f, z.f, Mode = #PB_Absolute)
* ScaleMesh(Mesh, x.f, y.f, z.f, Mode = #PB_Absolute)
* Value.f = MeshX(Mesh)
* Value.f = MeshY(Mesh)
* Value.f = MeshZ(Mesh)
* Value = CloneMesh(Mesh)
* MergeMeshes(Array Meshes(1))
* Attach(Parent, Child, x.f, y.f, z.f)
* SetMeshPivot(Mesh, x.f, y.f, z.f)
    
**■ Picking**
* PickEnable() 
* IsPick()
* PickMesh()
* Value.f = PickX()
* Value.f = PickY()
* Value.f = PickZ()
* Value.f = PickDistance()
* MeshId(Mesh)
* Translate(Mesh, Value.f) Move mesh local
  
**■ Particle**
* Emitter = CreateParticleEmitter(Name.s, Mesh, MaxNumberParticles = 2000) 
* ParticleTexture(Emitter, FileName.s)
* ParticleEmitBox(Emitter, x0.f, y0.f, z0.f, x1.f, y1.f, z1.f)
* ParticleColor(Emitter, Color1, Color2)
* ParticleColorDead(Emitter, Color)
* ParticleSizeRange(Emitter, Min.f, Max.f)
* ParticleTimeToLive(Emitter, Min.f, Max.f)
* ParticleEmissionRate(Emitter, Value.i)
* ParticleGravity(Emitter, x.f, y.f, z.f)
* ParticleDirection(Emitter, x1.f, y1.f, z1.f, x2.f, y2.f, z2.f)
* ParticleAngularSpeed(Emitter, Min.f, Max.f)
* ParticleSpeed(Emitter, Min.f, Max.f, Update.f)
* StartParticle(Emitter)
* StopParticle(Emitter)

Example 
http://falsam.com/sbbjs/particle.html
http://falsam.com/sbbjs/garden.html


**■ Music**
* Music = MusicLoad(Name.s, FileName.s, Loop = #False, Autoplay = #False, CallBack = #False)
* MusicVolume(Music, Value.f)
* GetMusicVolume(Music)
* MusicPlay(Music)
* IsMusicPlay(Music)
* MusicPause(Music)
* IsMusicPause(Music)
* MusicStop(Music)
* MusicPosition(Music, x.f, y.f, z.f)
* MusicAttachToMesh(Music, Mesh)

Example : http://falsam.com/sbbjs/music.html

**■ GUI**
* CreateDynamicTexture(Mesh = #False) 	
* AddControl3D(Parent, Child)
* HideControl3D(Object, Value = #True)
* Rectangle3D(Name.s, x.i, y.i, Width.i = -1, Height.i = -1, Radius = 8, Thickness = 1)
* Text3D(Name.s, x.i, y.i, Width.i, Height.i, Text.s, Align = #BJS_Center)
* Button3D(Name.s, x.i, y.i, Width.i, Height.i, Text.s, Callback, CornerRadius = 8)
* Image3D(Name.s, x.i, y.i, Width.i, Height.i, FileName.s, OnClick = #False)
* Slider3D(Name.s, x.i, y.i, Width.i, Height.i, MiniMum.i, Maximum.i, OnChange, BarOffset = 8)
* Input3D(Name.s, x.i, y.i, Width.i, Height.i, Text.s, OnLostFocus=#False, OnTextChange=#False, OnGetFocus=#False)
* PickerColor3D(Name.s, x.i, y.i, Width.i, Height.i, CallBack)
* GetText3D(Object)
* SetText3D(Object, Text.s)
* SetColor3D(Object, ColorType, Color)
* SetTextFont3D(Object, FontFamily.s, FontSize)
* SetOpacity3D(Object, Alpha.f)
* SetZindex3D(Object, zIndex.i)
* GetState3D(Object)
* SetState3D(Object, Value)
* Text3DLinkToMesh(Mesh, ObjectText, OffSetY.f)
* MoveObject3D(Object, x.i, y.i)

Example 
http://falsam.com/sbbjs/gui.html
http://falsam.com/sbbjs/sceneshoot.html

**■ Keyboard**
* InitKey()
* KeyPushed(Key)
* KeyReleased(Key)
  
**■ Tools**
* RunURL(Url.s, NewTab.b = #True)

