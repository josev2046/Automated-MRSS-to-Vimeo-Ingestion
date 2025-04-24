# Automated MRSS to Vimeo Ingestion

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.15276505.svg)](https://doi.org/10.5281/zenodo.15276505)

This proof-of-concept repository details an automated system for ingesting video content from an MRSS (Media RSS) feed directly into a Vimeo account, utilising Vimeo's "pull" upload mechanism.

![image](https://github.com/user-attachments/assets/620fa64b-93c0-4eb7-b1fc-05e0a91c88b6)


## Overview

The primary goal of this project is to automate the process of transferring new video content, as it appears in an MRSS feed, to a designated Vimeo account. This eliminates the need for manual downloading and re-uploading, streamlining the content delivery pipeline.

The system operates by periodically fetching and parsing the MRSS feed, identifying new video entries, and then instructing the Vimeo API to "pull" the video content from its existing online location.

## Strategy

The automated ingestion process follows these key steps:

*  **Periodic Feed Retrieval:** The system is scheduled to regularly fetch the latest version of the target MRSS feed.
*  **XML Parsing:** Upon retrieval, the XML content of the feed is analysed to identify new video entries. This involves examining specific XML elements that contain video metadata, including the direct URLs of the video files.
*  **URL Extraction:** For each new video identified, the direct URL of the associated video file (e.g., `.mp4`) is extracted.
*  **Vimeo "Pull" Upload Initiation:** Using the Vimeo API, a request is made to create a new video, specifying the "pull" upload method and providing the extracted video URL. This process requires secure authentication with the Vimeo API. The provided URL should ideally be a direct, encoded link, potentially from a CDN or a pre-signed URL for optimal performance and security.
*  **Optional Upload Monitoring:** The system can optionally monitor the status of the initiated upload via the Vimeo API to confirm successful completion.
*  **Tracking Processed Items:** A record of successfully ingested videos is maintained to prevent duplicate uploads.


