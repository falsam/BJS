# BJS
Babylon.sbi for SpiderBasic

**Engine**
* InitEngine(Callback, CanvasOutput = #PB_Ignore)  
* CreateSpace2D(Scene)  
* RenderLoop(Callback)  
* RenderWorld()  
* EnablePhysics()  
* MeshCollide(Mesh1, Mesh2)
  
**Scene**
* CreateScene()  
* SceneGravity(x.f = 0, y.f = -0.9, z.f = 0)   
* ClearScene(color)  
* CurrentScene(Scene, Camera)  
* ImportScene(Name.s, Path.s, FileName.s, Callback)  
* SaveScene(Scene, Name.s)  
* EnableOffLineSupport(Value = #True)   
* SceneDebug()  
   
**Environment**
* SkyBox(name.s, sky.s, size.i = 200)  
* CreateWater(Name.s, Texture.s, Width.f, Depth.f, SubDivs.i)  
* WaterRenderList(Water, Mesh)  
* SetWater(Mesh, WindForce.f = -5, WaveHeight.f = 0.05, BumpHeight.f = 0.05, Color = 0, ColorBlendFactor.f = 0.1)
* Fog(Color, Intensity.f = 0.01 , StartDistance.f = 20.0, EndDistance.f = 60.0)
* AmbientColor(Color.i)
  
**Light**
* CreateLight(id.s, x.f, y.f, z.f, intensity.f = 1, mode.i = #Hemispheric)
* SpotLightRange(Light, InnerAngle.f, OuterAngle.f)
* LightDirection(Light, x.f, y.f, z.f)
* MoveLight(Light.i, x.f, y.f, z.f, Mode = #PB_Relative)
* EnableLight(Light, Value.b)
* SetLightColor(Light, Type, Color)
  
**Shadow**
* InitShadow(Light, RenderSize = 1024)
* ShadowEmitter(Mesh)
* RenderShadows(Mesh, Value.b = #True) 
 
**Camera** 
* CreateCamera(id.s, x.f, y.f, z.f, Type = #Free)  
* CameraLookAtMesh(Camera, MeshObject)  
* CameraLookAt(Camera, x.f, y.f, z.f)
* ActiveCamera(Camera)
* MoveCamera(Camera, x.f, y.f, z.f, Mode = #PB_Absolute)
* CameraX(Camera)
* CameraY(Camera)
* CameraZ(Camera)
* RotateCamera(Camera, x.f, y.f, z.f, Mode = #PB_Absolute)  
* CameraMapKey(Camera, Key, Value = #PB_Ignore)
* DisableControlCamera(Camera, Value.b = #All)
* CameraCollision(Camera, Value = #True)
* CameraGravity(Camera, Value = #True)
* CameraBodySize(Camera, x.f = 1, y.f = 1, z.f = 1)
* GetCameraBeta(Camera)
* GetCameraAlpha(Camera)
* GetCameraRadius(Camera)
* SetCameraBeta(Camera, Value.f)
* SetCameraAlpha(Camera, Value.f)
* SetCameraRadius(Camera, Value.f)
  
**Material**
* CreateMaterial(Name.s, Image.s, BackFaceCulling = #False)
* ScaleMaterial(Material, UScale.f, VScale.f)
* ScrollMaterial(Material, UOffset.f, VOffset.f)
* SetMaterialColor(Material, Type, Color)
* SetMaterialTexture(Material, Type, FileName.s)
* SetMaterial(Mesh, Material)  
  
**Mesh**
* CreateSphere(Name.s, Size.f, Subdivs.i = 16)  
* CreateGround(Name.s, Width.f, Depth.f, Subdivs=2)
* CreateBox(Name.s, Size.f)
* CreatePlane(Name.s, Size.f)
* CreateCylinder(Name.s, Height.f, DiamTop.f, DiamBottom.f, Tessellation.i = 30, HeightSubdivs.i = 1)
* CreateTorus(Name.s, Diameter, Thickness, Tesselation = 32)
* CreateTerrain(Name.s, HeightmapPath.s, Width.f, Depth.f, Subdivs.i, MinHeight.f, MaxHeight.f)
* CreateBody(Mesh, Type, Mass.f = 1.0, Restitution.f = 1.0, Friction = 0.1)
* ApplyMeshImpulse(Mesh, x.f, y.f, z.f)
* GetMeshName(Mesh)
* FreeMesh(Mesh)
* MoveMesh(Mesh, x.f, y.f, z.f, Mode = #PB_Absolute)
* RotateMesh(Mesh, x.f, y.f, z.f, Mode = #PB_Absolute)
* ScaleMesh(Mesh, x.f, y.f, z.f, Mode = #PB_Absolute)
* MeshX(Mesh)
* MeshY(Mesh)
* MeshZ(Mesh)
* CloneMesh(Mesh)
* Attach(Parent, Child, x.f, y.f, z.f)
    
**Picking**
* PickEnable() 
* IsPick()
* PickMesh()
* PickX()
* PickY()
* PickZ()
* PickDistance()
* MeshId(Mesh)
* Translate(Mesh, Value.f) Move mesh local
  
**Particle**
* CreateParticleEmitter(Name.s, Mesh, MaxNumberParticles = 2000) 
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

**Music**
* MusicLoad(Name.s, FileName.s, Loop = #False, Autoplay = #False, CallBack = #False)
* MusicVolume(Music, Value.f)
* GetMusicVolume(Music)
* MusicPlay(Music)
* IsMusicPlay(Music)
* MusicPause(Music)
* IsMusicPause(Music)
* MusicStop(Music)
* MusicPosition(Music, x.f, y.f, z.f)
* MusicAttachToMesh(Music, Mesh)

**GUI**
* Text2D(x, y, Text.s, CallBack = #False, Font.s = "25pt Arial", Color = $FF000000) 	
* Rectangle2D(x, y, w, h, Radius = 6, BorderSize = 4, CallBack = #False, FillColor = $FFFFFFFF, BorderColor = $FF000000) 
* Button2D(x.f, y.f, w.f, h.f, Radius = 6, BorderSize = 4, Text.s = "", CallBack = #False, Font.s = "25pt Arial", FillColor = $FFFFFFFF, FrontColor = $FF000000, BorderColor = $FF000000)
* Image2D(x.f, y.f, Image.s);
* SetText(Element, Text.s)

**Keyboard**
* InitKey()
* KeyPushed(Key)
* KeyReleased(Key)
  
**Tools**
* RunURL(Url.s, NewTab.b = #True)
