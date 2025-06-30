# To Share Publicly
Individual scripts from private repositories to be shared publicly

**import_data_and_test_rag-faiss.ipynb**: This script was part of testing different approaches for an LLM chatbot for first-responders to natural disasters using Llama with RAG. The goal was to include location and disaster-specific documents in various forms (eg, after-action reports from previous disasters in the area, local disaster protocols, vulnerable population locations) in the RAG vector store, then allow first responders to query the LLM during an actual disaster to quickly help them make decisions (identify next steps, decide areas to target, etc). The ultimate tool would be built and hosted in AWS, but packaged and downloadable locally to enable responders to use it in the field running on their laptops if wifi was not available.

In this script, I was doing part of the testing for a local version of the tool - it is not in a final, production-clean state, as we were producing this proof-of-concept for a grant, but the result of this script is a functioning local RAG LLM (tested using the code in the final cell).

This was part of a project I was working on with Dr. Andrew Schroeder at CrisisReady. 

---

**collect_maps_locs-toshare.ipynb**: This file contains the fairly manual process of collecting Google Places data from cities of interest for my project on urban intergroup integration post-conflict and its impact on conflict recovery. I created grids of 400 x 400m (generally) for each city in ArcGIS Pro, then cycle through each grid centroid with the Google Places API to collect all places within a radius that meet my search criteria (religious, cultural, administrative, educational, medical sites, primarily).

The Places API has a limit of 20 sites it can return, so for each city after cycling through all the points initially, I test if any have returned 20+ sites. For these, I rerun using a version of the code that searches for different types separately (`split`), and in the few cases where that still goes over the API return limit, I split every category out separately (`split_all`). I do this instead of just splitting all the categories from the start to minimize the number of API calls I make, as they are not free. In this example code I show the process for a few cities as an example. 

I store the end result as a goeojson for each city and process all of the cities' data together in another script, `run_spatial_autocorrelation_cities.ipynb`.

**run_spatial_autocorrelation_cities-toshare.ipynb**: This notebook is part of the same urban intergroup integration project from above, using place data from the Google Maps API to generate a number of spatial autocorrelation statistics for each of the cities I'm including. 

Before running this notebook, I used the Places API to collect all places of interest in each city (`collect_maps_locs.ipynb`), and in this script, I process these data and collect them into a single dataframe that I use for statistical analysis. 
