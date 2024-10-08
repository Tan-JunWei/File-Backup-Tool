## Purpose
This is a Python script that facilitates the backup, compression, and decompression of directories. It provides functionalities to copy files from a source directory to a destination directory, compress a directory into a zip file, and decompress a zip file into a directory.

## Uses
- **File Backup:** Copies files from a source directory to a destination directory, only backing up modified files and creating a log of the operation (`backup_log.txt`).
- **Directory Compression:** Compresses a directory into a zip file for easier storage or transfer.
- **Directory Decompression:** Extracts the contents of a zip file into a specified directory.

## Unique Feature
- The `fuzzywuzzy` Python library is used in this script to implement a basic "autocorrect" feature for directory names. This feature helps handle cases where the user might provide a misspelled directory name. By leveraging fuzzy string matching, `fuzzywuzzy` suggests the closest match from existing directories, making the script more user-friendly and reducing errors due to typo errors.

More information about `fuzzywuzzy` can be found [here](https://pypi.org/project/fuzzywuzzy/).

## Installation
1. Clone the repository
```bash
git clone <link>
```
2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage
Run the script with the following command (note that compress/decompress arguments are optional):
```bash
python file_backup.py <source-directory-path> <destination-directory-path> [compress/decompress]
```

If directory paths contain spaces(" "), **enclose them in double quotes** to ensure they are properly recognized and not misinterpreted as separate arguments.

### Examples

**Backup files from source to destination:**
```bash
python file_backup.py "/path/to/source directory" "/path/to/destination directory"
```

**Compress a directory:**
```bash
python file_backup.py "/path/to/source directory" "/path/to/destination directory" compress
```

**Decompress a directory:**
```bash
python file_backup.py "/path/to/source directory" "/path/to/destination directory" decompress
```

### Error Handling
If you run the script with a source directory name that is not found:
```bash
python file_backup.py "/path/to/nonexistent source directory" "/path/to/destination directory"
```

A message similar to this will be displayed:
```
Source directory does not exist!

Directories within the parent directory:
    /path/to/existing directory 1
    /path/to/existing directory 2
    /path/to/existing directory 3

Did you mean "/path/to/existing directory"?
```
This suggestion uses fuzzy matching and can help guide users to the correct directory.