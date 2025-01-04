# Minigrep

A simple command-line tool written in Rust that searches for text patterns in files, similar to the grep utility.

## Features

- Case-sensitive and case-insensitive search
- File content searching
- Environment variable configuration
- Error handling with informative messages

## Installation

### From Source
Make sure you have Rust and Cargo installed on your system. Then:

```bash
git clone [your-repository-url]
cd minigrep
cargo build --release
```

The compiled binary will be available at `target/release/minigrep.exe`

### Windows Executable
1. Download `minigrep.exe`
2. (Optional) Add the folder containing minigrep.exe to your system PATH
   - Right-click on 'This PC' or 'My Computer'
   - Click 'Properties'
   - Click 'Advanced system settings'
   - Click 'Environment Variables'
   - Under 'System Variables', find and select 'Path'
   - Click 'Edit'
   - Click 'New'
   - Add the folder path containing minigrep.exe
   - Click 'OK' on all windows

## Detailed Usage Guide

### Basic Command Structure

```cmd
minigrep.exe [search_query] [file_path]
```

### Command Parameters

1. `search_query`: The text pattern you want to find
   - Can be a single word or multiple words in quotes
   - Case-sensitive by default
   - Examples:
     ```cmd
     minigrep.exe hello file.txt        # Searches for "hello"
     minigrep.exe "hello world" file.txt  # Searches for "hello world"
     ```

2. `file_path`: The path to the file you want to search in
   - Can be relative or absolute path
   - Examples:
     ```cmd
     minigrep.exe hello .\docs\file.txt     # Relative path
     minigrep.exe hello C:\Users\docs\file.txt  # Absolute path
     ```

### Case Sensitivity Options

#### Using Command Prompt
```cmd
# Case-insensitive search
set IGNORE_CASE=1
minigrep.exe to poem.txt
```

#### Using PowerShell
```powershell
# Case-insensitive search
$env:IGNORE_CASE=1; .\minigrep.exe to poem.txt
```

### Example Usage Scenarios

1. Basic search:
   ```cmd
   minigrep.exe "function" src\main.rs
   ```
   Finds all lines containing "function" in main.rs

2. Case-insensitive search in multiple files:
   ```powershell
   # PowerShell
   $env:IGNORE_CASE=1; Get-ChildItem *.txt | ForEach-Object { .\minigrep.exe "error" $_.Name }
   ```

3. Search in a specific directory:
   ```cmd
   minigrep.exe "TODO" .\src\*.rs
   ```

### Exit Codes

- 0: Successful execution
- 1: Error occurred (invalid arguments, file not found, etc.)

## Error Messages and Troubleshooting

Common error messages and their solutions:

1. "Problem parsing arguments":
   - Ensure you provided both search query and file path
   - Check if file path is correct
   - Enclose multi-word queries in quotes

2. "Application error":
   - Verify file exists and you have read permissions
   - Check if file content is valid UTF-8
   - Ensure sufficient system memory

3. "'minigrep' is not recognized as an internal or external command":
   - Make sure you're in the correct directory containing minigrep.exe
   - Or add the directory to your PATH (see Installation section)
   - Use complete path to executable: `C:\path\to\minigrep.exe`

## Project Structure

- `src/main.rs`: Entry point of the application
- `src/lib.rs`: Core functionality implementation
  - `Config`: Handles program configuration and argument parsing
  - `run`: Main program logic
  - `search`: Case-sensitive search implementation
  - `search_case_insensitive`: Case-insensitive search implementation

## Testing

Run the test suite with:

```cmd
cargo test
```

For verbose output including passed tests:
```cmd
cargo test -- --show-output
```

The test suite includes:
- Case-sensitive search functionality
- Case-insensitive search functionality
- Configuration parsing

## Contributing

Feel free to submit issues and pull requests.

### Development Setup

1. Clone the repository
2. Install Rust and Cargo
3. Run tests to ensure everything works
4. Create a new branch for your changes
5. Submit a pull request

## License

[Your chosen license]

## Author

[Your name/organization]
