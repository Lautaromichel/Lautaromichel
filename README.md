from moviepy.editor import *
from moviepy.video.tools.drawing import color_gradient

# Duración total del video
duracion_total = 10  # segundos

# Clip de introducción
intro_texto = TextClip("Cable Carril de Chilecito, La Rioja", fontsize=40, color='white')
intro_texto = intro_texto.set_position('center').set_duration(4).set_bg_color("black")

# Clip sobre matrices
matrices_texto = TextClip("Las matrices en ingeniería y física\n permiten calcular fuerzas y trayectorias.", fontsize=30, color='yellow')
matrices_texto = matrices_texto.set_position('center').set_duration(3).set_bg_color("blue")

# Clip de relación entre el cable carril y matrices
relacion_texto = TextClip("En el cable carril, las matrices calculan la estabilidad y distancia entre estaciones.", fontsize=30, color='white')
relacion_texto = relacion_texto.set_position('center').set_duration(3).set_bg_color("green")

# Crear un fondo de color con degradado
background = ColorClip(size=(640, 360), color=(0, 0, 0), duration=duracion_total)
background = background.fl_image(lambda img: color_gradient(img, p1=(0, 0), p2=(640, 360), 
                                  color1=(50,50,150), color2=(200,200,255)))

# Combinar los clips de texto y el fondo
video = CompositeVideoClip([background, intro_texto.set_start(0), matrices_texto.set_start(4), relacion_texto.set_start(7)])

# Guardar el video
video.write_videofile("video_cable_carril_matrices.mp4", fps=24)
