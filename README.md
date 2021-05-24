# fastapi-images

# api manipulating images using python

### FastAPI is a modern, fast (high-performance), web framework for building APIs with Python 3.6+ based on standard Python type hints.


Using UploadFile has several advantages over bytes:

It uses a "spooled" file:
A file stored in memory up to a maximum size limit, and after passing this limit it will be stored in disk.
This means that it will work well for large files like images, videos, large binaries, etc. without consuming all the memory.
You can get metadata from the uploaded file.
It has a file-like async interface.
It exposes an actual Python SpooledTemporaryFile object that you can pass directly to other libraries that expect a file-like object.


```
from fastapi import FastAPI, File, UploadFile

app = FastAPI()


@app.post("/files/")

async def create_file(file: bytes = File(...)):

    return {"file_size": len(file)}


@app.post("/uploadfile/")
async def create_upload_file(file: UploadFile = File(...)):
    return {"filename": file.filename}

```

## install
```
pip install fastapi
pip install uvicorn
```

## Run
```
uvicorn main:app
```
