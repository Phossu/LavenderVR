# Avatar Creation

## Short Version ##

### Very very short version ###

* The same process as ''other unity game'' but using Lavender's Avatar component at the end, then creating and uploading a .avatar file for use within the game.

### Very short version ###

* Install Lavender SDK into a Unity 2019.3 project
** SDK location currently on the Lavender discord in #release-info
** "Setup project defaults" (Important)
* Rig up an Avatar - materials, rigging, etc.
* Create a .avatar file with the SDK's avatar component
* Upload to the Lavender website
* Load in Lavender

It is very similar to ''other unity games that allow user content'' so if you've made on in that you'll have no problems here.

### Short(?) version ###

* Install unity hub and install Unity 2019.3. 3D project.
** Modules - Add linux and android for future compatability, but not required for now.
* Highly recommened to make a new project - don't port over projects from ''other unity games''.
** If you have to, delete the ''other unity game'' SDK beforehand.
* Download and install then Lavender SDK
** Currently located on the discord, planned to be on steam tools.
* Select and run "Setup Project Defaults" from the SDK menu.
* Make a new scene for your avatar to be loaded and setup inside
* Import content. If FBX, the process is like ''other unity game''
* Pull into scene
** If moving from ''other unity game'' then you can copy over your folders to the new 2019.3 project and then the process will involve fixing it up.
* Rigging and bones: Ensure humanoid. 
** If it has 'old cats fix' with the flipped hips this will break the avatar. Redo CATS with new CATS in this case.
** Lavander works from the standard humanoid layout in unity so if unity likes it there's a good chance it's fine in Lavender. No hacks needed.
* Dynamic bones: Lavender has its own version that supports threading and colliders.
** Jiggle Bones!
*** ''Should'' just be able to copy and paste settings from your dynamic bones.
*** Missing 'end length' parameter, called 'end offset'
* Colliders: Feel free to add more than you think you should, as they're threaded in Lavender.
* Set up materials, textures, etc
** The move to 2019.3 shouldn't break anything but if it does, you'll probably have to change or update your shader.
* Gestures and animations
** Current support for 4 gestures
** Create gestures as an animation like ''other unity game'', but assign them to the gesture's list in the avatar component, and assign them to hands.
** To use them ingame you need to set them as SteamVR bindings. No default controls yet.
* When avatar ready, add the Lavender avatar descriptor (Just called "Avatar").
** Viewball is easier to do if wireframe is set and you look at the scene from the side
** Other ball is where noise comes out of when you speak
** If you have visemes generated by CATS you can just click the button (and fix sil usually)
** Set gestures here. 
* Building and Uploading
** Click quick build.
** Upload .avatar file to lavender website.
** Add picture, description, etc.
* Done!
* You should be able to use your avatar in lavender.

= Detailed Information and Basics =

== Rigging ==

Rigging a model for Unity will be the same as for ''other unity games''. Rigging means having 'bones', which are virtual items that when moved, manipulate the mesh of the model around them in predictable locations. In Lavender they will map to your real head, arms, legs and so on. Moving your arm in the game will move the arm bones on your model, taking with it the mesh assigned to the bone.

When you first pull in an FBX into unity for use in Lavender, you will need to create a rigged character that Unity can use (a Humanoid character or any other Unity Mecanim viable rigged model), if such a model is available, creating an avatar is possible and can be done by first importing the 3d model into Unity by dragging and dropping it into the Project Folder, clicking on the model & then going to Rig, selecting “Humanoid” from the Animation Type then applying settings so the Avatar can be configured, then under Avatar Definition, select “Create From This Model” from the dropdown menu before pulling it into the scene.

This will switch Unity into the Rig Mapping mode, check if every bone is correctly assigned (If everything is green, things are likely good to go - depending on the character), scroll down on the very left side and press Apply/Done, assuming the model has been correctly configured, drag the model into the scene/hierarchy window and everything is good to go for the next step.

== Materials ==

Setting up Materials is required for the Avatar model to shade properly, if the model has already had materials setup in a 3d modelling suite such as Blender, Maya, 3DSMax, then it is possible to extract those materials. This is done by going to the same page as the Model Setup, clicking on the Materials tab and clicking on “Extract Materials”, choose a folder within the models Project Folder. In the material folder, select each material one by one and assign the texture(s) corresponding to the Material, if everything is setup correctly, you should see the changes reflected within the scene, assuming that the Model is present in the current scene.

Note: If the Standard shader material setup does not look satisfactory for an Anime/Cartoon style character, you may download a open-source toon shader. Here are two that should work with the latest version of Unity:

[NoeNoe](https://github.com/HugoZink/NoeNoeShaderEdits)

[Poiyomi](https://github.com/poiyomi/PoiyomiToonShader)

For the new Unity Scriptable Render Pipelines such as HDRP/URP, a Shader Graph shader will be linked here on a later date.

== Avatar Component Setup ==

This is the final step within Unity, to setup your Avatar for Lavender, click on your model, on the very right side click “Add Component” and search for “Avatar” and press Enter. This should add the Lavender SDK Avatar component to the character, this is a required component. Within this Script, we have to setup the View Offset and Mouth Offset and assign our Visemes, once this is done we can hit Quick Build Avatar to create it.
* View Offset
The View Offset is used as the point of view position of our character, usually this point is positioned in between our characters eyes with a depth that matches this.
* Mouth Offset
The Mouth Offset is used as the audio position of our character, this is from where a sound will be heard from when a player talks.
* Other
In most cases, the Hide Action does not need to be changed, only in certain cases such as when our character has their face or head model separated from the body we may need to use Toggle Mesh instead of Scale Head Down and move the model into the selection field, advanced users are also able to use the Shape Key function.
* Visemes
If our character in the scene has Visemes (pre-made mouth shapes required for lip sync), all we have to do is expand the prefab from the Unity Hierarchy found on the left side of the Editor and drag the character’s main mesh into the Viseme field, often this is called Body. If you have used a Blender addon called CATS to create these shapes, Lavender SDK script can auto-assign the Visemes for us. (Auto Assign by close enough name)

When everything is correct, hit Quick Build Avatar, the file will be in the root of our Project Folder. We’re done!

Now we just need to upload to our account on the website:
[Uploading Content](./uploading-content.md)

