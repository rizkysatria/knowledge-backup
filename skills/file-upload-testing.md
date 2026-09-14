# Skill: File Upload Testing

For file-upload features, test beyond filename extension.

Consider:
- Supported file type
- Wrong MIME type
- Actual content mismatch
- File size boundary
- Zero-byte file
- Corrupted file
- Double extension
- Script / executable content
- Path traversal filename
- Filename encoding / special characters
- Duplicate replacement / removal
- Upload failure / retry

Validate server-side controls where the system exposes server behavior.
