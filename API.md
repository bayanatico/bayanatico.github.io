# Data Analyzer API

Base URL: `https://api.shabani05.com`

## Endpoints

### 1. List Files
Retrieves a list of available CSV files on the server.

- **URL**: `/files`
- **Method**: `GET`
- **Response**: JSON object containing a list of file paths.

```json
{
  "files": [
    "./files/dataset1.csv",
    "./files/dataset2.csv"
  ]
}
```

### 2. Summarize CSV
Generates statistical summary (mean, variance) for a given CSV file.

- **URL**: `/summarize`
- **Method**: `POST`
- **Content-Type**: `application/json`
- **Request Body**:

```json
{
  "path": "./files/dataset1.csv"
}
```

- **Response**: JSON object with row count, column names, means, and variances.

```json
{
  "rows": 100,
  "columns": ["age", "salary", "score"],
  "mean": {
    "age": 25.5,
    "salary": 50000.0
  },
  "variance": {
    "age": 5.2,
    "salary": 2000.0
  }
}
```

### 3. Generate Plot
Generates a hexbin density plot for two numeric variables.

- **URL**: `/plot`
- **Method**: `POST`
- **Content-Type**: `application/json`
- **Request Body**:

```json
{
  "path": "./files/dataset1.csv",
  "var1": "age",
  "var2": "salary"
}
```

- **Response**: Returns a PNG image stream (`image/png`).

### 4. Upload CSV
Upload a new CSV dataset to the server.

- **URL**: `/upload`
- **Method**: `POST`
- **Content-Type**: `multipart/form-data`
- **Request Body**: Form data with key `file` containing the CSV file.
- **Response**:

```json
{
  "message": "File uploaded successfully",
  "path": "./files/uploaded_file.csv"
}
```