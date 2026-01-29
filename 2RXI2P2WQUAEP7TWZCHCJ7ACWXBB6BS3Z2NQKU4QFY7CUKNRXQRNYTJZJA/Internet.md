import os
import requests
import time

SERPAPI_KEY = os.getenv("SERPAPI_KEY")
SERPAPI_URL = "https://serpapi.com/search"

if not SERPAPI_KEY:
    raise RuntimeError("Missing SERPAPI_KEY environment variable")


def serp_search(query, num_results=10, pause=1.5):
    """Run a single SerpAPI Google search"""
    params = {
        "engine": "google",
        "q": query,
        "num": num_results,
        "api_key": SERPAPI_KEY,
    }

    r = requests.get(SERPAPI_URL, params=params, timeout=20)
    r.raise_for_status()
    time.sleep(pause)  # be polite / avoid throttling
    return r.json()


def search_handle(handle):
    """
    Search a handle across the public web using multiple query shapes
    """
    queries = [
        f'"@{handle}"',
        f'"{handle}"',
        f'"{handle}" Algorand',
        f'"{handle}" crypto',
        f'"{handle}" NUGGET',
        f'"{handle}.algo"',
    ]

    seen_links = set()
    results = []

    for q in queries:
        print(f"[+] Searching: {q}")
        data = serp_search(q)

        for item in data.get("organic_results", []):
            link = item.get("link")
            if not link or link in seen_links:
                continue

            seen_links.add(link)

            results.append({
                "query": q,
                "title": item.get("title"),
                "link": link,
                "snippet": item.get("snippet"),
                "source": item.get("source"),
            })

    return results


if __name__ == "__main__":
    handle = "examplehandle"  # <-- replace
    hits = search_handle(handle)

    print("\n=== RESULTS ===\n")
    for h in hits:
        print(f"- {h['title']}")
        print(f"  {h['link']}")
        if h["snippet"]:
            print(f"  {h['snippet']}")
        print()
