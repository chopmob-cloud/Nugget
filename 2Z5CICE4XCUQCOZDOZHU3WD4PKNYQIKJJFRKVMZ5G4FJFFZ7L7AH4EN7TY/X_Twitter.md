import requests

BEARER_TOKEN = "YOUR_X_BEARER_TOKEN"
SEARCH_URL = "https://api.twitter.com/2/tweets/search/recent"

def search_x(query, max_results=20):
    headers = {
        "Authorization": f"Bearer {BEARER_TOKEN}"
    }

    params = {
        "query": query,
        "max_results": max_results,
        "tweet.fields": "author_id,created_at,public_metrics"
    }

    r = requests.get(SEARCH_URL, headers=headers, params=params, timeout=10)
    r.raise_for_status()
    return r.json()


if __name__ == "__main__":
    nfd = "myname.algo"
    results = search_x(nfd)

    for tweet in results.get("data", []):
        print(f"{tweet['created_at']} | {tweet['author_id']} | {tweet['text']}")

