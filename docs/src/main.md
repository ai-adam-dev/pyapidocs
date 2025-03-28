```markdown
# Documentation Generator API

This CLI tool generates documentation for Python code using the specified Ollama model.

## Command: `cli`

Generates documentation for Python code using a specified Ollama model.

**Usage:**

```
cli [OPTIONS]
```

**Options:**

*   **`--model`** / **`-m`** `<model>`:  Specifies the Ollama model to use for documentation generation.  The tool will automatically pull the model if it's not already present locally.
    *   Example: `--model llama2`
*   **`--extension`** / **`-e`** `<extension>`: Specifies the file extension of the Python files to generate documentation for (e.g., `py`, `ipynb`).
    *   Example: `--extension py`
*   **`--dir`** / **`-d`** `<directory>`: Specifies a directory to generate documentation for. If not provided, the current working directory will be used.
    *   Example: `--dir src/modules`

**Workflow:**

1.  **Model Check:** The tool first checks if the specified Ollama model is available locally.
2.  **Model Pull (if needed):** If the model is not found, it will be downloaded from Ollama.
3.  **Documentation Generation:** A `PyDoc` object is instantiated with the given model, extension, and directory, and the `generate_documentation` method is called to create the documentation.
4.  **Error Handling:** If any error occurs during the process, it will be printed to the console.

**Return Value:**

The tool does not explicitly return a value. It performs documentation generation and displays any errors encountered.
```