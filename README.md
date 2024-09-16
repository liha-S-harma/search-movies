# search-movies
#python code to find movies in computer system 
import os
import fnmatch

# List of common movie file extensions
movie_extensions = ['*.mp4', '*.mkv', '*.avi', '*.mov', '*.flv']

# Function to search for movie files
def find_movies(directory):
    movie_files = []
    
    # Traverse the directory tree
    for root, dirs, files in os.walk(directory):
        for ext in movie_extensions:
            for filename in fnmatch.filter(files, ext):
                movie_files.append(f"file://{os.path.join(root, filename)}")
    
    return movie_files

# Replace 'C:\\' with the drive or folder where you want to search for movies
movies_found = find_movies("C:\\")

# Display the list of found movie files
for movie in movies_found:
    print(movie)
