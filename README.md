 organizer.py
import os
import shutil

# Change this to your Downloads path
folder_path = "C:/Users/YourName/Downloads"

# File types
file_types = {
    "Images": [".jpg", ".png", ".jpeg"],
    "Documents": [".pdf", ".docx", ".txt"],
    "Videos": [".mp4", ".mkv"],
    "Music": [".mp3", ".wav"],
    "Zips": [".zip", ".rar"]
}

for file in os.listdir(folder_path):
    file_path = os.path.join(folder_path, file)

    if os.path.isfile(file_path):
        ext = os.path.splitext(file)[1].lower()

        for folder_name, extensions in file_types.items():
            if ext in extensions:
                new_folder = os.path.join(folder_path, folder_name)
                os.makedirs(new_folder, exist_ok=True)
                shutil.move(file_path, os.path.join(new_folder, file))
                print(f"Moved {file} -> {folder_name}")
                break

print("Done! Folder organized.")