# NoSQL Data Lake - Online Record Store
## Universal Studios Colombia

### Project Overview
This project involves the construction and management of a NoSQL Data Lake for Universal Studios Colombia's online record store. Utilizing **MongoDB** as the core database engine, we modeled and managed a collection of albums and songs from internationally renowned artists across various genres.

### Data Model Structure
The database follows a non-relational document-based model:
- **Database:** `universal_studios_db`
- **Collections:** Each album is represented by a separate collection.
- **Documents:** Each song is a JSON/BSON document with the following mandatory fields:
  - `_id`: Unique identifier.
  - `titulo`: Song title.
  - `anio_salida`: Release year.
  - `autor`: Artist or band name.
  - `id_imagen_portada`: Path to the album cover image (stored in `/images`).

---

### Project Tasks Summary

#### Task 1: Initial Database Creation
- **Objective:** Establish the baseline database with one album per artist for 6 different artists: Lady Gaga, Diomedes Díaz, BTS, Michael Jackson, Queen, and Ivy Queen.
- **Deliverables:** Initial JSON/CSV exports and the `images/` folder.
- **Branch:** `main`

#### Task 2: Album Updates
- **Objective:** Expand the Data Lake by incorporating "hidden gems" or less-known tracks from the same albums.
- **Action:** We added 2 additional songs to each collection (IDs ending in `_04` and `_05`).
- **Branch:** `actualizaciones`

#### Task 3: Data Deletion & Cleanup
- **Objective:** Perform administrative cleanup tasks.
- **Actions:**
  - Deleted the 2 newest songs added in Task 2 from each album to revert to the main hits.
  - Performed a full **Collection Drop** on the album "Sentimiento" by Ivy Queen.
- **Branch:** `eliminaciones`

---

### Key Findings & Design Decisions
- **Modularity:** Using a separate collection for each album allowed for better organization, though a single "albums" collection with nested songs could be an alternative design for different use cases.
- **Naming Conventions:** We maintained strict naming for image assets to ensure the `id_imagen_portada` field always points to a valid file in the repository.
- **Integrity:** MongoDB's flexible schema allowed us to easily add and remove documents without affecting the structure of the remaining data.

### Challenges & Learnings
- **Tooling:** We gained hands-on experience using **MongoDB Atlas** for cloud hosting and **MongoDB Compass** for efficient data exporting (CSV/JSON).
- **Git Workflow:** Managing multiple branches (`main`, `actualizaciones`, `eliminaciones`) was essential for maintaining a clear history of the database evolution.

### How to Replicate
1. **Prerequisites:** Install MongoDB Compass.
2. **Import:**
   - Create a database named `universal_studios_db`.
   - Use the "Import Data" feature in Compass to load the `.json` or `.csv` files provided in this repository into their respective collections.
3. **Images:** Ensure the `images/` folder is placed in the same root directory to maintain correct paths for the album covers.
