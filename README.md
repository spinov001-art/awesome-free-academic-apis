# Awesome Free Academic APIs [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of free APIs for academic research — search papers, patents, datasets, and more. No API key needed for most.

## Papers & Articles

| API | Papers | Key Required | Rate Limit | Docs |
|-----|--------|-------------|------------|------|
| [OpenAlex](https://docs.openalex.org) | 250M+ | No | Polite pool | [Tutorial](https://github.com/spinov001-art/openalex-python-tutorial) |
| [arXiv API](https://arxiv.org/help/api) | 2M+ | No | 1 req/3s | [Dev.to Guide](https://dev.to/0012303) |
| [Crossref](https://www.crossref.org/documentation/) | 140M+ | No (polite pool) | Generous | [Docs](https://api.crossref.org) |
| [Semantic Scholar](https://api.semanticscholar.org/) | 200M+ | Free key | 100/5min | [Docs](https://api.semanticscholar.org/api-docs/) |
| [CORE](https://core.ac.uk/documentation/) | 200M+ | Free key | 150/min | [Docs](https://api.core.ac.uk/docs/v3) |
| [Europe PMC](https://europepmc.org/RestfulWebService) | 40M+ | No | Generous | [Docs](https://europepmc.org/RestfulWebService) |
| [PubMed](https://www.ncbi.nlm.nih.gov/home/develop/api/) | 35M+ | Free key | 10/s (with key) | [E-utils](https://www.ncbi.nlm.nih.gov/books/NBK25500/) |
| [DOAJ](https://doaj.org/api/docs) | 9M+ | No | Generous | [Docs](https://doaj.org/api/docs) |

## Patents

| API | Records | Key Required | Docs |
|-----|---------|-------------|------|
| [EPO Open Patent Services](https://www.epo.org/en/searching-for-patents/data/web-services/ops) | 130M+ | Free key | [Docs](https://developers.epo.org/) |
| [USPTO PatentsView](https://patentsview.org/apis/purpose) | 12M+ | No | [Docs](https://patentsview.org/apis) |
| [Google Patents (Public Datasets)](https://console.cloud.google.com/marketplace/product/google_patents_public_datasets/google-patents-public-data) | 100M+ | BigQuery free tier | [Docs](https://cloud.google.com/blog/topics/public-datasets/google-patents-public-datasets-connecting-public-paid-and-open-patent-data) |

## Datasets & Data

| API | Description | Key Required | Docs |
|-----|------------|-------------|------|
| [Kaggle API](https://github.com/Kaggle/kaggle-api) | 200K+ datasets | API token | [Docs](https://www.kaggle.com/docs/api) |
| [Zenodo](https://developers.zenodo.org/) | 2M+ records | No | [REST API](https://developers.zenodo.org/) |
| [Figshare](https://docs.figshare.com/) | 5M+ records | No | [API Docs](https://docs.figshare.com/) |
| [Dryad](https://datadryad.org/api/v2/docs/) | 50K+ datasets | No | [Docs](https://datadryad.org/api/v2/docs/) |
| [data.gov](https://www.data.gov/developers/apis) | 300K+ datasets | Free key | [CKAN API](https://catalog.data.gov/api/3) |

## Citation & Metrics

| API | Description | Key Required | Docs |
|-----|------------|-------------|------|
| [OpenCitations](https://opencitations.net/index/api/v2) | 1.5B+ citations | No | [Docs](https://opencitations.net/index/api/v2) |
| [Altmetric](https://api.altmetric.com) | Social impact metrics | Free tier | [Docs](https://api.altmetric.com) |
| [Unpaywall](https://unpaywall.org/products/api) | Open access finder | Email as key | [Docs](https://unpaywall.org/products/api) |

## Institutions & Funders

| API | Description | Docs |
|-----|------------|------|
| [ROR (Research Organization Registry)](https://ror.readme.io/docs/rest-api) | 100K+ orgs | [Docs](https://ror.readme.io/) |
| [OpenAlex Institutions](https://docs.openalex.org/api-entities/institutions) | 100K+ institutions | [Docs](https://docs.openalex.org) |
| [CrossRef Funders](https://api.crossref.org/funders) | 30K+ funders | [Docs](https://api.crossref.org) |

## Quick Start Examples

### Search papers (OpenAlex — no key needed)

```python
import requests

resp = requests.get("https://api.openalex.org/works", params={
    "search": "transformer attention mechanism",
    "sort": "cited_by_count:desc",
    "per_page": 5
})

for work in resp.json()["results"]:
    print(f"[{work['publication_year']}] {work['title']}")
    print(f"  Citations: {work['cited_by_count']}")
```

### Find open access versions (Unpaywall)

```python
doi = "10.1038/nature12373"
resp = requests.get(f"https://api.unpaywall.org/v2/{doi}?email=your@email.com")
data = resp.json()
if data.get("best_oa_location"):
    print(f"Free PDF: {data['best_oa_location']['url_for_pdf']}")
```

### Get citation count (OpenCitations)

```python
doi = "10.1038/nature12373"
resp = requests.get(f"https://opencitations.net/index/api/v2/citation-count/{doi}")
print(f"Citations: {resp.json()[0]['count']}")
```

## Related Resources

- [OpenAlex Python Tutorial](https://github.com/spinov001-art/openalex-python-tutorial) — Full tutorial with code
- [SQLite Vector Search](https://github.com/spinov001-art/sqlite-vector-search-tutorial) — Build semantic search for papers
- [Awesome Web Scraping](https://github.com/spinov001-art/awesome-web-scraping-2026) — 130+ scraping tools
- [All Dev.to Tutorials](https://dev.to/0012303) — 540+ API tutorials

## Contributing

PRs welcome! Add free academic APIs with: name, link, record count, whether key is required.

## License

MIT
