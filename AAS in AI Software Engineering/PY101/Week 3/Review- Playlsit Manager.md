
### 🎼 Playlist Manager Cheat Sheet

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

  ```plaintext
  genre_counts = {}
  for song in playlist:
      genre = song["genre"]
      count = genre_counts.get(genre, 0) # Get old count, or 0
      genre_counts[genre] = count + 1
  # Result: {'Pop': 2, 'Rock': 1, ...}
  
  ```

- **To Get Unique Artists:** Use a `set` to automatically handle duplicates.

  Python

  ```plaintext
  artists = set()
  for song in playlist:
      artists.add(song["artist"])
  
  unique_count = len(artists)
  ```