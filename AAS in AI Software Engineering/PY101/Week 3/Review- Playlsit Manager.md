
### 🎼 Playlist Manager Cheat Sheet

### 1. The Data: Parse Text to a List of Dictionaries

**Instruction:** You first needed to take a raw block of text and parse it into a list of dictionaries, converting data types (like `duration` to a `float`) along the way.

**Your Code:**

Python

```python
data = """Summer Set|Dia|2.12|Pop
Something in the Orange|Zach Brown|4.15|Country
Yellow Glow|YellowCard|3.20|Rock"""

playlist = [] 
lines = data.splitlines()
for line in lines:
    parts = line.split("|")
    song_dict = {
        "title": parts[0].strip(),
        "artist": parts[1].strip(),
        "duration": float(parts[2]),
        "genre": parts[3].strip()
    }
    playlist.append(song_dict)
```

---

### 2. Function: Add a New Song

**Instruction:** "Add a new song to playlist."

**Your Code:**

Python

```python
def add_song(playlist_list, song_to_add):
    """
    Adds a new song (a dictionary) to the playlist (a list).
    """
    playlist_list.append(song_to_add)
    print(f"\nAdded '{song_to_add['title']}' to the playlist.")
```

---

### 3. Function: Remove a Song by Title

**Instruction:** "Remove a song by its title."

**Your Code:**

Python

```python
def remove_song(playlist_list, title_to_remove):
    """
    Finds a song by its title string and removes it from the list.
    """
    song_found = None
    for song in playlist_list:
        if song["title"] == title_to_remove:
            song_found = song
            break

    if song_found:
        playlist_list.remove(song_found)
        print(f"\nRemoved '{title_to_remove}' from the playlist.")
    else:
        print(f"\nCould not find '{title_to_remove}' in the playlist.")
```

---

### 4. Function: Sort the Playlist (with Guard Clause)

**Instruction:** "Sort the playlist by any chosen field (title, artist, duration, or genre)." **Improvement:** "Add a guard for invalid sort keys to avoid possible runtime errors."

**Your Code:**

Python

```python
def sort_playlist(playlist_list, field_to_sort_by):
    """
    Sorts the playlist based on a given key (e.g., 'title', 'duration').
    """
    
    # --- This is the "Guard Clause" for the improvement ---
    if not playlist_list:
        print("\nPlaylist is empty, nothing to sort.")
        return 
        
    if field_to_sort_by not in playlist_list[0]:
        print(f"\nError: Cannot sort by '{field_to_sort_by}'. It is not a valid field.")
        return # Stop the function
    # --- End of guard ---

    playlist_list.sort(key=lambda song: song[field_to_sort_by])
    print(f"\nPlaylist sorted by '{field_to_sort_by}'.")
```

---

### 5. Functions: Summary Stats

**Instruction:** "Show at least two summary stats, for example: Total number of songs. Average song duration. Number of songs per genre. Number of unique artists."

**Your Code:**

Python

```python
def get_total_songs(playlist_list):
    """
    Calculates the total number of songs in the playlist.
    """
    return len(playlist_list)

def get_average_duration(playlist_list):
    """
    Calculates the average duration of all songs in the playlist.
    """
    if not playlist_list:
        return 0
    
    total_duration = 0
    for song in playlist_list:
        total_duration += song["duration"]
        
    return total_duration / len(playlist_list)

def get_songs_per_genre(playlist_list):
    """
    Counts the number of songs for each genre.
    Returns a dictionary, e.g., {'Pop': 2, 'Rock': 1}
    """
    genre_counts = {}
    for song in playlist_list:
        genre = song["genre"]
        current_count = genre_counts.get(genre, 0)
        genre_counts[genre] = current_count + 1
    return genre_counts

def get_unique_artists_count(playlist_list):
    """
    Calculates the number of unique artists in the playlist.
    """
    artists = set()
    for song in playlist_list:
        artists.add(song["artist"])
    return len(artists)
```

---

### 6. Demo Code (in `main` block)

**Instruction:** "Consider packaging your demo calls (add, sort, remove) inside a `main()` so they do not run on import."

**Your Code:**

Python

```python
# This block only runs when you execute this file directly.
if __name__ == "__main__":
    
    # (The parsing code from Step 1 also goes in here)
    data = """Summer Set|Dia|2.12|Pop
Something in the Orange|Zach Brown|4.15|Country
Yellow Glow|YellowCard|3.20|Rock"""

    playlist = [] 
    lines = data.splitlines()
    for line in lines:
        parts = line.split("|")
        song_dict = {
            "title": parts[0].strip(),
            "artist": parts[1].strip(),
            "duration": float(parts[2]),
            "genre": parts[3].strip()
        }
        playlist.append(song_dict)

    print("--- Initial Playlist ---")
    print(playlist)

    # Test adding a song
    new_song = {"title": "Friendly Fire", "artist": "Bad Monkeys", "duration": 2.30, "genre": "Indie"}
    add_song(playlist, new_song)

    # Test sorting (valid and invalid)
    sort_playlist(playlist, "artist")
    sort_playlist(playlist, "year") # Tests the guard clause

    # Test removing a song
    remove_song(playlist, "Yellow Glow")

    # --- Summary Stats Demo ---
    print("\n--- Summary Stats ---")
    total = get_total_songs(playlist)
    print(f"Total songs: {total}")

    average = get_average_duration(playlist)
    print(f"Average duration: {average:.2f} minutes")

    genres = get_songs_per_genre(playlist)
    print(f"Songs per genre: {genres}")

    unique_artists = get_unique_artists_count(playlist)
    print(f"Unique artists: {unique_artists}")
```

#### 1. Core Functions

- **To Add a Song:** Use `.append()` to add a new dictionary to your list.

  Python

  ```python
  # new_song = {"title": "...", "artist": "...", ...}
  playlist.append(new_song)
  
  ```

- **To Remove a Song (by Title):** Loop, find the song, and then `list.remove()` it.

  Python

  ```python
  song_to_delete = None
  for song in playlist:
      if song['title'] == "Title to Remove":
          song_to_delete = song
          break # Stop looking
  
  if song_to_delete:
      playlist.remove(song_to_delete)
  
  ```

- **To Sort the List:** Use `.sort(key=lambda s: s[field])`.

  Python

  ```python
  # Sort by 'artist'
  playlist.sort(key=lambda song: song["artist"])
  
  # Sort by 'duration'
  playlist.sort(key=lambda song: song["duration"])
  
  ```

---

#### 2. Summary Stats Functions

- **To Get Total Count:** Use `len()`.

  Python

  ```python
  total = len(playlist)
  
  ```

- **To Get Average Duration:** Loop, sum the values, and divide by the count.

  Python

  ```python
  total_duration = 0
  for song in playlist:
      total_duration += song["duration"]
  
  average = total_duration / len(playlist)
  
  ```

- **To Count by Genre:** Use a dictionary to keep track of counts.

  Python

  ```python
  genre_counts = {}
  for song in playlist:
      genre = song["genre"]
      count = genre_counts.get(genre, 0) # Get old count, or 0
      genre_counts[genre] = count + 1
  # Result: {'Pop': 2, 'Rock': 1, ...}
  
  ```

- **To Get Unique Artists:** Use a `set` to automatically handle duplicates.

  Python

  ```python
  artists = set()
  for song in playlist:
      artists.add(song["artist"])
  
  unique_count = len(artists)
  ```