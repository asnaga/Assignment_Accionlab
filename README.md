# Assignment_Accionlab
# 5 Text Manipulation with an Object Orientated Programming Language
#will use 404 error log parser using Python

import re
from collections import Counter

class LogAnalyzer:
    def __init__(self, log_file):
        self.log_file = log_file

    def extract_404_ips(self):
        ip_addresses = []
        try:
            with open(self.log_file, 'r') as file:
                for line in file:
                    match = re.search(r'(\d+\.\d+\.\d+\.\d+).*? 404', line)
                    if match:
                        ip_addresses.append(match.group(1))
        except FileNotFoundError:
            return ["Log file not found."]
        return [f"{count} {ip}" for ip, count in Counter(ip_addresses).most_common()]


          
      
