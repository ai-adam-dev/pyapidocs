## PyDoc API Documentation

This documentation describes the `PyDoc` class and its methods, generated from the provided code.

### Class: `PyDoc`

The `PyDoc` class is designed to generate API documentation and a README file using a language model (Ollama).  It iterates through files matching a given extension within a specified directory (or the current working directory if no directory is provided), sends their contents to the language model, and writes the generated documentation to markdown files within a `docs/` directory.

#### Constructor: `__init__(self, model, extension, dir)`

*   **Parameters:**
    *   `model` (str):  The name of the Ollama language model to use for documentation generation.
    *   `extension` (str): The file extension to search for (e.g., "py", "js").
    *   `dir` (str, optional):  The directory to search for files.  If `None`, the current working directory is used. Defaults to `None`.

#### Method: `generate_documentation(self)`

*   **Description:** Generates API documentation for the files matching the specified extension.  Uses the provided language model to generate documentation content and writes it to markdown files in the `docs/` directory.
*   **Returns:** None
*   **Raises:**  Potentially raises exceptions related to Ollama API calls and file I/O.
*   **Example:**

```python
pydoc = PyDoc(model="llama2", extension="py", dir="src")
pydoc.generate_documentation()
```

#### Method: `generate_readme(self)`

*   **Description:** Generates a README file for the project.  Similar to `generate_documentation`, it uses the language model to create content and writes it to a markdown file. Only the first matching file is processed.
*   **Returns:** None
*   **Raises:** Potentially raises exceptions related to Ollama API calls and file I/O.
*   **Example:**

```python
pydoc = PyDoc(model="llama2", extension="py", dir="src")
pydoc.generate_readme()
```

#### Method: `get_files(self)`

*   **Description:**  Searches for files matching the specified extension and returns them as a list.  It respects the `.gitignore` file to exclude files.
*   **Returns:** `list`: A list of `Path` objects representing the files found.
*   **Raises:** None

#### Method: `read_file(self, file)`

*   **Description:** Reads the content of a file.
*   **Parameters:**
    *   `file` (`Path`): The path to the file to read.
*   **Returns:** `str`: The content of the file as a string.
*   **Raises:**  `IOError` if the file cannot be opened.

#### Method: `write_md_file(self, response, file)`

*   **Description:** Writes the generated documentation content to a markdown file within the `docs/` directory.
*   **Parameters:**
    *   `response` (str): The generated documentation content from the language model.
    *   `file` (`Path`): The original file path (used to construct the markdown file name).
*   **Returns:** None
*   **Raises:** `IOError` if the directory cannot be created or the file cannot be written.

### Notes

*   The `docs/` directory is created if it doesn't exist.
*   The `.gitignore` file is consulted to exclude files from documentation generation.
*   File names in the `docs/` directory will have the `.md` extension.
*   Error handling is limited within the provided code. Real-world implementations should include more robust error handling.
*   The API relies on the Ollama library. Ensure it's installed (`pip install ollama`).
*   The quality of the generated documentation depends on the capabilities of the specified language model.
