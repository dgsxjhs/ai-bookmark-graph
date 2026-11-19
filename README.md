from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI(title="AI Bookmark Knowledge Graph")

class BookmarkIn(BaseModel):
    url: str

@app.post("/ingest")
async def ingest_url(item: BookmarkIn):
    # TODO: trafilatura scraping + pgvector embedding & dedup pipeline
    return {"status": "queued", "url": item.url}
# ai-bookmark-graph