# Z2L-RevengeRealm
## Purpose
Breaking the automation into modular sub-workflows keeps every step clear and self-contained. This structure simplifies debugging, speeds up enhancements, and lets you reuse individual sub-workflows in other projects without extra effort.

## RR_By_Peter_Ps
Activate this workflow to run the entire automation. It orchestrates the overall logic, calling each sub-workflow in the correct order and handling the decision-making that drives the process.

## Get_Pexels_Video_Url
* Pick a URL from Google Document pexels_background_videos sheet Video_List_with_Minutes.
* Return fields:
  * video_url

## Generate_Transcript
* Call the generate-text API endpoint.
* Return fields:
  * output (the cleaned Transcript result).

## Generate_Video_Metadata
* Call the generate-text API endpoint.
* Return fields:
  * output_title
  * output_description
  * output_hashtags
  * output_tags
  * output_top_text
  * output_bottom_text
  * output_title_firstItem

## Generate_Video_Audio
* Call the generate-audio/url/generate API endpoint
* Return fields:
  * timeout_status (true or false boolean),
  * request_status (200 or the status from the HTTP request),
  * videoUrl (if the API returned one).

## Save_Audio_File
* Save the generated audio to a Google Drive folder named Audio.
  * The name of the file will be the video title with a .mp3 extension.

## Render_Video
* Call the generate-video API endpoint
* Return Fields:
  * timeout_status (true or false boolean),
  * job_id (which can be used for logging if you need it),
  * videoUrl (if the API gave one).

## Upload_Video
* Upload the video to YouTube with the given privacy status.
* Upload to Google Drive in folder Video.
* Create the Thumbnail Avatar and Thumbnail Image.
* Upload Thumbnail Image to YouTube updating the video.
* Upload Thumbnail Image Google Drive folder KARMA'S LEDGER
* Update the KARMA'S LEDGER THUMBNAILS spreadsheet Sheet1
