import moviepy.editor as mp
from pathlib import Path

# Define file paths
input_path = Path("/mnt/data/videoplayback.mp4")
output_path = Path("/mnt/data/edited_video.mp4")

# Load the original video
video = mp.VideoFileClip(str(input_path))

# Basic stylized effect: speed up slightly, add color tint, and simulate motion (light effect for now)
edited_video = (
    video.fx(mp.vfx.colorx, 1.4)           # Increase brightness/saturation a bit
          .fx(mp.vfx.lum_contrast, 0, 50, 255)  # Increase contrast
          .fx(mp.vfx.speedx, 1.15)          # Slight speed-up to match AMV energy
)

# Write the processed video
edited_video.write_videofile(str(output_path), codec="libx264", audio_codec="aac")
