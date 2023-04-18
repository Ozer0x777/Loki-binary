# Loki

Loki is a simple IOC scanner that scans files and directories for indicators of compromise (IOCs). It is designed to be fast and efficient and can be used as a standalone tool or as part of a larger security toolkit.

## Usage

To use Loki, simply run the loki command followed by the path to the file or directory to be scanned:

    loki /path/to/file_or_directory

By default, Loki will scan the specified file or directory recursively. If you want to scan only the top-level directory, you can use the -n or --no-recursive option.

Loki also supports specifying a signature file that defines the IOCs to be searched for. To use a signature file, use the -s or --signature option followed by the path to the signature file:

    loki /path/to/file_or_directory -s /path/to/signature_file.yml

The signature file is a YAML file that defines the IOCs to be searched for. The file consists of a list of rules, each of which defines a single IOC. The following rule types are currently supported:

   FileHash: Searches for files with a specific hash value.
   FilePath: Searches for files with a specific file path.
   YaraRule: Searches for files that match a Yara rule.

Here is an example signature file:

    title: Sample signature file
    description: Example of a signature file
    author: John Doe
    date: 2022-04-18

    rules:
      - title: Example rule 1
        description: This rule searches for files with a specific SHA256 hash value.
        type: FileHash
        hash: 3aa0c7f91887e9caae0a2fb01d1e71c1f0e381d24c247a82b81c91990f82b9e7

      - title: Example rule 2
        description: This rule searches for files in a specific directory.
        type: FilePath
        path: /opt/malware

      - title: Example rule 3
        description: This rule searches for files that match a Yara rule.
        type: YaraRule
        rule: |
          rule ExampleRule {
              strings:
                  $s1 = "malware.exe"
              condition:
                  $s1
          }

Loki produces both human-readable and machine-readable output. The human-readable output is written to the console or to a log file, depending on the options specified. The machine-readable output is written to a JSON or CSV file.



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
