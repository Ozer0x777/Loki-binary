# Loki

Loki is a simple IOC scanner that scans files and directories for indicators of compromise (IOCs). It is designed to be fast and efficient and can be used as a standalone tool or as part of a larger security toolkit.





## Get_OTX_Iocs 

This script allows you to fetch Indicators of Compromise (IOCs) from the Open Threat Exchange (OTX) by AlienVault API and generate a report in JSON or CSV format. IOCs can be used to detect potential malicious activity in your network or systems.
Requirements

    Python 3.x
    OTX API key (you can obtain one by creating an account on https://otx.alienvault.com/)

## Installation

  Clone or download the repository.
  
    git clone https://github.com/Ozer0x777/Loki-binary.git
   
  Install the required Python packages:


    pip install -r requirements.txt
    

## Usage

  Open a terminal or command prompt and navigate to the directory where the script is located.

  Run the script with the following command:

     python get_otx_iocs.py --key <your_otx_api_key> --query <query_string> --output <output_format>



  <your_otx_api_key> is your OTX API key.
  <query_string> is the search term(s) to use for fetching IOCs. For example, you could use the name of a malware or the IP address of a suspicious domain. If you want to fetch all IOCs from a specific OTX pulse, you can use its ID.
  <output_format> is the format in which to generate the report. Currently, the script supports json and csv.

For example, to fetch IOCs related to the Emotet malware and generate a CSV report, you would run:

    python get_otx_iocs.py --key 123456789abcdefghij -o dir

The script will fetch the IOCs and generate a report in the specified format. The report will be saved in the output directory with a filename based on the current date and time.
