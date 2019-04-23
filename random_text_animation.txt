import random, bpy
def init_text_animation(text_for_animation):
	bpy.ops.object.delete(use_global=False) # delete the cube
	bpy.context.scene.frame_end = 101 #set animation end frame as 101
	xval = - (((len(text_for_animation))*0.6)/2.0)  # set the initial position of x-axis value
	i=2 # 2 objects already exist, one in camera and the other is lamp
	for ch in text_for_animation: #for each character in the text
		if(ch != ' '):	
			bpy.ops.object.text_add(view_align=False, enter_editmode=False, location=(xval, 0, 0), layers=(True, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False))
			bpy.ops.transform.rotate(value=1.5708, axis=(1, 0, 0), constraint_axis=(True, False, False), constraint_orientation='GLOBAL', mirror=False, proportional='DISABLED', proportional_edit_falloff='SMOOTH', proportional_size=1)
			bpy.ops.object.editmode_toggle()
			bpy.ops.font.delete(type='PREVIOUS_OR_SELECTION')
			bpy.ops.font.delete(type='PREVIOUS_OR_SELECTION')
			bpy.ops.font.delete(type='PREVIOUS_OR_SELECTION')
			bpy.ops.font.delete(type='PREVIOUS_OR_SELECTION')
			bpy.ops.font.text_insert(text=ch)
			bpy.ops.object.editmode_toggle()
			obj = bpy.data.objects[i]
			obj.data.extrude = 0.1
			obj.data.align_x = 'CENTER'
			obj.keyframe_insert(data_path="location", frame=100.0, index=-1)
			obj.location[0] = random.randrange(-10,10)
			obj.location[1] = random.randrange(-10,10)
			obj.location[2] = random.randrange(-10,10)
			obj.keyframe_insert(data_path="location", frame=1.0, index=-1)
			i = i+1
		xval = xval + 0.6

init_text_animation("I love open source by Akhil Ennu") #****************Edit Here*************************

